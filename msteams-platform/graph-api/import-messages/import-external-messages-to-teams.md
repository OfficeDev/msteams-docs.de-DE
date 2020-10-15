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
# <a name="import-third-party-platform-messages-to-teams-using-microsoft-graph"></a><span data-ttu-id="33b23-104">Plattform-Nachrichten von Drittanbietern mithilfe von Microsoft Graph in Teams importieren</span><span class="sxs-lookup"><span data-stu-id="33b23-104">Import third-party platform messages to Teams using Microsoft Graph</span></span>

>[!IMPORTANT]
> <span data-ttu-id="33b23-105">Microsoft Graph und Microsoft Teams öffentliche Vorschauen stehen für den frühzeitigen Zugriff und das Feedback zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="33b23-105">Microsoft Graph and Microsoft Teams public previews are available for early-access and feedback.</span></span> <span data-ttu-id="33b23-106">Obwohl diese Version umfangreiche Tests unterzogen wurde, ist Sie nicht für die Verwendung in der Produktion vorgesehen.</span><span class="sxs-lookup"><span data-stu-id="33b23-106">Although this release has undergone extensive testing, it is not intended for use in production.</span></span>

<span data-ttu-id="33b23-107">Mit Microsoft Graph können Sie den vorhandenen Nachrichtenverlauf und die Daten von Benutzern aus einem externen System in einen Teams-Kanal migrieren.</span><span class="sxs-lookup"><span data-stu-id="33b23-107">With Microsoft Graph, you can migrate users' existing message history and data from an external system into a Teams channel.</span></span> <span data-ttu-id="33b23-108">Durch die Aktivierung einer Drittanbieter-Platt Form Messaging-Hierarchie in Microsoft Teams können Benutzer ihre Kommunikation nahtlos fortsetzen und ohne Unterbrechung fortfahren.</span><span class="sxs-lookup"><span data-stu-id="33b23-108">By enabling the recreation of a third-party platform messaging hierarchy inside Teams, users can continue their communications in a seamless manner and proceed without interruption.</span></span>

## <a name="import-overview"></a><span data-ttu-id="33b23-109">Import (Übersicht)</span><span class="sxs-lookup"><span data-stu-id="33b23-109">Import overview</span></span>

<span data-ttu-id="33b23-110">Auf hohem Niveau besteht der Importvorgang aus folgenden Elementen:</span><span class="sxs-lookup"><span data-stu-id="33b23-110">At a high level, the import process consists of the following:</span></span>

1. [<span data-ttu-id="33b23-111">Erstellen eines Teams mit einem Back-in-Time-Zeitstempel</span><span class="sxs-lookup"><span data-stu-id="33b23-111">Create a team with a back-in-time timestamp</span></span>](#step-one-create-a-team)
1. [<span data-ttu-id="33b23-112">Erstellen eines Kanals mit einem Back-in-Time-Zeitstempel</span><span class="sxs-lookup"><span data-stu-id="33b23-112">Create a channel with a back-in-time timestamp</span></span>](#step-two-create-a-channel)  
1. [<span data-ttu-id="33b23-113">Importieren externer Back-in-Time datierter Nachrichten</span><span class="sxs-lookup"><span data-stu-id="33b23-113">Import external back-in-time dated messages</span></span>](#step-three-import-messages)
1. [<span data-ttu-id="33b23-114">Abschließen des Migrationsprozesses für Teams und Kanäle</span><span class="sxs-lookup"><span data-stu-id="33b23-114">Complete the team and channel migration process</span></span>](#step-four-complete-migration-mode)
1. [<span data-ttu-id="33b23-115">Hinzufügen von Teammitgliedern</span><span class="sxs-lookup"><span data-stu-id="33b23-115">Add team members</span></span>](#step-five-add-team-members)

## <a name="necessary-requirements"></a><span data-ttu-id="33b23-116">Erforderliche Anforderungen</span><span class="sxs-lookup"><span data-stu-id="33b23-116">Necessary requirements</span></span>

### <a name="analyze-and-prepare-message-data"></a><span data-ttu-id="33b23-117">Analysieren und Vorbereiten von Nachrichtendaten</span><span class="sxs-lookup"><span data-stu-id="33b23-117">Analyze and prepare message data</span></span>

<span data-ttu-id="33b23-118">✔ Überprüfen Sie die drittanbieterdaten, um zu entscheiden, was migriert werden soll.</span><span class="sxs-lookup"><span data-stu-id="33b23-118">✔ Review the third-party data to decide what will be migrated.</span></span>  
<span data-ttu-id="33b23-119">✔ Extrahieren Sie die ausgewählten Daten aus dem Drittanbieter-Chat System.</span><span class="sxs-lookup"><span data-stu-id="33b23-119">✔ Extract the selected data from the third-party chat system.</span></span>  
<span data-ttu-id="33b23-120">✔ Ordnen Sie die Chat Struktur eines Drittanbieters der Teams-Struktur zu.</span><span class="sxs-lookup"><span data-stu-id="33b23-120">✔ Map the third-party chat structure to the Teams structure.</span></span>  
<span data-ttu-id="33b23-121">✔ Konvertieren von Importdaten in Format, das für die Migration benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="33b23-121">✔ Convert import data into format needed for migration.</span></span>  

### <a name="set-up-your-office-365-tenant"></a><span data-ttu-id="33b23-122">Einrichten des Office 365-Mandanten</span><span class="sxs-lookup"><span data-stu-id="33b23-122">Set up your Office 365 tenant</span></span>

<span data-ttu-id="33b23-123">✔ Sicherstellen, dass ein Office 365 Mandant für die Importdaten vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="33b23-123">✔ Ensure that an Office 365 tenant exists for the import data.</span></span> <span data-ttu-id="33b23-124">Weitere Informationen zum Einrichten eines Office 365 Mandanten für Teams *finden Sie unter* [Vorbereiten des Office 365 Mandanten](../../concepts/build-and-test/prepare-your-o365-tenant.md).</span><span class="sxs-lookup"><span data-stu-id="33b23-124">For more information on setting up an Office 365 tenancy for Teams, *see*, [Prepare your Office 365 tenant](../../concepts/build-and-test/prepare-your-o365-tenant.md).</span></span>  
<span data-ttu-id="33b23-125">✔ Stellen Sie sicher, dass sich die Teammitglieder in Azure Active Directory (AAD) befinden.</span><span class="sxs-lookup"><span data-stu-id="33b23-125">✔ Make sure that team members are in Azure Active Directory (AAD).</span></span>  <span data-ttu-id="33b23-126">Weitere Informationen *finden Sie unter* [Hinzufügen eines neuen Benutzers](/azure/active-directory/fundamentals/add-users-azure-active-directory) zu Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="33b23-126">For more information *see* [Add a new user](/azure/active-directory/fundamentals/add-users-azure-active-directory) to Azure Active Directory.</span></span>

## <a name="step-one-create-a-team"></a><span data-ttu-id="33b23-127">Schritt 1: Erstellen eines Teams</span><span class="sxs-lookup"><span data-stu-id="33b23-127">Step One: Create a team</span></span>

<span data-ttu-id="33b23-128">Da vorhandene Daten migriert werden, sind die Beibehaltung der ursprünglichen Nachrichtenzeitstempel und das verhindern von Messaging Aktivitäten während des Migrationsprozesses entscheidend, um den vorhandenen Nachrichtenfluss des Benutzers in Microsoft Teams neu zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="33b23-128">Since existing data is being migrated, maintaining the original message timestamps and preventing messaging activity during the migration process are key to recreating the user's existing message flow in Teams.</span></span> <span data-ttu-id="33b23-129">Dies wird wie folgt erreicht:</span><span class="sxs-lookup"><span data-stu-id="33b23-129">This is achieved as follows:</span></span>

> <span data-ttu-id="33b23-130">[Erstellen Sie ein neues Team](/graph/api/team-post?view=graph-rest-beta&tabs=http&preserve-view=true) mit einem Back-in-Time-Zeitstempel mithilfe der Team Resource  `createdDateTime`  -Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="33b23-130">[Create a new team](/graph/api/team-post?view=graph-rest-beta&tabs=http&preserve-view=true) with a back-in-time timestamp using the team resource  `createdDateTime`  property.</span></span> <span data-ttu-id="33b23-131">Platzieren Sie das neue Team in `migration mode` , einem besonderen Status, der Benutzer von den meisten Aktivitäten innerhalb des Teams bis zum Abschluss des Migrationsvorgangs verriegelt.</span><span class="sxs-lookup"><span data-stu-id="33b23-131">Place the new team in `migration mode`, a special state that bars users from most activities within the team until the migration process is complete.</span></span> <span data-ttu-id="33b23-132">Fügen `teamCreationMode` Sie das Instanz-Attribut mit dem `migration` Wert in die Post-Anforderung ein, um das neue Team explizit als für die Migration erstellt zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="33b23-132">Include the `teamCreationMode` instance attribute with the `migration` value in the POST request to explicitly identify the new team as being created for migration.</span></span>  

> <span data-ttu-id="33b23-133">**Hinweis**: das `createdDateTime` Feld wird nur für Instanzen eines Teams oder Kanals aufgefüllt, die migriert wurden.</span><span class="sxs-lookup"><span data-stu-id="33b23-133">**NOTE**:  The `createdDateTime` field will only be populated for instances of a team or channel that have been migrated.</span></span>

<!-- markdownlint-disable MD001 -->

#### <a name="permissions"></a><span data-ttu-id="33b23-134">Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="33b23-134">Permissions</span></span>

|<span data-ttu-id="33b23-135">ScopeName</span><span class="sxs-lookup"><span data-stu-id="33b23-135">ScopeName</span></span>|<span data-ttu-id="33b23-136">DisplayName</span><span class="sxs-lookup"><span data-stu-id="33b23-136">DisplayName</span></span>|<span data-ttu-id="33b23-137">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="33b23-137">Description</span></span>|<span data-ttu-id="33b23-138">Typ</span><span class="sxs-lookup"><span data-stu-id="33b23-138">Type</span></span>|<span data-ttu-id="33b23-139">Zustimmung des Administrators?</span><span class="sxs-lookup"><span data-stu-id="33b23-139">Admin Consent?</span></span>|<span data-ttu-id="33b23-140">Behandelte Entitäten/APIs</span><span class="sxs-lookup"><span data-stu-id="33b23-140">Entities/APIs covered</span></span>|
|-|-|-|-|-|-|
|`Teamwork.Migrate.All`|<span data-ttu-id="33b23-141">Migration zu Microsoft Teams verwalten</span><span class="sxs-lookup"><span data-stu-id="33b23-141">Manage migration to Microsoft Teams</span></span>|<span data-ttu-id="33b23-142">Erstellen und Verwalten von Ressourcen für die Migration zu Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="33b23-142">Creating, managing resources for migration to Microsoft Teams</span></span>|<span data-ttu-id="33b23-143">**Nur Anwendung**</span><span class="sxs-lookup"><span data-stu-id="33b23-143">**Application-only**</span></span>|<span data-ttu-id="33b23-144">**Ja**</span><span class="sxs-lookup"><span data-stu-id="33b23-144">**Yes**</span></span>|`POST /teams`|

#### <a name="request-create-a-team-in-migration-state"></a><span data-ttu-id="33b23-145">Anforderung (Erstellen eines Teams im Migrationsstatus)</span><span class="sxs-lookup"><span data-stu-id="33b23-145">Request (create a team in migration state)</span></span>

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

#### <a name="response"></a><span data-ttu-id="33b23-146">Antwort</span><span class="sxs-lookup"><span data-stu-id="33b23-146">Response</span></span>

```http
HTTP/1.1 202 Accepted
Location: /teams/{teamId}/operations/{operationId}
Content-Location: /teams/{teamId}
```

#### <a name="error-messages"></a><span data-ttu-id="33b23-147">Fehlermeldungen</span><span class="sxs-lookup"><span data-stu-id="33b23-147">Error messages</span></span>

```http
400 Bad Request
```

* <span data-ttu-id="33b23-148">`createdDateTime`  für Zukunft festgelegt.</span><span class="sxs-lookup"><span data-stu-id="33b23-148">`createdDateTime`  set for future.</span></span>
* <span data-ttu-id="33b23-149">`createdDateTime`  richtig angegeben, `teamCreationMode`  das Instanz-Attribut fehlt oder ist auf ungültigen Wert festgelegt.</span><span class="sxs-lookup"><span data-stu-id="33b23-149">`createdDateTime`  correctly specified, but `teamCreationMode`  instance attribute  is missing or set to invalid value.</span></span>

## <a name="step-two-create-a-channel"></a><span data-ttu-id="33b23-150">Schritt 2: Erstellen eines Kanals</span><span class="sxs-lookup"><span data-stu-id="33b23-150">Step Two: Create a channel</span></span>

<span data-ttu-id="33b23-151">Das Erstellen eines Kanals für die importierten Nachrichten ähnelt dem Szenario zum Erstellen eines Teams:</span><span class="sxs-lookup"><span data-stu-id="33b23-151">Creating a channel for the imported messages is similar to the create team scenario:</span></span>

> <span data-ttu-id="33b23-152">Erstellen Sie mithilfe der Channel-Ressourceneigenschaft [einen neuen Kanal](/graph/api/channel-post?view=graph-rest-beta&tabs=http&preserve-view=true) mit einem Back-in-Time-Zeitstempel `createdDateTime` .</span><span class="sxs-lookup"><span data-stu-id="33b23-152">[Create a new channel](/graph/api/channel-post?view=graph-rest-beta&tabs=http&preserve-view=true) with a back-in-time timestamp using the channel resource `createdDateTime` property.</span></span> <span data-ttu-id="33b23-153">Platzieren Sie den neuen Kanal in `migration mode` , einen besonderen Status, der Benutzer von den meisten chataktivitäten innerhalb des Kanals bis zum Abschluss des Migrationsprozesses verriegelt.</span><span class="sxs-lookup"><span data-stu-id="33b23-153">Place the new channel in `migration mode`, a special state that bars users from most chat activities within the channel until the migration process is complete.</span></span>  <span data-ttu-id="33b23-154">Fügen `channelCreationMode` Sie das Instanz-Attribut mit dem `migration` Wert in die Post-Anforderung ein, um das neue Team explizit als für die Migration erstellt zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="33b23-154">Include the `channelCreationMode` instance attribute with the `migration` value in the POST request to explicitly identify the new team as being created for migration.</span></span>  
<!-- markdownlint-disable MD024 -->
#### <a name="permissions"></a><span data-ttu-id="33b23-155">Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="33b23-155">Permissions</span></span>

|<span data-ttu-id="33b23-156">ScopeName</span><span class="sxs-lookup"><span data-stu-id="33b23-156">ScopeName</span></span>|<span data-ttu-id="33b23-157">DisplayName</span><span class="sxs-lookup"><span data-stu-id="33b23-157">DisplayName</span></span>|<span data-ttu-id="33b23-158">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="33b23-158">Description</span></span>|<span data-ttu-id="33b23-159">Typ</span><span class="sxs-lookup"><span data-stu-id="33b23-159">Type</span></span>|<span data-ttu-id="33b23-160">Zustimmung des Administrators?</span><span class="sxs-lookup"><span data-stu-id="33b23-160">Admin Consent?</span></span>|<span data-ttu-id="33b23-161">Behandelte Entitäten/APIs</span><span class="sxs-lookup"><span data-stu-id="33b23-161">Entities/APIs covered</span></span>|
|-|-|-|-|-|-|
|`Teamwork.Migrate.All`|<span data-ttu-id="33b23-162">Migration zu Microsoft Teams verwalten</span><span class="sxs-lookup"><span data-stu-id="33b23-162">Manage migration to Microsoft Teams</span></span>|<span data-ttu-id="33b23-163">Erstellen und Verwalten von Ressourcen für die Migration zu Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="33b23-163">Creating, managing resources for migration to Microsoft Teams</span></span>|<span data-ttu-id="33b23-164">**Nur Anwendung**</span><span class="sxs-lookup"><span data-stu-id="33b23-164">**Application-only**</span></span>|<span data-ttu-id="33b23-165">**Ja**</span><span class="sxs-lookup"><span data-stu-id="33b23-165">**Yes**</span></span>|`POST /teams`|

#### <a name="request-create-a-channel-in-migration-state"></a><span data-ttu-id="33b23-166">Anforderung (Kanal im Migrationsstatus erstellen)</span><span class="sxs-lookup"><span data-stu-id="33b23-166">Request (create a channel in migration state)</span></span>

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

#### <a name="response"></a><span data-ttu-id="33b23-167">Antwort</span><span class="sxs-lookup"><span data-stu-id="33b23-167">Response</span></span>

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

* <span data-ttu-id="33b23-168">`createdDateTime`  für Zukunft festgelegt.</span><span class="sxs-lookup"><span data-stu-id="33b23-168">`createdDateTime`  set for future.</span></span>
* <span data-ttu-id="33b23-169">`createdDateTime`  richtig angegeben `channelCreationMode`  , das Instanz-Attribut fehlt oder ist auf ungültigen Wert festgelegt.</span><span class="sxs-lookup"><span data-stu-id="33b23-169">`createdDateTime`  correctly specified but `channelCreationMode`  instance attribute  is missing or set to invalid value.</span></span>

## <a name="step-three-import-messages"></a><span data-ttu-id="33b23-170">Schritt 3: Importieren von Nachrichten</span><span class="sxs-lookup"><span data-stu-id="33b23-170">Step Three: Import messages</span></span>

<span data-ttu-id="33b23-171">Nachdem das Team und der Kanal erstellt wurden, können Sie mit dem Senden von Back-in-Time-Nachrichten mit den `createdDateTime`  und- `from`  Tasten im Anforderungstext beginnen.</span><span class="sxs-lookup"><span data-stu-id="33b23-171">After the team and channel have been created, you can begin sending back-in-time messages using the `createdDateTime`  and `from`  keys in the request body.</span></span> <span data-ttu-id="33b23-172">**Hinweis**: Nachrichten, `createdDateTime` die zuvor mit dem Nachrichtenthread importiert wurden `createdDateTime` , werden nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="33b23-172">**NOTE**: messages imported with `createdDateTime` earlier than the message thread `createdDateTime` is not supported.</span></span>

> [!NOTE]
> <span data-ttu-id="33b23-173">createdDateTime muss für Nachrichten in demselben Thread eindeutig sein.</span><span class="sxs-lookup"><span data-stu-id="33b23-173">createdDateTime must be unique across messages in the same thread.</span></span>

#### <a name="request-post-message-that-is-text-only"></a><span data-ttu-id="33b23-174">Request (Nachricht nur Text bereitstellen)</span><span class="sxs-lookup"><span data-stu-id="33b23-174">Request (POST message that is text-only)</span></span>

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

#### <a name="response"></a><span data-ttu-id="33b23-175">Antwort</span><span class="sxs-lookup"><span data-stu-id="33b23-175">Response</span></span>

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

#### <a name="error-messages"></a><span data-ttu-id="33b23-176">Fehlermeldungen</span><span class="sxs-lookup"><span data-stu-id="33b23-176">Error messages</span></span>

```http
400 Bad Request
```

#### <a name="request-post-a-message-with-inline-image"></a><span data-ttu-id="33b23-177">Anforderung (Senden einer Nachricht mit Inlinebild)</span><span class="sxs-lookup"><span data-stu-id="33b23-177">Request (POST a message with inline image)</span></span>

> <span data-ttu-id="33b23-178">**Hinweis**: in diesem Szenario gibt es keine speziellen Berechtigungs Bereiche, da die Anforderung Teil von Chat Message ist; Bereiche für Chat Message gelten auch hier.</span><span class="sxs-lookup"><span data-stu-id="33b23-178">**Note**: There are no special permission scopes in this scenario since the request is part of chatMessage; scopes for chatMessage apply here as well.</span></span>

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

#### <a name="response"></a><span data-ttu-id="33b23-179">Antwort</span><span class="sxs-lookup"><span data-stu-id="33b23-179">Response</span></span>

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

## <a name="step-four-complete-migration-mode"></a><span data-ttu-id="33b23-180">Schritt 4: vollständiger Migrationsmodus</span><span class="sxs-lookup"><span data-stu-id="33b23-180">Step Four: Complete migration mode</span></span>

<span data-ttu-id="33b23-181">Nachdem der Nachrichten Migrationsprozess abgeschlossen ist, werden sowohl das Team als auch der Kanal mithilfe der-Methode aus dem Migrationsmodus genommen  `completeMigration`  .</span><span class="sxs-lookup"><span data-stu-id="33b23-181">Once the message migration process has completed, both the team and channel are taken out of migration mode using the  `completeMigration`  method.</span></span> <span data-ttu-id="33b23-182">In diesem Schritt werden die Team-und Kanal Ressourcen für die allgemeine Verwendung durch Teammitglieder geöffnet.</span><span class="sxs-lookup"><span data-stu-id="33b23-182">This step opens the team and channel resources for general use by team members.</span></span> <span data-ttu-id="33b23-183">Die Aktion ist an die `team` Instanz gebunden.</span><span class="sxs-lookup"><span data-stu-id="33b23-183">The action is bound to the `team` instance.</span></span>

#### <a name="request-end-team-migration-mode"></a><span data-ttu-id="33b23-184">Anforderung (Ende Team Migrationsmodus)</span><span class="sxs-lookup"><span data-stu-id="33b23-184">Request (end team migration mode)</span></span>

```http
POST https://graph.microsoft.com/beta/teams/teamId/completeMigration

```

#### <a name="response"></a><span data-ttu-id="33b23-185">Antwort</span><span class="sxs-lookup"><span data-stu-id="33b23-185">Response</span></span>

```http
HTTP/1.1 204 NoContent
```

#### <a name="request-end-channel-migration-mode"></a><span data-ttu-id="33b23-186">Request (End Channel-Migrationsmodus)</span><span class="sxs-lookup"><span data-stu-id="33b23-186">Request (end channel migration mode)</span></span>

```http
POST https://graph.microsoft.com/beta/teams/teamId/channels/channelId/completeMigration

```

#### <a name="response"></a><span data-ttu-id="33b23-187">Antwort</span><span class="sxs-lookup"><span data-stu-id="33b23-187">Response</span></span>

```http
HTTP/1.1 204 NoContent
```

#### <a name="error-response"></a><span data-ttu-id="33b23-188">Fehlerantwort</span><span class="sxs-lookup"><span data-stu-id="33b23-188">Error response</span></span>

```http
400 Bad Request
```

* <span data-ttu-id="33b23-189">Aktion mit dem Namen "a" `team` oder " `channel` nicht in" aufgerufen `migrationMode` .</span><span class="sxs-lookup"><span data-stu-id="33b23-189">Action called on a `team` or `channel` that is not in `migrationMode`.</span></span>

## <a name="step-five-add-team-members"></a><span data-ttu-id="33b23-190">Schritt 5: Hinzufügen von Teammitgliedern</span><span class="sxs-lookup"><span data-stu-id="33b23-190">Step Five: Add team members</span></span>

<span data-ttu-id="33b23-191">Sie können ein Mitglied zu einem Team hinzufügen, [indem Sie die Benutzeroberfläche von Teams oder die](https://support.microsoft.com/office/add-members-to-a-team-in-teams-aff2249d-b456-4bc3-81e7-52327b6b38e9) [Add Member](/graph/api/group-post-members?view=graph-rest-beta&tabs=http&preserve-view=true) -API von Microsoft Graph verwenden:</span><span class="sxs-lookup"><span data-stu-id="33b23-191">You can add a member to a team [using the Teams UI](https://support.microsoft.com/office/add-members-to-a-team-in-teams-aff2249d-b456-4bc3-81e7-52327b6b38e9) or Microsoft Graph [Add member](/graph/api/group-post-members?view=graph-rest-beta&tabs=http&preserve-view=true) API:</span></span>

#### <a name="request-add-member"></a><span data-ttu-id="33b23-192">Request (Add Member)</span><span class="sxs-lookup"><span data-stu-id="33b23-192">Request (add member)</span></span>

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

#### <a name="response"></a><span data-ttu-id="33b23-193">Antwort</span><span class="sxs-lookup"><span data-stu-id="33b23-193">Response</span></span>

```http
HTTP/1.1 204 No Content
```

## <a name="tips-and-additional-information"></a><span data-ttu-id="33b23-194">Tipps und zusätzliche Informationen</span><span class="sxs-lookup"><span data-stu-id="33b23-194">Tips and additional information</span></span>

<!-- markdownlint-disable MD001 -->
<!-- markdownlint-disable MD026 -->

* <span data-ttu-id="33b23-195">Sie können Nachrichten von Benutzern importieren, die sich nicht in Microsoft Teams befinden.</span><span class="sxs-lookup"><span data-stu-id="33b23-195">You can import messages from users who are not in Teams.</span></span> <span data-ttu-id="33b23-196">**Hinweis**: Nachrichten, die für Benutzer importiert werden, die nicht im Mandanten vorhanden sind, können während der öffentlichen Vorschau nicht in den Teams-Client-oder Compliance-Portalen durchsucht werden.</span><span class="sxs-lookup"><span data-stu-id="33b23-196">**NOTE**: Messages imported for users not present in the tenant will not be searchable in the Teams client or compliance portals during Public Preview.</span></span>

* <span data-ttu-id="33b23-197">Nachdem die `completeMigration` Anforderung gestellt wurde, können Sie keine weiteren Nachrichten in das Team importieren.</span><span class="sxs-lookup"><span data-stu-id="33b23-197">Once the `completeMigration` request is made, you cannot import further messages into the team.</span></span>

* <span data-ttu-id="33b23-198">Teammitglieder können dem neuen Team nur hinzugefügt werden, nachdem die `completeMigration` Anforderung eine erfolgreiche Antwort zurückgegeben hat.</span><span class="sxs-lookup"><span data-stu-id="33b23-198">Team members can only be added to the new team after the `completeMigration` request has returned a successful response.</span></span>

* <span data-ttu-id="33b23-199">Drosselung: Nachrichten werden mit 5 RPS pro Kanal importiert.</span><span class="sxs-lookup"><span data-stu-id="33b23-199">Throttling: Messages import at 5 RPS per channel.</span></span>

* <span data-ttu-id="33b23-200">Wenn Sie eine Korrektur an den Migrations Ergebnissen vornehmen müssen, müssen Sie das Team löschen und die Schritte wiederholen, um das Team zu erstellen und die Nachrichten erneut zu migrieren.</span><span class="sxs-lookup"><span data-stu-id="33b23-200">If you need to make a correction to the migration results, you need to delete the team and repeat the steps to create the team and channel and re-migrate the messages.</span></span>

> [!NOTE]
> <span data-ttu-id="33b23-201">Derzeit sind Inline Bilder die einzige Art von Medien, die vom API-Schema für die Import Nachrichten unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="33b23-201">Currently, inline images are the only type of media supported by the import message API schema.</span></span>

##### <a name="import-content-scope"></a><span data-ttu-id="33b23-202">Inhaltsbereich importieren</span><span class="sxs-lookup"><span data-stu-id="33b23-202">Import content scope</span></span>

|<span data-ttu-id="33b23-203">Im Bereich</span><span class="sxs-lookup"><span data-stu-id="33b23-203">In-scope</span></span> | <span data-ttu-id="33b23-204">Derzeit außerhalb des Bereichs</span><span class="sxs-lookup"><span data-stu-id="33b23-204">Currently out-of-scope</span></span>|
|----------|--------------------------|
|<span data-ttu-id="33b23-205">Team-und Kanal Nachrichten</span><span class="sxs-lookup"><span data-stu-id="33b23-205">Team and channel messages</span></span>|<span data-ttu-id="33b23-206">1:1-und Gruppenchatnachrichten</span><span class="sxs-lookup"><span data-stu-id="33b23-206">1:1 and group chat messages</span></span>|
|<span data-ttu-id="33b23-207">Erstellter Zeitpunkt der ursprünglichen Nachricht</span><span class="sxs-lookup"><span data-stu-id="33b23-207">Created time of the original message</span></span>|<span data-ttu-id="33b23-208">Private Kanäle</span><span class="sxs-lookup"><span data-stu-id="33b23-208">Private channels</span></span>|
|<span data-ttu-id="33b23-209">Inline Bilder als Teil der Nachricht</span><span class="sxs-lookup"><span data-stu-id="33b23-209">Inline images as part of the message</span></span>|<span data-ttu-id="33b23-210">Unter Erwähnungen</span><span class="sxs-lookup"><span data-stu-id="33b23-210">At mentions</span></span>|
|<span data-ttu-id="33b23-211">Links zu vorhandenen Dateien in SpO/OneDrive</span><span class="sxs-lookup"><span data-stu-id="33b23-211">Links to existing files in SPO/OneDrive</span></span>|<span data-ttu-id="33b23-212">Reaktionen</span><span class="sxs-lookup"><span data-stu-id="33b23-212">Reactions</span></span>|
|<span data-ttu-id="33b23-213">Nachrichten mit Rich-Text</span><span class="sxs-lookup"><span data-stu-id="33b23-213">Messages with rich text</span></span>|<span data-ttu-id="33b23-214">Videos</span><span class="sxs-lookup"><span data-stu-id="33b23-214">Videos</span></span>|
|<span data-ttu-id="33b23-215">Nachrichten Antwort Kette</span><span class="sxs-lookup"><span data-stu-id="33b23-215">Message reply chain</span></span>|<span data-ttu-id="33b23-216">Announcements</span><span class="sxs-lookup"><span data-stu-id="33b23-216">Announcements</span></span>|
|<span data-ttu-id="33b23-217">Verarbeitung mit hohem Durchsatz</span><span class="sxs-lookup"><span data-stu-id="33b23-217">High throughput processing</span></span>|<span data-ttu-id="33b23-218">Codeausschnitte</span><span class="sxs-lookup"><span data-stu-id="33b23-218">Code snippets</span></span>|
||<span data-ttu-id="33b23-219">Adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="33b23-219">Adaptive cards</span></span>|
||<span data-ttu-id="33b23-220">Sticker</span><span class="sxs-lookup"><span data-stu-id="33b23-220">Stickers</span></span>|
||<span data-ttu-id="33b23-221">Emojis</span><span class="sxs-lookup"><span data-stu-id="33b23-221">Emojis</span></span>|
||<span data-ttu-id="33b23-222">Anführungszeichen</span><span class="sxs-lookup"><span data-stu-id="33b23-222">Quotes</span></span>|
||<span data-ttu-id="33b23-223">Cross-Posts zwischen Kanälen</span><span class="sxs-lookup"><span data-stu-id="33b23-223">Cross posts between channels</span></span>|

> [!div class="nextstepaction"]
>[<span data-ttu-id="33b23-224">Weitere Informationen zur Integration von Microsoft Graph und Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="33b23-224">Learn more about Microsoft Graph and Teams integration</span></span>](/graph/teams-concept-overview)
