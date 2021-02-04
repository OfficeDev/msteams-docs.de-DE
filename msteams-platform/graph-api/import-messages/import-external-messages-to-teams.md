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
# <a name="import-third-party-platform-messages-to-teams-using-microsoft-graph"></a><span data-ttu-id="62845-104">Plattform-Nachrichten von Drittanbietern mithilfe von Microsoft Graph in Teams importieren</span><span class="sxs-lookup"><span data-stu-id="62845-104">Import third-party platform messages to Teams using Microsoft Graph</span></span>

>[!IMPORTANT]
> <span data-ttu-id="62845-105">Microsoft Graph und Microsoft Teams public previews are available for early-access and feedback.</span><span class="sxs-lookup"><span data-stu-id="62845-105">Microsoft Graph and Microsoft Teams public previews are available for early-access and feedback.</span></span> <span data-ttu-id="62845-106">Obwohl diese Version umfassenden Tests unterzogen wurde, ist sie nicht für die Verwendung in der Produktion vorgesehen.</span><span class="sxs-lookup"><span data-stu-id="62845-106">Although this release has undergone extensive testing, it is not intended for use in production.</span></span>

<span data-ttu-id="62845-107">Mit Microsoft Graph können Sie den vorhandenen Nachrichtenverlauf und die Daten von Benutzern aus einem externen System in einen Microsoft Teams-Kanal migrieren.</span><span class="sxs-lookup"><span data-stu-id="62845-107">With Microsoft Graph, you can migrate users' existing message history and data from an external system into a Teams channel.</span></span> <span data-ttu-id="62845-108">Durch die Neugestaltung einer Drittanbieterplattform-Messaging-Hierarchie in Teams können Benutzer ihre Kommunikation nahtlos fortsetzen und ohne Unterbrechung fortfahren.</span><span class="sxs-lookup"><span data-stu-id="62845-108">By enabling the recreation of a third-party platform messaging hierarchy inside Teams, users can continue their communications in a seamless manner and proceed without interruption.</span></span>

## <a name="import-overview"></a><span data-ttu-id="62845-109">Übersicht über den Import</span><span class="sxs-lookup"><span data-stu-id="62845-109">Import overview</span></span>

<span data-ttu-id="62845-110">Der Importvorgang umfasst auf hoher Ebene Folgendes:</span><span class="sxs-lookup"><span data-stu-id="62845-110">At a high level, the import process consists of the following:</span></span>

1. [<span data-ttu-id="62845-111">Erstellen eines Teams mit einem Back-in-Time-Zeitstempel</span><span class="sxs-lookup"><span data-stu-id="62845-111">Create a team with a back-in-time timestamp</span></span>](#step-one-create-a-team)
1. [<span data-ttu-id="62845-112">Erstellen eines Kanals mit einem Back-in-Time-Zeitstempel</span><span class="sxs-lookup"><span data-stu-id="62845-112">Create a channel with a back-in-time timestamp</span></span>](#step-two-create-a-channel)  
1. [<span data-ttu-id="62845-113">Importieren externer Back-in-Time-Nachrichten mit Datum</span><span class="sxs-lookup"><span data-stu-id="62845-113">Import external back-in-time dated messages</span></span>](#step-three-import-messages)
1. [<span data-ttu-id="62845-114">Abschließen des Team- und Kanalmigrationsprozesses</span><span class="sxs-lookup"><span data-stu-id="62845-114">Complete the team and channel migration process</span></span>](#step-four-complete-migration-mode)
1. [<span data-ttu-id="62845-115">Hinzufügen von Teammitgliedern</span><span class="sxs-lookup"><span data-stu-id="62845-115">Add team members</span></span>](#step-five-add-team-members)

## <a name="necessary-requirements"></a><span data-ttu-id="62845-116">Erforderliche Anforderungen</span><span class="sxs-lookup"><span data-stu-id="62845-116">Necessary requirements</span></span>

### <a name="analyze-and-prepare-message-data"></a><span data-ttu-id="62845-117">Analysieren und Vorbereiten von Nachrichtendaten</span><span class="sxs-lookup"><span data-stu-id="62845-117">Analyze and prepare message data</span></span>

<span data-ttu-id="62845-118">✔ Sie die Drittanbieterdaten, um zu entscheiden, was migriert wird.</span><span class="sxs-lookup"><span data-stu-id="62845-118">✔ Review the third-party data to decide what will be migrated.</span></span>  
<span data-ttu-id="62845-119">✔ extrahieren Sie die ausgewählten Daten aus dem Drittanbieter-Chatsystem.</span><span class="sxs-lookup"><span data-stu-id="62845-119">✔ Extract the selected data from the third-party chat system.</span></span>  
<span data-ttu-id="62845-120">✔ Sie die Chatstruktur eines Drittanbieters der Teams-Struktur zu.</span><span class="sxs-lookup"><span data-stu-id="62845-120">✔ Map the third-party chat structure to the Teams structure.</span></span>  
<span data-ttu-id="62845-121">✔ Konvertieren von Importdaten in das für die Migration benötigte Format.</span><span class="sxs-lookup"><span data-stu-id="62845-121">✔ Convert import data into format needed for migration.</span></span>  

### <a name="set-up-your-office-365-tenant"></a><span data-ttu-id="62845-122">Einrichten des Office 365-Mandanten</span><span class="sxs-lookup"><span data-stu-id="62845-122">Set up your Office 365 tenant</span></span>

<span data-ttu-id="62845-123">✔ Stellen Sie sicher, dass ein Office 365-Mandant für die Importdaten vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="62845-123">✔ Ensure that an Office 365 tenant exists for the import data.</span></span> <span data-ttu-id="62845-124">Weitere Informationen zum Einrichten eines Office 365-Mandanten für Teams finden Sie unter *"* [Vorbereiten Ihres Office 365-Mandanten".](../../concepts/build-and-test/prepare-your-o365-tenant.md)</span><span class="sxs-lookup"><span data-stu-id="62845-124">For more information on setting up an Office 365 tenancy for Teams, *see*, [Prepare your Office 365 tenant](../../concepts/build-and-test/prepare-your-o365-tenant.md).</span></span>  
<span data-ttu-id="62845-125">✔ Stellen Sie sicher, dass sich Teammitglieder in Azure Active Directory (AAD) befinden.</span><span class="sxs-lookup"><span data-stu-id="62845-125">✔ Make sure that team members are in Azure Active Directory (AAD).</span></span>  <span data-ttu-id="62845-126">Weitere Informationen finden *Sie unter* [Hinzufügen eines neuen Benutzers](/azure/active-directory/fundamentals/add-users-azure-active-directory) zu Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="62845-126">For more information *see* [Add a new user](/azure/active-directory/fundamentals/add-users-azure-active-directory) to Azure Active Directory.</span></span>

## <a name="step-one-create-a-team"></a><span data-ttu-id="62845-127">Schritt 1: Erstellen eines Teams</span><span class="sxs-lookup"><span data-stu-id="62845-127">Step One: Create a team</span></span>

<span data-ttu-id="62845-128">Da vorhandene Daten migriert werden, sind die Beibehaltung der ursprünglichen Nachrichtenzeitstempel und das Verhindern von Messagingaktivitäten während des Migrationsprozesses entscheidend, um den vorhandenen Nachrichtenfluss des Benutzers in Teams neu zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="62845-128">Since existing data is being migrated, maintaining the original message timestamps and preventing messaging activity during the migration process are key to recreating the user's existing message flow in Teams.</span></span> <span data-ttu-id="62845-129">Dies wird wie folgt erreicht:</span><span class="sxs-lookup"><span data-stu-id="62845-129">This is achieved as follows:</span></span>

> <span data-ttu-id="62845-130">[Erstellen Sie ein neues Team](/graph/api/team-post?view=graph-rest-beta&tabs=http&preserve-view=true) mit einem Back-in-Time-Zeitstempel mithilfe der Teamressourceneigenschaft. `createdDateTime`</span><span class="sxs-lookup"><span data-stu-id="62845-130">[Create a new team](/graph/api/team-post?view=graph-rest-beta&tabs=http&preserve-view=true) with a back-in-time timestamp using the team resource  `createdDateTime`  property.</span></span> <span data-ttu-id="62845-131">Platzieren Sie das neue Team in einem speziellen Zustand, der Benutzer von den meisten Aktivitäten innerhalb des Teams abgleistet, bis `migration mode` der Migrationsprozess abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="62845-131">Place the new team in `migration mode`, a special state that bars users from most activities within the team until the migration process is complete.</span></span> <span data-ttu-id="62845-132">Schließen Sie das Instanzattribut in den Wert in die POST-Anforderung ein, um das neue Team explizit als `teamCreationMode` für die Migration erstellt zu `migration` identifizieren.</span><span class="sxs-lookup"><span data-stu-id="62845-132">Include the `teamCreationMode` instance attribute with the `migration` value in the POST request to explicitly identify the new team as being created for migration.</span></span>  

> <span data-ttu-id="62845-133">**HINWEIS:** Das Feld wird nur für Instanzen eines Teams oder Kanals `createdDateTime` aufgefüllt, die migriert wurden.</span><span class="sxs-lookup"><span data-stu-id="62845-133">**NOTE**:  The `createdDateTime` field will only be populated for instances of a team or channel that have been migrated.</span></span>

<!-- markdownlint-disable MD001 -->

#### <a name="permissions"></a><span data-ttu-id="62845-134">Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="62845-134">Permissions</span></span>

|<span data-ttu-id="62845-135">ScopeName</span><span class="sxs-lookup"><span data-stu-id="62845-135">ScopeName</span></span>|<span data-ttu-id="62845-136">DisplayName</span><span class="sxs-lookup"><span data-stu-id="62845-136">DisplayName</span></span>|<span data-ttu-id="62845-137">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="62845-137">Description</span></span>|<span data-ttu-id="62845-138">Typ</span><span class="sxs-lookup"><span data-stu-id="62845-138">Type</span></span>|<span data-ttu-id="62845-139">Administrator-Zustimmung?</span><span class="sxs-lookup"><span data-stu-id="62845-139">Admin Consent?</span></span>|<span data-ttu-id="62845-140">Behandelte Entitäten/APIs</span><span class="sxs-lookup"><span data-stu-id="62845-140">Entities/APIs covered</span></span>|
|-|-|-|-|-|-|
|`Teamwork.Migrate.All`|<span data-ttu-id="62845-141">Migration zu Microsoft Teams verwalten</span><span class="sxs-lookup"><span data-stu-id="62845-141">Manage migration to Microsoft Teams</span></span>|<span data-ttu-id="62845-142">Erstellen, Verwalten von Ressourcen für die Migration zu Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="62845-142">Creating, managing resources for migration to Microsoft Teams</span></span>|<span data-ttu-id="62845-143">**Nur Anwendung**</span><span class="sxs-lookup"><span data-stu-id="62845-143">**Application-only**</span></span>|<span data-ttu-id="62845-144">**Ja**</span><span class="sxs-lookup"><span data-stu-id="62845-144">**Yes**</span></span>|`POST /teams`|

#### <a name="request-create-a-team-in-migration-state"></a><span data-ttu-id="62845-145">Anforderung (Erstellen eines Teams im Migrationsstatus)</span><span class="sxs-lookup"><span data-stu-id="62845-145">Request (create a team in migration state)</span></span>

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

#### <a name="response"></a><span data-ttu-id="62845-146">Antwort</span><span class="sxs-lookup"><span data-stu-id="62845-146">Response</span></span>

```http
HTTP/1.1 202 Accepted
Location: /teams/{teamId}/operations/{operationId}
Content-Location: /teams/{teamId}
```

#### <a name="error-messages"></a><span data-ttu-id="62845-147">Fehlermeldungen</span><span class="sxs-lookup"><span data-stu-id="62845-147">Error messages</span></span>

```http
400 Bad Request
```

* <span data-ttu-id="62845-148">`createdDateTime`  für die Zukunft festgelegt.</span><span class="sxs-lookup"><span data-stu-id="62845-148">`createdDateTime`  set for future.</span></span>
* <span data-ttu-id="62845-149">`createdDateTime`  richtig angegeben, aber `teamCreationMode`  das Instanzattribut fehlt oder ist auf einen ungültigen Wert festgelegt.</span><span class="sxs-lookup"><span data-stu-id="62845-149">`createdDateTime`  correctly specified, but `teamCreationMode`  instance attribute  is missing or set to invalid value.</span></span>

## <a name="step-two-create-a-channel"></a><span data-ttu-id="62845-150">Schritt 2: Erstellen eines Kanals</span><span class="sxs-lookup"><span data-stu-id="62845-150">Step Two: Create a channel</span></span>

<span data-ttu-id="62845-151">Das Erstellen eines Kanals für die importierten Nachrichten ähnelt dem Szenario zum Erstellen eines Teams:</span><span class="sxs-lookup"><span data-stu-id="62845-151">Creating a channel for the imported messages is similar to the create team scenario:</span></span>

> <span data-ttu-id="62845-152">[Erstellen Sie einen neuen Kanal](/graph/api/channel-post?view=graph-rest-beta&tabs=http&preserve-view=true) mit einem Back-in-Time-Zeitstempel mithilfe der Kanalressourceneigenschaft. `createdDateTime`</span><span class="sxs-lookup"><span data-stu-id="62845-152">[Create a new channel](/graph/api/channel-post?view=graph-rest-beta&tabs=http&preserve-view=true) with a back-in-time timestamp using the channel resource `createdDateTime` property.</span></span> <span data-ttu-id="62845-153">Platzieren Sie den neuen Kanal in einem besonderen Zustand, der Benutzer von den meisten Chataktivitäten innerhalb des Kanals abgleistet, bis der `migration mode` Migrationsprozess abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="62845-153">Place the new channel in `migration mode`, a special state that bars users from most chat activities within the channel until the migration process is complete.</span></span>  <span data-ttu-id="62845-154">Schließen Sie das Instanzattribut in den Wert in die POST-Anforderung ein, um das neue Team explizit als `channelCreationMode` für die Migration erstellt zu `migration` identifizieren.</span><span class="sxs-lookup"><span data-stu-id="62845-154">Include the `channelCreationMode` instance attribute with the `migration` value in the POST request to explicitly identify the new team as being created for migration.</span></span>  
<!-- markdownlint-disable MD024 -->
#### <a name="permissions"></a><span data-ttu-id="62845-155">Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="62845-155">Permissions</span></span>

|<span data-ttu-id="62845-156">ScopeName</span><span class="sxs-lookup"><span data-stu-id="62845-156">ScopeName</span></span>|<span data-ttu-id="62845-157">DisplayName</span><span class="sxs-lookup"><span data-stu-id="62845-157">DisplayName</span></span>|<span data-ttu-id="62845-158">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="62845-158">Description</span></span>|<span data-ttu-id="62845-159">Typ</span><span class="sxs-lookup"><span data-stu-id="62845-159">Type</span></span>|<span data-ttu-id="62845-160">Administrator-Zustimmung?</span><span class="sxs-lookup"><span data-stu-id="62845-160">Admin Consent?</span></span>|<span data-ttu-id="62845-161">Behandelte Entitäten/APIs</span><span class="sxs-lookup"><span data-stu-id="62845-161">Entities/APIs covered</span></span>|
|-|-|-|-|-|-|
|`Teamwork.Migrate.All`|<span data-ttu-id="62845-162">Migration zu Microsoft Teams verwalten</span><span class="sxs-lookup"><span data-stu-id="62845-162">Manage migration to Microsoft Teams</span></span>|<span data-ttu-id="62845-163">Erstellen, Verwalten von Ressourcen für die Migration zu Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="62845-163">Creating, managing resources for migration to Microsoft Teams</span></span>|<span data-ttu-id="62845-164">**Nur Anwendung**</span><span class="sxs-lookup"><span data-stu-id="62845-164">**Application-only**</span></span>|<span data-ttu-id="62845-165">**Ja**</span><span class="sxs-lookup"><span data-stu-id="62845-165">**Yes**</span></span>|`POST /teams`|

#### <a name="request-create-a-channel-in-migration-state"></a><span data-ttu-id="62845-166">Anforderung (Erstellen eines Kanals im Migrationsstatus)</span><span class="sxs-lookup"><span data-stu-id="62845-166">Request (create a channel in migration state)</span></span>

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

#### <a name="response"></a><span data-ttu-id="62845-167">Antwort</span><span class="sxs-lookup"><span data-stu-id="62845-167">Response</span></span>

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

#### <a name="error-message"></a><span data-ttu-id="62845-168">Fehlermeldung</span><span class="sxs-lookup"><span data-stu-id="62845-168">Error message</span></span>

```http
400 Bad Request
```

* <span data-ttu-id="62845-169">`createdDateTime`  für die Zukunft festgelegt.</span><span class="sxs-lookup"><span data-stu-id="62845-169">`createdDateTime`  set for future.</span></span>
* <span data-ttu-id="62845-170">`createdDateTime`  richtig angegeben, `channelCreationMode`  aber das Instanzattribut fehlt oder ist auf einen ungültigen Wert festgelegt.</span><span class="sxs-lookup"><span data-stu-id="62845-170">`createdDateTime`  correctly specified but `channelCreationMode`  instance attribute  is missing or set to invalid value.</span></span>

## <a name="step-three-import-messages"></a><span data-ttu-id="62845-171">Schritt 3: Importieren von Nachrichten</span><span class="sxs-lookup"><span data-stu-id="62845-171">Step Three: Import messages</span></span>

<span data-ttu-id="62845-172">Nachdem das Team und der Kanal erstellt wurden, können Sie mit dem Senden von Back-in-Time-Nachrichten beginnen, indem Sie die Schlüssel im `createdDateTime` `from`  Anforderungstext verwenden.</span><span class="sxs-lookup"><span data-stu-id="62845-172">After the team and channel have been created, you can begin sending back-in-time messages using the `createdDateTime`  and `from`  keys in the request body.</span></span> <span data-ttu-id="62845-173">**HINWEIS:** Nachrichten, die mit einer früheren Zeit als `createdDateTime` dem Nachrichtenthread `createdDateTime` importiert wurden, werden nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="62845-173">**NOTE**: messages imported with `createdDateTime` earlier than the message thread `createdDateTime` is not supported.</span></span>

> [!NOTE]
> * <span data-ttu-id="62845-174">`createdDateTime` muss für alle Nachrichten im selben Thread eindeutig sein.</span><span class="sxs-lookup"><span data-stu-id="62845-174">`createdDateTime` must be unique across messages in the same thread.</span></span>
> * <span data-ttu-id="62845-175">`createdDateTime` unterstützt Zeitstempel mit Millisekundengenauigkeit.</span><span class="sxs-lookup"><span data-stu-id="62845-175">`createdDateTime` supports timestamps with milliseconds precision.</span></span> <span data-ttu-id="62845-176">Wenn die eingehende Anforderungsnachricht beispielsweise den Wert `createdDateTime` *2020-09-16T05:50:31.0025302Z* hat, wird sie in *2020-09-16T05:50:31.002Z* konvertiert, wenn die Nachricht aufgenommen wird.</span><span class="sxs-lookup"><span data-stu-id="62845-176">For example, if the incoming request message has the value of `createdDateTime` set as *2020-09-16T05:50:31.0025302Z*, then it would be converted to *2020-09-16T05:50:31.002Z* when the message is ingested.</span></span>

#### <a name="request-post-message-that-is-text-only"></a><span data-ttu-id="62845-177">Anforderung (nur Text enthaltende POST-Nachricht)</span><span class="sxs-lookup"><span data-stu-id="62845-177">Request (POST message that is text-only)</span></span>

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

#### <a name="response"></a><span data-ttu-id="62845-178">Antwort</span><span class="sxs-lookup"><span data-stu-id="62845-178">Response</span></span>

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

#### <a name="error-messages"></a><span data-ttu-id="62845-179">Fehlermeldungen</span><span class="sxs-lookup"><span data-stu-id="62845-179">Error messages</span></span>

```http
400 Bad Request
```

#### <a name="request-post-a-message-with-inline-image"></a><span data-ttu-id="62845-180">Anforderung (POST einer Nachricht mit Inlinebild)</span><span class="sxs-lookup"><span data-stu-id="62845-180">Request (POST a message with inline image)</span></span>

> <span data-ttu-id="62845-181">**Hinweis:** In diesem Szenario gibt es keine speziellen Berechtigungsbereiche, da die Anforderung Teil von chatMessage ist. Bereiche für chatMessage gelten auch hier.</span><span class="sxs-lookup"><span data-stu-id="62845-181">**Note**: There are no special permission scopes in this scenario since the request is part of chatMessage; scopes for chatMessage apply here as well.</span></span>

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

#### <a name="response"></a><span data-ttu-id="62845-182">Antwort</span><span class="sxs-lookup"><span data-stu-id="62845-182">Response</span></span>

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

## <a name="step-four-complete-migration-mode"></a><span data-ttu-id="62845-183">Schritt 4: Abschließen des Migrationsmodus</span><span class="sxs-lookup"><span data-stu-id="62845-183">Step Four: Complete migration mode</span></span>

<span data-ttu-id="62845-184">Sobald der Nachrichtenmigrationsprozess abgeschlossen ist, werden das Team und der Kanal mithilfe der Methode aus dem Migrationsmodus  `completeMigration`  genommen.</span><span class="sxs-lookup"><span data-stu-id="62845-184">Once the message migration process has completed, both the team and channel are taken out of migration mode using the  `completeMigration`  method.</span></span> <span data-ttu-id="62845-185">In diesem Schritt werden die Team- und Kanalressourcen für die allgemeine Verwendung durch Teammitglieder geöffnet.</span><span class="sxs-lookup"><span data-stu-id="62845-185">This step opens the team and channel resources for general use by team members.</span></span> <span data-ttu-id="62845-186">Die Aktion ist an die Instanz `team` gebunden.</span><span class="sxs-lookup"><span data-stu-id="62845-186">The action is bound to the `team` instance.</span></span>

#### <a name="request-end-team-migration-mode"></a><span data-ttu-id="62845-187">Anforderung (Teammigrationsmodus beenden)</span><span class="sxs-lookup"><span data-stu-id="62845-187">Request (end team migration mode)</span></span>

```http
POST https://graph.microsoft.com/beta/teams/teamId/completeMigration

```

#### <a name="response"></a><span data-ttu-id="62845-188">Antwort</span><span class="sxs-lookup"><span data-stu-id="62845-188">Response</span></span>

```http
HTTP/1.1 204 NoContent
```

#### <a name="request-end-channel-migration-mode"></a><span data-ttu-id="62845-189">Anforderung (Endkanalmigrationsmodus)</span><span class="sxs-lookup"><span data-stu-id="62845-189">Request (end channel migration mode)</span></span>

```http
POST https://graph.microsoft.com/beta/teams/teamId/channels/channelId/completeMigration

```

#### <a name="response"></a><span data-ttu-id="62845-190">Antwort</span><span class="sxs-lookup"><span data-stu-id="62845-190">Response</span></span>

```http
HTTP/1.1 204 NoContent
```

#### <a name="error-response"></a><span data-ttu-id="62845-191">Fehlerantwort</span><span class="sxs-lookup"><span data-stu-id="62845-191">Error response</span></span>

```http
400 Bad Request
```

* <span data-ttu-id="62845-192">Aktion aufgerufen für eine `team` oder die sich nicht in `channel` `migrationMode` befindet.</span><span class="sxs-lookup"><span data-stu-id="62845-192">Action called on a `team` or `channel` that is not in `migrationMode`.</span></span>

## <a name="step-five-add-team-members"></a><span data-ttu-id="62845-193">Schritt 5: Hinzufügen von Teammitgliedern</span><span class="sxs-lookup"><span data-stu-id="62845-193">Step Five: Add team members</span></span>

<span data-ttu-id="62845-194">Sie können ein Mitglied mithilfe der [Benutzeroberfläche](https://support.microsoft.com/office/add-members-to-a-team-in-teams-aff2249d-b456-4bc3-81e7-52327b6b38e9) von Teams oder der Microsoft Graph-Mitglieds-API hinzufügen [zu einem Team](/graph/api/group-post-members?view=graph-rest-beta&tabs=http&preserve-view=true) hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="62845-194">You can add a member to a team [using the Teams UI](https://support.microsoft.com/office/add-members-to-a-team-in-teams-aff2249d-b456-4bc3-81e7-52327b6b38e9) or Microsoft Graph [Add member](/graph/api/group-post-members?view=graph-rest-beta&tabs=http&preserve-view=true) API:</span></span>

#### <a name="request-add-member"></a><span data-ttu-id="62845-195">Anforderung (Mitglied hinzufügen)</span><span class="sxs-lookup"><span data-stu-id="62845-195">Request (add member)</span></span>

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

#### <a name="response"></a><span data-ttu-id="62845-196">Antwort</span><span class="sxs-lookup"><span data-stu-id="62845-196">Response</span></span>

```http
HTTP/1.1 204 No Content
```

## <a name="tips-and-additional-information"></a><span data-ttu-id="62845-197">Tipps und zusätzliche Informationen</span><span class="sxs-lookup"><span data-stu-id="62845-197">Tips and additional information</span></span>

<!-- markdownlint-disable MD001 -->
<!-- markdownlint-disable MD026 -->

* <span data-ttu-id="62845-198">Sie können Nachrichten von Benutzern importieren, die sich nicht in Teams befinden.</span><span class="sxs-lookup"><span data-stu-id="62845-198">You can import messages from users who are not in Teams.</span></span> <span data-ttu-id="62845-199">**HINWEIS:** Nachrichten, die für Benutzer importiert wurden, die nicht im Mandanten vorhanden sind, können während der öffentlichen Vorschau nicht im Client- oder Complianceportal von Teams durchsucht werden.</span><span class="sxs-lookup"><span data-stu-id="62845-199">**NOTE**: Messages imported for users not present in the tenant will not be searchable in the Teams client or compliance portals during Public Preview.</span></span>

* <span data-ttu-id="62845-200">Nachdem die `completeMigration` Anforderung gestellt wurde, können Sie keine weiteren Nachrichten in das Team importieren.</span><span class="sxs-lookup"><span data-stu-id="62845-200">Once the `completeMigration` request is made, you cannot import further messages into the team.</span></span>

* <span data-ttu-id="62845-201">Teammitglieder können dem neuen Team erst hinzugefügt werden, nachdem `completeMigration` die Anforderung eine erfolgreiche Antwort zurückgegeben hat.</span><span class="sxs-lookup"><span data-stu-id="62845-201">Team members can only be added to the new team after the `completeMigration` request has returned a successful response.</span></span>

* <span data-ttu-id="62845-202">Einschränkung: Nachrichten werden mit 5 RPS pro Kanal importiert.</span><span class="sxs-lookup"><span data-stu-id="62845-202">Throttling: Messages import at 5 RPS per channel.</span></span>

* <span data-ttu-id="62845-203">Wenn Sie eine Korrektur an den Migrationsergebnissen vornehmen müssen, müssen Sie das Team löschen und die Schritte wiederholen, um das Team und den Kanal zu erstellen und die Nachrichten erneut zu migrieren.</span><span class="sxs-lookup"><span data-stu-id="62845-203">If you need to make a correction to the migration results, you need to delete the team and repeat the steps to create the team and channel and re-migrate the messages.</span></span>

> [!NOTE]
> <span data-ttu-id="62845-204">Derzeit sind Inlinebilder die einzige Art von Medien, die vom Schema der Api zum Importieren von Nachrichten unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="62845-204">Currently, inline images are the only type of media supported by the import message API schema.</span></span>

##### <a name="import-content-scope"></a><span data-ttu-id="62845-205">Importieren des Inhaltsbereichs</span><span class="sxs-lookup"><span data-stu-id="62845-205">Import content scope</span></span>

|<span data-ttu-id="62845-206">In-Scope</span><span class="sxs-lookup"><span data-stu-id="62845-206">In-scope</span></span> | <span data-ttu-id="62845-207">Derzeit nicht bereichsbereichsf?n</span><span class="sxs-lookup"><span data-stu-id="62845-207">Currently out-of-scope</span></span>|
|----------|--------------------------|
|<span data-ttu-id="62845-208">Team- und Kanalnachrichten</span><span class="sxs-lookup"><span data-stu-id="62845-208">Team and channel messages</span></span>|<span data-ttu-id="62845-209">1:1 und Gruppenchatnachrichten</span><span class="sxs-lookup"><span data-stu-id="62845-209">1:1 and group chat messages</span></span>|
|<span data-ttu-id="62845-210">Zeitpunkt der Ursprünglichen Nachricht</span><span class="sxs-lookup"><span data-stu-id="62845-210">Created time of the original message</span></span>|<span data-ttu-id="62845-211">Private Kanäle</span><span class="sxs-lookup"><span data-stu-id="62845-211">Private channels</span></span>|
|<span data-ttu-id="62845-212">Inlinebilder als Teil der Nachricht</span><span class="sxs-lookup"><span data-stu-id="62845-212">Inline images as part of the message</span></span>|<span data-ttu-id="62845-213">Erwähnungen</span><span class="sxs-lookup"><span data-stu-id="62845-213">At mentions</span></span>|
|<span data-ttu-id="62845-214">Links zu vorhandenen Dateien in SPO/OneDrive</span><span class="sxs-lookup"><span data-stu-id="62845-214">Links to existing files in SPO/OneDrive</span></span>|<span data-ttu-id="62845-215">Reaktionen</span><span class="sxs-lookup"><span data-stu-id="62845-215">Reactions</span></span>|
|<span data-ttu-id="62845-216">Nachrichten mit Rich-Text</span><span class="sxs-lookup"><span data-stu-id="62845-216">Messages with rich text</span></span>|<span data-ttu-id="62845-217">Videos</span><span class="sxs-lookup"><span data-stu-id="62845-217">Videos</span></span>|
|<span data-ttu-id="62845-218">Nachrichtenantwortkette</span><span class="sxs-lookup"><span data-stu-id="62845-218">Message reply chain</span></span>|<span data-ttu-id="62845-219">Ankündigungen</span><span class="sxs-lookup"><span data-stu-id="62845-219">Announcements</span></span>|
|<span data-ttu-id="62845-220">Verarbeitung mit hohem Durchsatz</span><span class="sxs-lookup"><span data-stu-id="62845-220">High throughput processing</span></span>|<span data-ttu-id="62845-221">Codeausschnitte</span><span class="sxs-lookup"><span data-stu-id="62845-221">Code snippets</span></span>|
||<span data-ttu-id="62845-222">Adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="62845-222">Adaptive cards</span></span>|
||<span data-ttu-id="62845-223">Sticker</span><span class="sxs-lookup"><span data-stu-id="62845-223">Stickers</span></span>|
||<span data-ttu-id="62845-224">Emojis</span><span class="sxs-lookup"><span data-stu-id="62845-224">Emojis</span></span>|
||<span data-ttu-id="62845-225">Anführungszeichen</span><span class="sxs-lookup"><span data-stu-id="62845-225">Quotes</span></span>|
||<span data-ttu-id="62845-226">Übergreifende Beiträge zwischen Kanälen</span><span class="sxs-lookup"><span data-stu-id="62845-226">Cross posts between channels</span></span>|

> [!div class="nextstepaction"]
>[<span data-ttu-id="62845-227">Weitere Informationen zur Integration von Microsoft Graph und Teams</span><span class="sxs-lookup"><span data-stu-id="62845-227">Learn more about Microsoft Graph and Teams integration</span></span>](/graph/teams-concept-overview)
