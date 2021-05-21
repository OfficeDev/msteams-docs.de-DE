---
title: Verwenden von Microsoft Graph zum Importieren externer Plattformnachrichten in Teams
description: Beschreibt, wie Sie Microsoft Graph verwenden, um Nachrichten von einer externen Plattform zu Teams
localization_priority: Normal
author: laujan
ms.author: lajanuar
ms.topic: Overview
keywords: teams import messages api graph microsoft migrate migration post
ms.openlocfilehash: 5ea06e8b490bae0595abb31086848d0b050bded0
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566159"
---
# <a name="import-third-party-platform-messages-to-teams-using-microsoft-graph"></a><span data-ttu-id="47d8f-104">Plattform-Nachrichten von Drittanbietern mithilfe von Microsoft Graph in Teams importieren</span><span class="sxs-lookup"><span data-stu-id="47d8f-104">Import third-party platform messages to Teams using Microsoft Graph</span></span>

<span data-ttu-id="47d8f-105">Mit Microsoft Graph können Sie den vorhandenen Nachrichtenverlauf und die Daten von Benutzern aus einem externen System in einen Teams migrieren.</span><span class="sxs-lookup"><span data-stu-id="47d8f-105">With Microsoft Graph, you can migrate users' existing message history and data from an external system into a Teams channel.</span></span> <span data-ttu-id="47d8f-106">Durch die Aktivierung der Neugestaltung einer Drittanbieterplattform-Messaginghierarchie innerhalb von Teams können Benutzer ihre Kommunikation nahtlos fortsetzen und ohne Unterbrechung fortfahren.</span><span class="sxs-lookup"><span data-stu-id="47d8f-106">By enabling the recreation of a third-party platform messaging hierarchy inside Teams, users can continue their communications in a seamless manner and proceed without interruption.</span></span>

> [!NOTE] 
> <span data-ttu-id="47d8f-107">Microsoft kann in Zukunft von Ihnen oder Ihren Kunden fordern, basierend auf der Menge der importierten Daten, zusätzliche Gebühren zu zahlen.</span><span class="sxs-lookup"><span data-stu-id="47d8f-107">In the future, Microsoft may require you or your customers to pay additional fees based on the amount of data imported.</span></span>

## <a name="import-overview"></a><span data-ttu-id="47d8f-108">Übersicht über den Import</span><span class="sxs-lookup"><span data-stu-id="47d8f-108">Import overview</span></span>

<span data-ttu-id="47d8f-109">Auf einer hohen Ebene besteht der Importvorgang aus folgendem:</span><span class="sxs-lookup"><span data-stu-id="47d8f-109">At a high level, the import process consists of the following:</span></span>

1. [<span data-ttu-id="47d8f-110">Erstellen eines Teams mit einem Back-in-Time-Zeitstempel</span><span class="sxs-lookup"><span data-stu-id="47d8f-110">Create a team with a back-in-time timestamp</span></span>](#step-one-create-a-team)
1. [<span data-ttu-id="47d8f-111">Erstellen eines Kanals mit einem Back-in-Time-Zeitstempel</span><span class="sxs-lookup"><span data-stu-id="47d8f-111">Create a channel with a back-in-time timestamp</span></span>](#step-two-create-a-channel) 
1. [<span data-ttu-id="47d8f-112">Importieren externer Back-in-Time-Nachrichten</span><span class="sxs-lookup"><span data-stu-id="47d8f-112">Import external back-in-time dated messages</span></span>](#step-three-import-messages)
1. [<span data-ttu-id="47d8f-113">Abschließen des Team- und Kanalmigrationsprozesses</span><span class="sxs-lookup"><span data-stu-id="47d8f-113">Complete the team and channel migration process</span></span>](#step-four-complete-migration-mode)
1. [<span data-ttu-id="47d8f-114">Hinzufügen von Teammitgliedern</span><span class="sxs-lookup"><span data-stu-id="47d8f-114">Add team members</span></span>](#step-five-add-team-members)

## <a name="necessary-requirements"></a><span data-ttu-id="47d8f-115">Erforderliche Anforderungen</span><span class="sxs-lookup"><span data-stu-id="47d8f-115">Necessary requirements</span></span>

### <a name="analyze-and-prepare-message-data"></a><span data-ttu-id="47d8f-116">Analysieren und Vorbereiten von Nachrichtendaten</span><span class="sxs-lookup"><span data-stu-id="47d8f-116">Analyze and prepare message data</span></span>

<span data-ttu-id="47d8f-117">✔ Überprüfen Sie die Daten von Drittanbietern, um zu entscheiden, was migriert wird.</span><span class="sxs-lookup"><span data-stu-id="47d8f-117">✔ Review the third-party data to decide what will be migrated.</span></span>  
<span data-ttu-id="47d8f-118">✔ Die ausgewählten Daten aus dem Drittanbieterchatsystem extrahieren.</span><span class="sxs-lookup"><span data-stu-id="47d8f-118">✔ Extract the selected data from the third-party chat system.</span></span>  
<span data-ttu-id="47d8f-119">✔ Ordnen Sie die Chatstruktur eines Drittanbieters der Teams zu.</span><span class="sxs-lookup"><span data-stu-id="47d8f-119">✔ Map the third-party chat structure to the Teams structure.</span></span>  
<span data-ttu-id="47d8f-120">✔ Importieren von Daten in das für die Migration benötigte Format konvertieren.</span><span class="sxs-lookup"><span data-stu-id="47d8f-120">✔ Convert import data into format needed for migration.</span></span>  

### <a name="set-up-your-office-365-tenant"></a><span data-ttu-id="47d8f-121">Einrichten des Office 365-Mandanten</span><span class="sxs-lookup"><span data-stu-id="47d8f-121">Set up your Office 365 tenant</span></span>

<span data-ttu-id="47d8f-122">✔ Stellen Sie sicher, dass Office 365 Mandanten für die Importdaten vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="47d8f-122">✔ Ensure that an Office 365 tenant exists for the import data.</span></span> <span data-ttu-id="47d8f-123">Weitere Informationen zum Einrichten eines Office 365 Mandanten für Teams finden Sie unter [Prepare your Office 365 tenant](../../concepts/build-and-test/prepare-your-o365-tenant.md).</span><span class="sxs-lookup"><span data-stu-id="47d8f-123">For more information on setting up an Office 365 tenancy for Teams, see [Prepare your Office 365 tenant](../../concepts/build-and-test/prepare-your-o365-tenant.md).</span></span>  
<span data-ttu-id="47d8f-124">✔ Stellen Sie sicher, dass sich Teammitglieder in Azure Active Directory (AAD) befinden.</span><span class="sxs-lookup"><span data-stu-id="47d8f-124">✔ Make sure that team members are in Azure Active Directory (AAD).</span></span>  <span data-ttu-id="47d8f-125">Weitere Informationen finden Sie unter [Hinzufügen eines neuen Benutzers](/azure/active-directory/fundamentals/add-users-azure-active-directory) zu Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="47d8f-125">For more information, see [Add a new user](/azure/active-directory/fundamentals/add-users-azure-active-directory) to Azure Active Directory.</span></span>

## <a name="step-one-create-a-team"></a><span data-ttu-id="47d8f-126">Schritt 1: Erstellen eines Teams</span><span class="sxs-lookup"><span data-stu-id="47d8f-126">Step One: Create a team</span></span>

<span data-ttu-id="47d8f-127">Da vorhandene Daten migriert werden, sind die Beibehaltung der ursprünglichen Nachrichtenzeitstempel und das Verhindern von Messagingaktivitäten während des Migrationsprozesses der Schlüssel zum Erstellen des vorhandenen Nachrichtenflusses des Benutzers in Teams.</span><span class="sxs-lookup"><span data-stu-id="47d8f-127">Since existing data is being migrated, maintaining the original message timestamps and preventing messaging activity during the migration process are key to recreating the user's existing message flow in Teams.</span></span> <span data-ttu-id="47d8f-128">Dies wird wie folgt erreicht:</span><span class="sxs-lookup"><span data-stu-id="47d8f-128">This is achieved as follows:</span></span>

> <span data-ttu-id="47d8f-129">[Erstellen Sie ein neues Team](/graph/api/team-post?view=graph-rest-beta&tabs=http&preserve-view=true) mit einem Back-in-Time-Zeitstempel mithilfe der Teamressourceneigenschaft. `createdDateTime`</span><span class="sxs-lookup"><span data-stu-id="47d8f-129">[Create a new team](/graph/api/team-post?view=graph-rest-beta&tabs=http&preserve-view=true) with a back-in-time timestamp using the team resource  `createdDateTime`  property.</span></span> <span data-ttu-id="47d8f-130">Platzieren Sie das neue Team in einem speziellen Zustand, der Benutzer von den meisten Aktivitäten innerhalb des Teams bis zum Abschluss des `migration mode` Migrationsprozesses aussenist.</span><span class="sxs-lookup"><span data-stu-id="47d8f-130">Place the new team in `migration mode`, a special state that bars users from most activities within the team until the migration process is complete.</span></span> <span data-ttu-id="47d8f-131">Fügen Sie `teamCreationMode` das Instanzattribut mit dem Wert in die POST-Anforderung ein, um das neue Team explizit als `migration` für die Migration erstellt zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="47d8f-131">Include the `teamCreationMode` instance attribute with the `migration` value in the POST request to explicitly identify the new team as being created for migration.</span></span>  

> [!Note]
> <span data-ttu-id="47d8f-132">Das Feld wird nur für Instanzen eines Teams oder Kanals aufgefüllt, `createdDateTime` die migriert wurden.</span><span class="sxs-lookup"><span data-stu-id="47d8f-132">The `createdDateTime` field will only be populated for instances of a team or channel that have been migrated.</span></span>

<!-- markdownlint-disable MD001 -->

#### <a name="permissions"></a><span data-ttu-id="47d8f-133">Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="47d8f-133">Permissions</span></span>

|<span data-ttu-id="47d8f-134">ScopeName</span><span class="sxs-lookup"><span data-stu-id="47d8f-134">ScopeName</span></span>|<span data-ttu-id="47d8f-135">DisplayName</span><span class="sxs-lookup"><span data-stu-id="47d8f-135">DisplayName</span></span>|<span data-ttu-id="47d8f-136">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="47d8f-136">Description</span></span>|<span data-ttu-id="47d8f-137">Typ</span><span class="sxs-lookup"><span data-stu-id="47d8f-137">Type</span></span>|<span data-ttu-id="47d8f-138">Administrator-Zustimmung?</span><span class="sxs-lookup"><span data-stu-id="47d8f-138">Admin Consent?</span></span>|<span data-ttu-id="47d8f-139">Abgedeckte Entitäten/APIs</span><span class="sxs-lookup"><span data-stu-id="47d8f-139">Entities/APIs covered</span></span>|
|-|-|-|-|-|-|
|`Teamwork.Migrate.All`|<span data-ttu-id="47d8f-140">Migration zu Microsoft Teams verwalten</span><span class="sxs-lookup"><span data-stu-id="47d8f-140">Manage migration to Microsoft Teams</span></span>|<span data-ttu-id="47d8f-141">Erstellen, Verwalten von Ressourcen für die Migration zu Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="47d8f-141">Creating, managing resources for migration to Microsoft Teams.</span></span>|<span data-ttu-id="47d8f-142">**Nur anwendung**</span><span class="sxs-lookup"><span data-stu-id="47d8f-142">**Application-only**</span></span>|<span data-ttu-id="47d8f-143">**Ja**</span><span class="sxs-lookup"><span data-stu-id="47d8f-143">**Yes**</span></span>|`POST /teams`|

#### <a name="request-create-a-team-in-migration-state"></a><span data-ttu-id="47d8f-144">Anforderung (Erstellen eines Teams im Migrationsstatus)</span><span class="sxs-lookup"><span data-stu-id="47d8f-144">Request (create a team in migration state)</span></span>

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

#### <a name="response"></a><span data-ttu-id="47d8f-145">Antwort</span><span class="sxs-lookup"><span data-stu-id="47d8f-145">Response</span></span>

```http
HTTP/1.1 202 Accepted
Location: /teams/{team-id}/operations/{operation-id}
Content-Location: /teams/{team-id}
```

#### <a name="error-messages"></a><span data-ttu-id="47d8f-146">Fehlermeldungen</span><span class="sxs-lookup"><span data-stu-id="47d8f-146">Error messages</span></span>

```http
400 Bad Request
```

* <span data-ttu-id="47d8f-147">`createdDateTime`  für die Zukunft festgelegt.</span><span class="sxs-lookup"><span data-stu-id="47d8f-147">`createdDateTime`  set for future.</span></span>
* <span data-ttu-id="47d8f-148">`createdDateTime`  richtig angegeben, aber `teamCreationMode`  das Instanzattribut fehlt oder ist auf ungültigen Wert festgelegt.</span><span class="sxs-lookup"><span data-stu-id="47d8f-148">`createdDateTime`  correctly specified, but `teamCreationMode`  instance attribute  is missing or set to invalid value.</span></span>

## <a name="step-two-create-a-channel"></a><span data-ttu-id="47d8f-149">Schritt 2: Erstellen eines Kanals</span><span class="sxs-lookup"><span data-stu-id="47d8f-149">Step Two: Create a channel</span></span>

<span data-ttu-id="47d8f-150">Das Erstellen eines Kanals für die importierten Nachrichten ähnelt dem Erstellen eines Teamszenarios:</span><span class="sxs-lookup"><span data-stu-id="47d8f-150">Creating a channel for the imported messages is similar to the create team scenario:</span></span>

> <span data-ttu-id="47d8f-151">[Erstellen Sie einen neuen Kanal](/graph/api/channel-post?view=graph-rest-v1.0&tabs=http&preserve-view=true) mit einem Back-in-Time-Zeitstempel mithilfe der Kanalressourceneigenschaft. `createdDateTime`</span><span class="sxs-lookup"><span data-stu-id="47d8f-151">[Create a new channel](/graph/api/channel-post?view=graph-rest-v1.0&tabs=http&preserve-view=true) with a back-in-time timestamp using the channel resource `createdDateTime` property.</span></span> <span data-ttu-id="47d8f-152">Platzieren Sie den neuen Kanal in einem speziellen Zustand, der Benutzer von den meisten Chataktivitäten innerhalb des Kanals abt, bis der `migration mode` Migrationsprozess abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="47d8f-152">Place the new channel in `migration mode`, a special state that bars users from most chat activities within the channel until the migration process is complete.</span></span>  <span data-ttu-id="47d8f-153">Fügen Sie `channelCreationMode` das Instanzattribut mit dem Wert in die POST-Anforderung ein, um das neue Team explizit als `migration` für die Migration erstellt zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="47d8f-153">Include the `channelCreationMode` instance attribute with the `migration` value in the POST request to explicitly identify the new team as being created for migration.</span></span>  
<!-- markdownlint-disable MD024 -->
#### <a name="permissions"></a><span data-ttu-id="47d8f-154">Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="47d8f-154">Permissions</span></span>

|<span data-ttu-id="47d8f-155">ScopeName</span><span class="sxs-lookup"><span data-stu-id="47d8f-155">ScopeName</span></span>|<span data-ttu-id="47d8f-156">DisplayName</span><span class="sxs-lookup"><span data-stu-id="47d8f-156">DisplayName</span></span>|<span data-ttu-id="47d8f-157">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="47d8f-157">Description</span></span>|<span data-ttu-id="47d8f-158">Typ</span><span class="sxs-lookup"><span data-stu-id="47d8f-158">Type</span></span>|<span data-ttu-id="47d8f-159">Administrator-Zustimmung?</span><span class="sxs-lookup"><span data-stu-id="47d8f-159">Admin Consent?</span></span>|<span data-ttu-id="47d8f-160">Abgedeckte Entitäten/APIs</span><span class="sxs-lookup"><span data-stu-id="47d8f-160">Entities/APIs covered</span></span>|
|-|-|-|-|-|-|
|`Teamwork.Migrate.All`|<span data-ttu-id="47d8f-161">Migration zu Microsoft Teams verwalten</span><span class="sxs-lookup"><span data-stu-id="47d8f-161">Manage migration to Microsoft Teams</span></span>|<span data-ttu-id="47d8f-162">Erstellen, Verwalten von Ressourcen für die Migration zu Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="47d8f-162">Creating, managing resources for migration to Microsoft Teams.</span></span>|<span data-ttu-id="47d8f-163">**Nur anwendung**</span><span class="sxs-lookup"><span data-stu-id="47d8f-163">**Application-only**</span></span>|<span data-ttu-id="47d8f-164">**Ja**</span><span class="sxs-lookup"><span data-stu-id="47d8f-164">**Yes**</span></span>|`POST /teams`|

#### <a name="request-create-a-channel-in-migration-state"></a><span data-ttu-id="47d8f-165">Anforderung (Erstellen eines Kanals im Migrationsstatus)</span><span class="sxs-lookup"><span data-stu-id="47d8f-165">Request (create a channel in migration state)</span></span>

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

#### <a name="response"></a><span data-ttu-id="47d8f-166">Antwort</span><span class="sxs-lookup"><span data-stu-id="47d8f-166">Response</span></span>

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

#### <a name="error-message"></a><span data-ttu-id="47d8f-167">Fehlermeldung</span><span class="sxs-lookup"><span data-stu-id="47d8f-167">Error message</span></span>

```http
400 Bad Request
```

* <span data-ttu-id="47d8f-168">`createdDateTime`  für die Zukunft festgelegt.</span><span class="sxs-lookup"><span data-stu-id="47d8f-168">`createdDateTime`  set for future.</span></span>
* <span data-ttu-id="47d8f-169">`createdDateTime`  richtig angegeben, `channelCreationMode`  aber das Instanzattribut fehlt oder wird auf ungültigen Wert festgelegt.</span><span class="sxs-lookup"><span data-stu-id="47d8f-169">`createdDateTime`  correctly specified but `channelCreationMode`  instance attribute  is missing or set to invalid value.</span></span>

## <a name="step-three-import-messages"></a><span data-ttu-id="47d8f-170">Schritt 3: Importieren von Nachrichten</span><span class="sxs-lookup"><span data-stu-id="47d8f-170">Step Three: Import messages</span></span>

<span data-ttu-id="47d8f-171">Nachdem das Team und der Kanal erstellt wurden, können Sie mit dem Senden von Back-in-Time-Nachrichten mit den Und-Schlüsseln `createdDateTime` `from`  im Anforderungstext beginnen.</span><span class="sxs-lookup"><span data-stu-id="47d8f-171">After the team and channel have been created, you can begin sending back-in-time messages using the `createdDateTime`  and `from`  keys in the request body.</span></span> <span data-ttu-id="47d8f-172">**HINWEIS:** Nachrichten, die mit `createdDateTime` früheren Nachrichtenthreads importiert `createdDateTime` wurden, werden nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="47d8f-172">**NOTE**: messages imported with `createdDateTime` earlier than the message thread `createdDateTime` is not supported.</span></span>

> [!NOTE]
> * <span data-ttu-id="47d8f-173">`createdDateTime` muss für alle Nachrichten im gleichen Thread eindeutig sein.</span><span class="sxs-lookup"><span data-stu-id="47d8f-173">`createdDateTime` must be unique across messages in the same thread.</span></span>
> * <span data-ttu-id="47d8f-174">`createdDateTime` unterstützt Zeitstempel mit Millisekundengenauigkeit.</span><span class="sxs-lookup"><span data-stu-id="47d8f-174">`createdDateTime` supports timestamps with milliseconds precision.</span></span> <span data-ttu-id="47d8f-175">Wenn die eingehende Anforderungsnachricht beispielsweise den Wert `createdDateTime` *2020-09-16T05:50:31.0025302Z* hat, wird sie in *2020-09-16T05:50:31.002Z* konvertiert, wenn die Nachricht aufgenommen wird.</span><span class="sxs-lookup"><span data-stu-id="47d8f-175">For example, if the incoming request message has the value of `createdDateTime` set as *2020-09-16T05:50:31.0025302Z*, then it would be converted to *2020-09-16T05:50:31.002Z* when the message is ingested.</span></span>

#### <a name="request-post-message-that-is-text-only"></a><span data-ttu-id="47d8f-176">Anforderung (nur Text enthaltende POST-Nachricht)</span><span class="sxs-lookup"><span data-stu-id="47d8f-176">Request (POST message that is text-only)</span></span>

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

#### <a name="response"></a><span data-ttu-id="47d8f-177">Antwort</span><span class="sxs-lookup"><span data-stu-id="47d8f-177">Response</span></span>

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

#### <a name="error-messages"></a><span data-ttu-id="47d8f-178">Fehlermeldungen</span><span class="sxs-lookup"><span data-stu-id="47d8f-178">Error messages</span></span>

```http
400 Bad Request
```

#### <a name="request-post-a-message-with-inline-image"></a><span data-ttu-id="47d8f-179">Anforderung (POST a message with inline image)</span><span class="sxs-lookup"><span data-stu-id="47d8f-179">Request (POST a message with inline image)</span></span>

> [!Note]
> <span data-ttu-id="47d8f-180">In diesem Szenario gibt es keine speziellen Berechtigungsbereiche, da die Anforderung Teil von chatMessage ist. Bereiche für chatMessage gelten auch hier.</span><span class="sxs-lookup"><span data-stu-id="47d8f-180">There are no special permission scopes in this scenario since the request is part of chatMessage; scopes for chatMessage apply here as well.</span></span>

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

#### <a name="response"></a><span data-ttu-id="47d8f-181">Antwort</span><span class="sxs-lookup"><span data-stu-id="47d8f-181">Response</span></span>

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

## <a name="step-four-complete-migration-mode"></a><span data-ttu-id="47d8f-182">Schritt 4: Abschließen des Migrationsmodus</span><span class="sxs-lookup"><span data-stu-id="47d8f-182">Step Four: Complete migration mode</span></span>

<span data-ttu-id="47d8f-183">Sobald der Nachrichtenmigrationsprozess abgeschlossen ist, werden sowohl das Team als auch der Kanal mithilfe der Methode aus dem Migrationsmodus  `completeMigration`  genommen.</span><span class="sxs-lookup"><span data-stu-id="47d8f-183">Once the message migration process has completed, both the team and channel are taken out of migration mode using the  `completeMigration`  method.</span></span> <span data-ttu-id="47d8f-184">In diesem Schritt werden die Team- und Kanalressourcen für die allgemeine Verwendung durch Teammitglieder geöffnet.</span><span class="sxs-lookup"><span data-stu-id="47d8f-184">This step opens the team and channel resources for general use by team members.</span></span> <span data-ttu-id="47d8f-185">Die Aktion ist an die Instanz `team` gebunden.</span><span class="sxs-lookup"><span data-stu-id="47d8f-185">The action is bound to the `team` instance.</span></span> <span data-ttu-id="47d8f-186">Alle Kanäle müssen aus dem Migrationsmodus abgeschlossen werden, bevor das Team abgeschlossen werden kann.</span><span class="sxs-lookup"><span data-stu-id="47d8f-186">All channels must be completed out of migration mode before the team can be completed.</span></span>

#### <a name="request-end-channel-migration-mode"></a><span data-ttu-id="47d8f-187">Anforderung (Endkanalmigrationsmodus)</span><span class="sxs-lookup"><span data-stu-id="47d8f-187">Request (end channel migration mode)</span></span>

```http
POST https://graph.microsoft.com/v1.0/teams/team-id/channels/channel-id/completeMigration

```

#### <a name="response"></a><span data-ttu-id="47d8f-188">Antwort</span><span class="sxs-lookup"><span data-stu-id="47d8f-188">Response</span></span>

```http
HTTP/1.1 204 NoContent
```

#### <a name="request-end-team-migration-mode"></a><span data-ttu-id="47d8f-189">Anforderung (Endteammigrationsmodus)</span><span class="sxs-lookup"><span data-stu-id="47d8f-189">Request (end team migration mode)</span></span>

```http
POST https://graph.microsoft.com/v1.0/teams/team-id/completeMigration
```

#### <a name="response"></a><span data-ttu-id="47d8f-190">Antwort</span><span class="sxs-lookup"><span data-stu-id="47d8f-190">Response</span></span>

```http
HTTP/1.1 204 NoContent
```

* <span data-ttu-id="47d8f-191">Aktion, die für `team` eine oder nicht in aufgerufen `channel` `migrationMode` wird.</span><span class="sxs-lookup"><span data-stu-id="47d8f-191">Action called on a `team` or `channel` that is not in `migrationMode`.</span></span>

## <a name="step-five-add-team-members"></a><span data-ttu-id="47d8f-192">Schritt 5: Hinzufügen von Teammitgliedern</span><span class="sxs-lookup"><span data-stu-id="47d8f-192">Step Five: Add team members</span></span>

<span data-ttu-id="47d8f-193">Sie können einem Team [](https://support.microsoft.com/office/add-members-to-a-team-in-teams-aff2249d-b456-4bc3-81e7-52327b6b38e9) ein Mitglied mithilfe der benutzeroberfläche Teams oder microsoft Graph [Hinzufügen von Mitglied-API](/graph/api/group-post-members?view=graph-rest-beta&tabs=http&preserve-view=true) hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="47d8f-193">You can add a member to a team [using the Teams UI](https://support.microsoft.com/office/add-members-to-a-team-in-teams-aff2249d-b456-4bc3-81e7-52327b6b38e9) or Microsoft Graph [Add member](/graph/api/group-post-members?view=graph-rest-beta&tabs=http&preserve-view=true) API:</span></span>

#### <a name="request-add-member"></a><span data-ttu-id="47d8f-194">Anforderung (Mitglied hinzufügen)</span><span class="sxs-lookup"><span data-stu-id="47d8f-194">Request (add member)</span></span>

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

#### <a name="response"></a><span data-ttu-id="47d8f-195">Antwort</span><span class="sxs-lookup"><span data-stu-id="47d8f-195">Response</span></span>

```http
HTTP/1.1 204 No Content
```

## <a name="tips-and-additional-information"></a><span data-ttu-id="47d8f-196">Tipps und zusätzliche Informationen</span><span class="sxs-lookup"><span data-stu-id="47d8f-196">Tips and additional information</span></span>

<!-- markdownlint-disable MD001 -->
<!-- markdownlint-disable MD026 -->

* <span data-ttu-id="47d8f-197">Nachdem die `completeMigration` Anforderung gestellt wurde, können Sie keine weiteren Nachrichten in das Team importieren.</span><span class="sxs-lookup"><span data-stu-id="47d8f-197">Once the `completeMigration` request is made, you cannot import further messages into the team.</span></span>

* <span data-ttu-id="47d8f-198">Teammitglieder können dem neuen Team erst hinzugefügt werden, nachdem `completeMigration` die Anforderung eine erfolgreiche Antwort zurückgegeben hat.</span><span class="sxs-lookup"><span data-stu-id="47d8f-198">Team members can only be added to the new team after the `completeMigration` request has returned a successful response.</span></span>

* <span data-ttu-id="47d8f-199">Einschränkung: Nachrichten werden mit 5 RPS pro Kanal importiert.</span><span class="sxs-lookup"><span data-stu-id="47d8f-199">Throttling: Messages import at 5 RPS per channel.</span></span>

* <span data-ttu-id="47d8f-200">Wenn Sie eine Korrektur an den Migrationsergebnissen vornehmen müssen, müssen Sie das Team löschen und die Schritte wiederholen, um das Team und den Kanal zu erstellen und die Nachrichten erneut zu migrieren.</span><span class="sxs-lookup"><span data-stu-id="47d8f-200">If you need to make a correction to the migration results, you need to delete the team and repeat the steps to create the team and channel and re-migrate the messages.</span></span>

> [!NOTE]
> <span data-ttu-id="47d8f-201">Derzeit sind Inlinebilder der einzige Medientyp, der vom Apischema für die Importnachricht unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="47d8f-201">Currently, inline images are the only type of media supported by the import message API schema.</span></span>

##### <a name="import-content-scope"></a><span data-ttu-id="47d8f-202">Importieren des Inhaltsbereichs</span><span class="sxs-lookup"><span data-stu-id="47d8f-202">Import content scope</span></span>

|<span data-ttu-id="47d8f-203">In-Scope</span><span class="sxs-lookup"><span data-stu-id="47d8f-203">In-scope</span></span> | <span data-ttu-id="47d8f-204">Derzeit nicht im Bereich</span><span class="sxs-lookup"><span data-stu-id="47d8f-204">Currently out-of-scope</span></span>|
|----------|--------------------------|
|<span data-ttu-id="47d8f-205">Team- und Kanalnachrichten</span><span class="sxs-lookup"><span data-stu-id="47d8f-205">Team and channel messages</span></span>|<span data-ttu-id="47d8f-206">1:1- und Gruppenchatnachrichten</span><span class="sxs-lookup"><span data-stu-id="47d8f-206">1:1 and group chat messages</span></span>|
|<span data-ttu-id="47d8f-207">Erstellter Zeitpunkt der ursprünglichen Nachricht</span><span class="sxs-lookup"><span data-stu-id="47d8f-207">Created time of the original message</span></span>|<span data-ttu-id="47d8f-208">Private Kanäle</span><span class="sxs-lookup"><span data-stu-id="47d8f-208">Private channels</span></span>|
|<span data-ttu-id="47d8f-209">Inlinebilder als Teil der Nachricht</span><span class="sxs-lookup"><span data-stu-id="47d8f-209">Inline images as part of the message</span></span>|<span data-ttu-id="47d8f-210">Bei Erwähnungen</span><span class="sxs-lookup"><span data-stu-id="47d8f-210">At mentions</span></span>|
|<span data-ttu-id="47d8f-211">Links zu vorhandenen Dateien in SPO/OneDrive</span><span class="sxs-lookup"><span data-stu-id="47d8f-211">Links to existing files in SPO/OneDrive</span></span>|<span data-ttu-id="47d8f-212">Reaktionen</span><span class="sxs-lookup"><span data-stu-id="47d8f-212">Reactions</span></span>|
|<span data-ttu-id="47d8f-213">Nachrichten mit Rich Text</span><span class="sxs-lookup"><span data-stu-id="47d8f-213">Messages with rich text</span></span>|<span data-ttu-id="47d8f-214">Videos</span><span class="sxs-lookup"><span data-stu-id="47d8f-214">Videos</span></span>|
|<span data-ttu-id="47d8f-215">Nachrichtenantwortkette</span><span class="sxs-lookup"><span data-stu-id="47d8f-215">Message reply chain</span></span>|<span data-ttu-id="47d8f-216">Ankündigungen</span><span class="sxs-lookup"><span data-stu-id="47d8f-216">Announcements</span></span>|
|<span data-ttu-id="47d8f-217">Verarbeitung mit hohem Durchsatz</span><span class="sxs-lookup"><span data-stu-id="47d8f-217">High throughput processing</span></span>|<span data-ttu-id="47d8f-218">Codeausschnitte</span><span class="sxs-lookup"><span data-stu-id="47d8f-218">Code snippets</span></span>|
||<span data-ttu-id="47d8f-219">Sticker</span><span class="sxs-lookup"><span data-stu-id="47d8f-219">Stickers</span></span>|
||<span data-ttu-id="47d8f-220">Emojis</span><span class="sxs-lookup"><span data-stu-id="47d8f-220">Emojis</span></span>|
||<span data-ttu-id="47d8f-221">Anführungszeichen</span><span class="sxs-lookup"><span data-stu-id="47d8f-221">Quotes</span></span>|
||<span data-ttu-id="47d8f-222">Übergreifende Beiträge zwischen Kanälen</span><span class="sxs-lookup"><span data-stu-id="47d8f-222">Cross posts between channels</span></span>|


## <a name="see-also"></a><span data-ttu-id="47d8f-223">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="47d8f-223">See also</span></span>

[<span data-ttu-id="47d8f-224">Erfahren Sie mehr über microsoft Graph und Teams Integration</span><span class="sxs-lookup"><span data-stu-id="47d8f-224">Learn more about Microsoft Graph and Teams integration</span></span>](/graph/teams-concept-overview)
