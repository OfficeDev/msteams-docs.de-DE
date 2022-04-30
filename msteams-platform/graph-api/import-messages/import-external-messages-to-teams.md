---
title: Verwenden von Microsoft Graph zum Importieren externer Plattformnachrichten in Microsoft Teams
description: In diesem Artikel wird die Verwendung von Microsoft Graph zum Importieren von Nachrichten von einer externen Plattform in Microsoft Teams erläutert.
ms.localizationpriority: high
author: akjo
ms.author: lajanuar
ms.topic: Overview
keywords: Microsoft Teams Nachrichten importieren API Graph Microsoft Migrieren Migration Posting
ms.openlocfilehash: 72e33ae6c8792016394c7a464f132260a5231112
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111745"
---
# <a name="import-third-party-platform-messages-to-teams-using-microsoft-graph"></a>Plattform-Nachrichten von Drittanbietern mithilfe von Microsoft Graph in Teams importieren

Mit Microsoft Graph können Sie den bestehenden Nachrichtenverlauf und die Daten von Benutzern aus einem externen System in einen Microsoft Teams-Kanal importieren. Durch die Möglichkeit, die Hierarchie von Nachrichten aus einer Drittanbieterplattform in Microsoft Teams zu übertragen, können Benutzer ihre Unterhaltungen nahtlos und ohne Unterbrechung fortsetzen.

> [!NOTE]
> Microsoft kann in Zukunft von Ihnen oder Ihren Kunden fordern, basierend auf der Menge der importierten Daten, zusätzliche Gebühren zu zahlen.

## <a name="import-overview"></a>Übersicht über den Importprozess

Im Allgemeinen besteht der Importprozess aus den folgenden Schritten:

1. [Erstellen eines Teams mit einem Back-in-Time-Zeitstempel](#step-1-create-a-team)
1. [Erstellen eines Kanals mit einem Back-in-Time-Zeitstempel](#step-2-create-a-channel)
1. [Importieren externer Nachrichten mit Back-in-Time-Datum](#step-3-import-messages)
1. [Abschließen des Team- und Kanalmigrationsprozesses](#step-4-complete-migration-mode)
1. [Hinzufügen von Teammitgliedern](#step-five-add-team-members)

## <a name="prerequisites"></a>Voraussetzungen

### <a name="analyze-and-prepare-message-data"></a>Analysieren und Vorbereiten von Nachrichtendaten

* Überprüfen Sie die Drittanbieterdaten, um zu entscheiden, was übertragen werden soll.  
* Extrahieren Sie die ausgewählten Daten aus dem Drittanbieter-Chatsystem.  
* Ordnen Sie die Drittanbieter-Chatstruktur der Microsoft Teams-Struktur zu.  
* Konvertieren Sie die zu importierenden Daten in das für die Übertragung erforderliche Format.  

### <a name="set-up-your-office-365-tenant"></a>Einrichten des Office 365-Mandanten

* Stellen Sie sicher, dass ein Office 365-Mandant für die zu importierenden Daten vorhanden ist. Weitere Informationen zum Einrichten eines Office 365-Mandanten für Microsoft Teams finden Sie unter [Vorbereiten Ihres Office 365 Mandanten](../../concepts/build-and-test/prepare-your-o365-tenant.md).
* Stellen Sie sicher, dass Teammitglieder in Azure Active Directory vorhanden sind. Weitere Informationen finden Sie unter [Hinzufügen eines neuen Benutzers](/azure/active-directory/fundamentals/add-users-azure-active-directory) zu Azure AD.

## <a name="step-1-create-a-team"></a>Schritt 1: Erstellen eines Teams

Da Sie bestehende Daten migrieren, sind die Erhaltung der ursprünglichen Nachrichtenzeitstempel und das Verhindern von Nachrichtenaktivitäten während des Migrationsprozesses entscheidend, um den bestehenden Nachrichtenablauf des Benutzers in Microsoft Teams neu zu erstellen. Dies wird wie folgt erreicht:

> [Erstellen Sie ein neues Team](/graph/api/team-post?view=graph-rest-beta&tabs=http&preserve-view=true) mit einem Back-in-Time-Zeitstempel mithilfe der Teamressourceneigenschaft `createdDateTime`. Versetzen Sie das neue Team in den Modus `migration mode`, einem besonderen Zustand, der die meisten Benutzeraktivitäten innerhalb des Teams bis zum Abschluss des Migrationsprozesses einschränkt. Schließen Sie das `teamCreationMode`-Instanzattribut mit dem Wert `migration` in die POST-Anforderung ein, um das neue Team explizit als für die Migration erstellt zu identifizieren.  

> [!NOTE]
> Das `createdDateTime`-Feld wird nur für Instanzen eines Teams oder Kanals befüllt, die migriert wurden.

<!-- markdownlint-disable MD001 -->

#### <a name="permission"></a>Berechtigung

|ScopeName|DisplayName|Beschreibung|Typ|Administratorzustimmung?|Abgedeckte Entitäten/APIs|
|-|-|-|-|-|-|
|`Teamwork.Migrate.All`|Migration zu Microsoft Teams verwalten|Erstellen und Verwalten von Ressourcen für die Migration zu Microsoft Teams|**Nur Anwendung**|**Ja**|`POST /teams`|

#### <a name="request-create-a-team-in-migration-state"></a>Anforderung (Team im Migrationsstatus erstellen)

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

#### <a name="error-message"></a>Fehlermeldung

```http
400 Bad Request
```

Sie können diese Fehlermeldung in den folgenden Szenarien erhalten:

* Wenn `createdDateTime` auf ein Datum in der Zukunft festgelegt ist.
* Wenn `createdDateTime` ordnungsgemäß angegeben wurde, aber das `teamCreationMode`-Instanzattribut fehlt oder auf einen ungültigen Wert festgelegt wurde.

## <a name="step-2-create-a-channel"></a>Schritt 2: Erstellen eines Kanals

Das Erstellen eines Kanals für die zu importierenden Nachrichten ähnelt dem Vorgang zum Erstellen eines Teams:

> [Erstellen Sie einen neuen Kanal](/graph/api/channel-post?view=graph-rest-v1.0&tabs=http&preserve-view=true) mit einem Back-in-Time-Zeitstempel mithilfe der Kanalressourceneigenschaft `createdDateTime`. Versetzen Sie den neuen Kanal in den Modus `migration mode`, einem besonderen Zustand, der die meisten Chataktivitäten innerhalb des Kanals bis zum Abschluss des Migrationsprozesses einschränkt. Schließen Sie das `channelCreationMode`-Instanzattribut mit dem Wert `migration` in die POST-Anforderung ein, um den neuen Kanal explizit als für die Migration erstellt zu identifizieren.  
<!-- markdownlint-disable MD024 -->
#### <a name="permission"></a>Berechtigung

|ScopeName|DisplayName|Beschreibung|Typ|Administratorzustimmung?|Abgedeckte Entitäten/APIs|
|-|-|-|-|-|-|
|`Teamwork.Migrate.All`|Migration zu Microsoft Teams verwalten|Erstellen und Verwalten von Ressourcen für die Migration zu Microsoft Teams|**Nur Anwendung**|**Ja**|`POST /teams`|

#### <a name="request-create-a-channel-in-migration-state"></a>Anforderung (Kanal im Migrationsstatus erstellen)

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

Sie können diese Fehlermeldung in den folgenden Szenarien erhalten:

* Wenn `createdDateTime` auf ein Datum in der Zukunft festgelegt ist.
* Wenn `createdDateTime` ordnungsgemäß angegeben wurde, aber das `channelCreationMode`-Instanzattribut fehlt oder auf einen ungültigen Wert festgelegt wurde.

## <a name="step-3-import-messages"></a>Schritt 3: Importieren von Nachrichten

Nachdem das Team und der Kanal erstellt wurden, können Sie mit dem Senden von Back-in-Time-Nachrichten beginnen, indem Sie im Anforderungstext die Schlüssel `createdDateTime` und `from` verwenden.

> [!NOTE]
>
> * Nachrichten mit einem `createdDateTime`-Datum, das vor dem `createdDateTime`-Datum des Nachrichtenthreads liegt, werden nicht unterstützt.
> * `createdDateTime` muss für alle Nachrichten im selben Thread eindeutig sein.
> * `createdDateTime` unterstützt Zeitstempel mit einer Präzision im Millisekundenbereich. Wenn die eingehende Anforderungsnachricht beispielsweise für als Wert von `createdDateTime` *2020-09-16T05:50:31.0025302Z* aufweist, wird dies in *2020-09-16T05:50:31.002Z* konvertiert, wenn die Nachricht erfasst wird.

#### <a name="request-post-message-that-is-text-only"></a>Anforderung (POST einer Nur-Text-Nachricht)

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

#### <a name="error-message"></a>Fehlermeldung

```http
400 Bad Request
```

#### <a name="request-post-a-message-with-inline-image"></a>Anforderung (POST einer Nachricht mit Inlinebild)

> [!NOTE]
>
> * In diesem Szenario gibt es keine speziellen Berechtigungsbereiche, da die Anforderung Teil von `chatMessage` ist.
> * Die Bereiche für `chatMessage` gelten hier.

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

## <a name="step-4-complete-migration-mode"></a>Schritt 4: Beenden des Migrationsmodus

Nach Abschluss des Nachrichtenmigrationsprozesses wird der Migrationsmodus mithilfe der `completeMigration`-Methode sowohl für das Team als auch für den Kanal aufgehoben. In diesem Schritt werden die Team- und Kanalressourcen für die allgemeine Verwendung durch Teammitglieder freigegeben. Die Aktion ist an die `team`-Instanz gebunden. Bevor das Team abgeschlossen wird, müssen alle Kanäle außerhalb des Migrationsmodus abgeschlossen sein.

#### <a name="request-end-channel-migration-mode"></a>Anforderung (Kanalmigrationsmodus beenden)

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

Aktion, die für ein `team` oder einen `channel` aufgerufen wird, die nicht im `migrationMode` sind.

## <a name="step-five-add-team-members"></a>Schritt 5: Hinzufügen von Teammitgliedern

Sie können einem Team ein Mitglied [über die Microsoft Teams-Benutzeroberfläche](https://support.microsoft.com/office/add-members-to-a-team-in-teams-aff2249d-b456-4bc3-81e7-52327b6b38e9) oder mithilfe der Microsoft Graph-API zum [Hinzufügen von Mitgliedern](/graph/api/group-post-members?view=graph-rest-beta&tabs=http&preserve-view=true) hinzufügen:

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

* Nachdem die `completeMigration`-Anforderung gestellt wurde, können Sie keine weiteren Nachrichten in das Team importieren.

* Sie können dem neuen Team erst Teammitglieder hinzufügen, nachdem die `completeMigration`-Anforderung eine positive Antwort zurückgegeben hat.

* Drosselung: Nachrichten werden mit fünf RPS pro Kanal importiert.

* Wenn Sie eine Korrektur an den Migrationsergebnissen vornehmen müssen, müssen Sie das Team löschen, die Schritte zum Erstellen des Teams und Kanals wiederholen und die Nachrichten erneut migrieren.

> [!NOTE]
> Derzeit sind Inlinebilder der einzige Medientyp, der vom API-Schema für das Importieren von Nachrichten unterstützt wird.

##### <a name="import-content-scope"></a>Importierbare Inhalte

Die nachstehende Tabelle enthält die importierbaren Inhalte:

|Importierbar | Derzeit nicht importierbar|
|----------|--------------------------|
|Team- und Kanalnachrichten|1:1- und Gruppenchatnachrichten|
|Erstellungszeit der ursprünglichen Nachricht|Private Kanäle|
|Inlinebilder als Teil der Nachricht|@-Erwähnungen|
|Links zu vorhandenen Dateien in SPO oder OneDrive|Reaktionen|
|Nachrichten mit Rich-Text|Videos|
|Nachrichtenantwortkette|Ankündigungen|
|Verarbeitung mit hohem Durchsatz|Codeausschnitte|
||Sticker|
||Emojis|
||Zitate|
||Crossposts zwischen Kanälen|
||Freigegebene Kanäle|

## <a name="see-also"></a>Siehe auch

[Integration von Microsoft Graph und Microsoft Teams](/graph/teams-concept-overview)
