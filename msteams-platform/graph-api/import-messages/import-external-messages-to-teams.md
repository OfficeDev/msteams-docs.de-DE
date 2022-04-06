---
title: Verwenden von Microsoft Graph zum Importieren externer Plattformnachrichten in Teams
description: Beschreibt die Verwendung von Microsoft Graph zum Importieren von Nachrichten von einer externen Plattform in Teams
ms.localizationpriority: medium
author: akjo
ms.author: lajanuar
ms.topic: Overview
keywords: Teams importieren Nachrichten-API Graph Microsoft Migrate Migration Post
ms.openlocfilehash: 5a33334367d0f5c229874decd5e45c5bb89ceafc
ms.sourcegitcommit: f892125106adb6731a20127f15d6e92f279127c5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2022
ms.locfileid: "64685632"
---
# <a name="import-third-party-platform-messages-to-teams-using-microsoft-graph"></a>Plattform-Nachrichten von Drittanbietern mithilfe von Microsoft Graph in Teams importieren

Mit Microsoft Graph können Sie den vorhandenen Nachrichtenverlauf und die Daten der Benutzer aus einem externen System in einen Teams Kanal migrieren. Durch die Aktivierung der Wiederherstellung einer Drittanbieterplattform-Messaginghierarchie innerhalb Teams können Benutzer ihre Kommunikation nahtlos fortsetzen und ohne Unterbrechung fortfahren.

> [!NOTE]
> Microsoft kann in Zukunft von Ihnen oder Ihren Kunden fordern, basierend auf der Menge der importierten Daten, zusätzliche Gebühren zu zahlen.

## <a name="import-overview"></a>Importübersicht

Auf hoher Ebene besteht der Importprozess aus folgenden Komponenten:

1. [Erstellen Sie ein Team mit einem Back-in-Time-Zeitstempel](#step-1-create-a-team).
1. [Erstellen Eines Kanals mit einem Zeitstempel "Zurück in die Zeit"](#step-2-create-a-channel).
1. [Importieren externer nachrichten mit Back-in-Time-Datum](#step-3-import-messages).
1. [Abschließen des Team- und Kanalmigrationsprozesses](#step-4-complete-migration-mode).
1. [Fügen Sie Teammitglieder hinzu](#step-five-add-team-members).

## <a name="prerequisites"></a>Voraussetzungen

### <a name="analyze-and-prepare-message-data"></a>Analysieren und Vorbereiten von Nachrichtendaten

* Überprüfen Sie die Drittanbieterdaten, um zu entscheiden, was migriert werden soll.  
* Extrahieren Sie die ausgewählten Daten aus dem Drittanbieter-Chatsystem.  
* Ordnen Sie die Chatstruktur eines Drittanbieters der Teams Struktur zu.  
* Konvertieren Von Importdaten in das für die Migration erforderliche Format.  

### <a name="set-up-your-office-365-tenant"></a>Einrichten des Office 365-Mandanten

* Stellen Sie sicher, dass ein Office 365 Mandanten für die Importdaten vorhanden ist. Weitere Informationen zum Einrichten eines Office 365 Mandanten für Teams finden Sie unter [Vorbereiten Ihres Office 365 Mandanten](../../concepts/build-and-test/prepare-your-o365-tenant.md).
* Stellen Sie sicher, dass sich Teammitglieder in Azure Active Directory befinden. Weitere Informationen finden Sie unter [Hinzufügen eines neuen Benutzers](/azure/active-directory/fundamentals/add-users-azure-active-directory) zu Azure AD.

## <a name="step-1-create-a-team"></a>Schritt 1: Erstellen eines Teams

Da Sie vorhandene Daten migrieren, sind die Aufrechterhaltung der ursprünglichen Nachrichtenzeitstempel und das Verhindern von Nachrichtenaktivitäten während des Migrationsprozesses entscheidend, um den vorhandenen Nachrichtenfluss des Benutzers in Teams neu zu erstellen. Dies wird wie folgt erreicht:

> [Erstellen Sie ein neues Team](/graph/api/team-post?view=graph-rest-beta&tabs=http&preserve-view=true) mit einem Back-in-Time-Zeitstempel mithilfe der Teamressourceneigenschaft `createdDateTime` . Platzieren Sie das neue Team in `migration mode`einem speziellen Zustand, der Benutzer von den meisten Aktivitäten innerhalb des Teams bis zum Abschluss des Migrationsprozesses einschränkt. Schließen Sie das `teamCreationMode` Instanzattribut mit dem `migration` Wert in die POST-Anforderung ein, um das neue Team explizit als für die Migration erstellt zu identifizieren.  

> [!NOTE]
> Das `createdDateTime` Feld wird nur für Instanzen eines Teams oder Kanals aufgefüllt, die migriert wurden.

<!-- markdownlint-disable MD001 -->

#### <a name="permission"></a>Berechtigung

|ScopeName|DisplayName|Beschreibung|Typ|Administratorzustimmung?|Behandelte Entitäten/APIs|
|-|-|-|-|-|-|
|`Teamwork.Migrate.All`|Migration zu Microsoft Teams verwalten|Erstellen und Verwalten von Ressourcen für die Migration zu Microsoft Teams.|**Nur Anwendung**|**Ja**|`POST /teams`|

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

#### <a name="error-message"></a>Fehlermeldung

```http
400 Bad Request
```

Sie können die Fehlermeldung in den folgenden Szenarien erhalten:

* Wenn `createdDateTime` für die Zukunft festgelegt ist.
* Wenn `createdDateTime` richtig angegeben, aber `teamCreationMode` das Instanzattribut fehlt oder auf einen ungültigen Wert festgelegt ist.

## <a name="step-2-create-a-channel"></a>Schritt 2: Erstellen eines Kanals

Das Erstellen eines Kanals für die importierten Nachrichten ähnelt dem Szenario zum Erstellen eines Teams:

> [Erstellen Sie einen neuen Kanal](/graph/api/channel-post?view=graph-rest-v1.0&tabs=http&preserve-view=true) mit einem Back-in-Time-Zeitstempel mithilfe der Kanalressourceneigenschaft `createdDateTime` . Platzieren Sie den neuen Kanal in `migration mode`einem speziellen Zustand, der Benutzer von den meisten Chataktivitäten innerhalb des Kanals bis zum Abschluss des Migrationsprozesses einschränkt. Schließen Sie das `channelCreationMode` Instanzattribut mit dem `migration` Wert in die POST-Anforderung ein, um das neue Team explizit als für die Migration erstellt zu identifizieren.  
<!-- markdownlint-disable MD024 -->
#### <a name="permission"></a>Berechtigung

|ScopeName|DisplayName|Beschreibung|Typ|Administratorzustimmung?|Behandelte Entitäten/APIs|
|-|-|-|-|-|-|
|`Teamwork.Migrate.All`|Migration zu Microsoft Teams verwalten|Erstellen und Verwalten von Ressourcen für die Migration zu Microsoft Teams.|**Nur Anwendung**|**Ja**|`POST /teams`|

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

Sie können die Fehlermeldung in den folgenden Szenarien erhalten:

* Wenn `createdDateTime` für die Zukunft festgelegt ist.
* Wenn `createdDateTime` richtig angegeben, aber `channelCreationMode` das Instanzattribut fehlt oder auf einen ungültigen Wert festgelegt ist.

## <a name="step-3-import-messages"></a>Schritt 3: Importieren von Nachrichten

Nachdem das Team und der Kanal erstellt wurden, können Sie mit dem Senden von Back-in-Time-Nachrichten beginnen, indem Sie die `createdDateTime`  Schlüssel `from` im Anforderungstext verwenden.

> [!NOTE]
>
> * Nachrichten, die mit `createdDateTime` einer früheren Version als dem Nachrichtenthread `createdDateTime` importiert wurden, werden nicht unterstützt.
> * `createdDateTime` muss für alle Nachrichten im selben Thread eindeutig sein.
> * `createdDateTime` unterstützt Zeitstempel mit Millisekundengenauigkeit. Wenn die eingehende Anforderungsnachricht beispielsweise den Wert `createdDateTime` *"2020-09-16T05:50:31.0025302Z*" aufweist, wird sie in *2020-09-16T05:50:31.002Z* konvertiert, wenn die Nachricht erfasst wird.

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

#### <a name="error-message"></a>Fehlermeldung

```http
400 Bad Request
```

#### <a name="request-post-a-message-with-inline-image"></a>Anforderung (POST einer Nachricht mit Inlinebild)

> [!NOTE]
>
> * In diesem Szenario gibt es keine speziellen Berechtigungsbereiche, da die Anforderung Teil von `chatMessage`ist.
> * Die hier zutreffenden `chatMessage` Bereiche.

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

## <a name="step-4-complete-migration-mode"></a>Schritt 4: Abschließen des Migrationsmodus

Nach Abschluss des Nachrichtenmigrationsprozesses werden sowohl das Team als auch der Kanal mithilfe der Methode aus dem  `completeMigration` Migrationsmodus genommen. In diesem Schritt werden die Team- und Kanalressourcen für die allgemeine Verwendung durch Teammitglieder geöffnet. Die Aktion ist an die `team` Instanz gebunden. Bevor das Team abgeschlossen ist, müssen alle Kanäle außerhalb des Migrationsmodus abgeschlossen sein.

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

Aktion, die für eine `team` oder `channel` die nicht in `migrationMode`aufgerufen wird.

## <a name="step-five-add-team-members"></a>Schritt 5: Hinzufügen von Teammitgliedern

Sie können ein Mitglied zu einem Team [hinzufügen, indem Sie die Teams-Benutzeroberfläche](https://support.microsoft.com/office/add-members-to-a-team-in-teams-aff2249d-b456-4bc3-81e7-52327b6b38e9) oder die Microsoft Graph [Member-API hinzufügen](/graph/api/group-post-members?view=graph-rest-beta&tabs=http&preserve-view=true):

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

* Nachdem die `completeMigration` Anforderung gestellt wurde, können Sie keine weiteren Nachrichten in das Team importieren.

* Sie können dem neuen Team nur Teammitglieder hinzufügen, nachdem die `completeMigration` Anforderung eine erfolgreiche Antwort zurückgegeben hat.

* Drosselung: Nachrichten werden mit fünf RPS pro Kanal importiert.

* Wenn Sie eine Korrektur an den Migrationsergebnissen vornehmen müssen, müssen Sie das Team löschen und die Schritte wiederholen, um das Team und den Kanal zu erstellen und die Nachrichten erneut zu migrieren.

> [!NOTE]
> Derzeit sind Inlinebilder der einzige Medientyp, der vom Api-Schema für den Import von Nachrichten unterstützt wird.

##### <a name="import-content-scope"></a>Inhaltsbereich importieren

Die folgende Tabelle enthält den Inhaltsbereich:

|Bereichsbezogener Bereich | Derzeit außerhalb des Gültigkeitsbereichs|
|----------|--------------------------|
|Team- und Kanalnachrichten|1:1- und Gruppenchatnachrichten|
|Erstellungszeit der ursprünglichen Nachricht|Private Kanäle|
|Inlinebilder als Teil der Nachricht|Bei Erwähnungen|
|Links zu vorhandenen Dateien in SPO oder OneDrive|Reaktionen|
|Nachrichten mit Rich-Text|Videos|
|Nachrichtenantwortkette|Announcements|
|Verarbeitung mit hohem Durchsatz|Codeausschnitte|
||Sticker|
||Emojis|
||Zitate|
||Übergreifende Beiträge zwischen Kanälen|
||Freigegebene Kanäle|

## <a name="see-also"></a>Siehe auch

[Integration von Microsoft Graph und Teams](/graph/teams-concept-overview)
