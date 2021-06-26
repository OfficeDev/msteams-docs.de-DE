---
title: Verwenden von Microsoft Graph zum Importieren externer Plattformnachrichten in Teams
description: Beschreibt, wie Microsoft Graph zum Importieren von Nachrichten von einer externen Plattform in Teams
localization_priority: Normal
author: akjo
ms.author: lajanuar
ms.topic: Overview
keywords: Teams importieren Nachrichten-API-Diagramm Microsoft migrieren Migrationsbeitrag
ms.openlocfilehash: 95cbf6bf2deac4ea71e60fe0fece06c1dd3ad24c
ms.sourcegitcommit: 656a1de9e23e0ad90dddcb93a2bbfcc63848a856
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2021
ms.locfileid: "53130094"
---
# <a name="import-third-party-platform-messages-to-teams-using-microsoft-graph"></a><span data-ttu-id="3ee24-104">Plattform-Nachrichten von Drittanbietern mithilfe von Microsoft Graph in Teams importieren</span><span class="sxs-lookup"><span data-stu-id="3ee24-104">Import third-party platform messages to Teams using Microsoft Graph</span></span>

<span data-ttu-id="3ee24-105">Mit Microsoft Graph können Sie den vorhandenen Nachrichtenverlauf und die Daten von Benutzern aus einem externen System in einen Teams Kanal migrieren.</span><span class="sxs-lookup"><span data-stu-id="3ee24-105">With Microsoft Graph, you can migrate users' existing message history and data from an external system into a Teams channel.</span></span> <span data-ttu-id="3ee24-106">Durch die Aktivierung der Neugestaltung einer Drittanbieterplattform-Messaginghierarchie innerhalb Teams können Benutzer ihre Kommunikation nahtlos fortsetzen und ohne Unterbrechung fortfahren.</span><span class="sxs-lookup"><span data-stu-id="3ee24-106">By enabling the recreation of a third-party platform messaging hierarchy inside Teams, users can continue their communications in a seamless manner and proceed without interruption.</span></span>

> [!NOTE]
> <span data-ttu-id="3ee24-107">Microsoft kann in Zukunft von Ihnen oder Ihren Kunden fordern, basierend auf der Menge der importierten Daten, zusätzliche Gebühren zu zahlen.</span><span class="sxs-lookup"><span data-stu-id="3ee24-107">In the future, Microsoft may require you or your customers to pay additional fees based on the amount of data imported.</span></span>

## <a name="import-overview"></a><span data-ttu-id="3ee24-108">Übersicht über den Import</span><span class="sxs-lookup"><span data-stu-id="3ee24-108">Import overview</span></span>

<span data-ttu-id="3ee24-109">Auf hoher Ebene besteht der Importvorgang aus folgenden Komponenten:</span><span class="sxs-lookup"><span data-stu-id="3ee24-109">At a high level, the import process consists of the following:</span></span>

1. <span data-ttu-id="3ee24-110">[Erstellen Sie ein Team mit einem Back-in-Time-Zeitstempel.](#step-1-create-a-team)</span><span class="sxs-lookup"><span data-stu-id="3ee24-110">[Create a team with a back-in-time timestamp](#step-1-create-a-team).</span></span>
1. <span data-ttu-id="3ee24-111">[Erstellen Sie einen Kanal mit einem Back-in-Time-Zeitstempel.](#step-2-create-a-channel)</span><span class="sxs-lookup"><span data-stu-id="3ee24-111">[Create a channel with a back-in-time timestamp](#step-2-create-a-channel).</span></span>
1. <span data-ttu-id="3ee24-112">[Importieren sie externe Back-in-Time-Nachrichten.](#step-3-import-messages)</span><span class="sxs-lookup"><span data-stu-id="3ee24-112">[Import external back-in-time dated messages](#step-3-import-messages).</span></span>
1. <span data-ttu-id="3ee24-113">[Schließen Sie den Migrationsprozess für Team und Kanal ab.](#step-4-complete-migration-mode)</span><span class="sxs-lookup"><span data-stu-id="3ee24-113">[Complete the team and channel migration process](#step-4-complete-migration-mode).</span></span>
1. <span data-ttu-id="3ee24-114">[Fügen Sie Teammitglieder hinzu.](#step-five-add-team-members)</span><span class="sxs-lookup"><span data-stu-id="3ee24-114">[Add team members](#step-five-add-team-members).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3ee24-115">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="3ee24-115">Prerequisites</span></span>

### <a name="analyze-and-prepare-message-data"></a><span data-ttu-id="3ee24-116">Analysieren und Vorbereiten von Nachrichtendaten</span><span class="sxs-lookup"><span data-stu-id="3ee24-116">Analyze and prepare message data</span></span>

* <span data-ttu-id="3ee24-117">Überprüfen Sie die Drittanbieterdaten, um zu entscheiden, was migriert wird.</span><span class="sxs-lookup"><span data-stu-id="3ee24-117">Review the third-party data to decide what will be migrated.</span></span>  
* <span data-ttu-id="3ee24-118">Extrahieren Sie die ausgewählten Daten aus dem Drittanbieter-Chatsystem.</span><span class="sxs-lookup"><span data-stu-id="3ee24-118">Extract the selected data from the third-party chat system.</span></span>  
* <span data-ttu-id="3ee24-119">Ordnen Sie die Chatstruktur eines Drittanbieters der Teams Struktur zu.</span><span class="sxs-lookup"><span data-stu-id="3ee24-119">Map the third-party chat structure to the Teams structure.</span></span>  
* <span data-ttu-id="3ee24-120">Konvertieren von Importdaten in das für die Migration erforderliche Format.</span><span class="sxs-lookup"><span data-stu-id="3ee24-120">Convert import data into format needed for migration.</span></span>  

### <a name="set-up-your-office-365-tenant"></a><span data-ttu-id="3ee24-121">Einrichten des Office 365-Mandanten</span><span class="sxs-lookup"><span data-stu-id="3ee24-121">Set up your Office 365 tenant</span></span>

* <span data-ttu-id="3ee24-122">Stellen Sie sicher, dass für die Importdaten ein Office 365 Mandanten vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="3ee24-122">Ensure that an Office 365 tenant exists for the import data.</span></span> <span data-ttu-id="3ee24-123">Weitere Informationen zum Einrichten eines Office 365 Mandanten für Teams finden Sie unter [Vorbereiten Ihres Office 365 Mandanten.](../../concepts/build-and-test/prepare-your-o365-tenant.md)</span><span class="sxs-lookup"><span data-stu-id="3ee24-123">For more information on setting up an Office 365 tenancy for Teams, see [prepare your Office 365 tenant](../../concepts/build-and-test/prepare-your-o365-tenant.md).</span></span>
* <span data-ttu-id="3ee24-124">Stellen Sie sicher, dass sich Teammitglieder in Azure Active Directory (AAD) befinden.</span><span class="sxs-lookup"><span data-stu-id="3ee24-124">Make sure that team members are in Azure Active Directory (AAD).</span></span> <span data-ttu-id="3ee24-125">Weitere Informationen finden Sie unter [Hinzufügen eines neuen Benutzers](/azure/active-directory/fundamentals/add-users-azure-active-directory) zu AAD.</span><span class="sxs-lookup"><span data-stu-id="3ee24-125">For more information, see [add a new user](/azure/active-directory/fundamentals/add-users-azure-active-directory) to AAD.</span></span>

## <a name="step-1-create-a-team"></a><span data-ttu-id="3ee24-126">Schritt 1: Erstellen eines Teams</span><span class="sxs-lookup"><span data-stu-id="3ee24-126">Step 1: Create a team</span></span>

<span data-ttu-id="3ee24-127">Da Sie vorhandene Daten migrieren, sind die Aufrechterhaltung der ursprünglichen Nachrichtenzeitstempel und das Verhindern von Nachrichtenaktivitäten während des Migrationsprozesses entscheidend, um den vorhandenen Nachrichtenfluss des Benutzers in Teams neu zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="3ee24-127">Since you are migrating existing data, maintaining the original message timestamps and preventing messaging activity during the migration process are key to recreating the user's existing message flow in Teams.</span></span> <span data-ttu-id="3ee24-128">Dies wird wie folgt erreicht:</span><span class="sxs-lookup"><span data-stu-id="3ee24-128">This is achieved as follows:</span></span>

> <span data-ttu-id="3ee24-129">[Erstellen Sie ein neues Team](/graph/api/team-post?view=graph-rest-beta&tabs=http&preserve-view=true) mit einem Back-in-Timestamp mithilfe der Teamressourceneigenschaft. `createdDateTime`</span><span class="sxs-lookup"><span data-stu-id="3ee24-129">[Create a new team](/graph/api/team-post?view=graph-rest-beta&tabs=http&preserve-view=true) with a back-in-time timestamp using the team resource `createdDateTime` property.</span></span> <span data-ttu-id="3ee24-130">Platzieren Sie das neue Team in einem speziellen Zustand, der `migration mode` Benutzer von den meisten Aktivitäten innerhalb des Teams bis zum Abschluss des Migrationsprozesses einschränkt.</span><span class="sxs-lookup"><span data-stu-id="3ee24-130">Place the new team in `migration mode`, a special state that restricts users from most activities within the team until the migration process is complete.</span></span> <span data-ttu-id="3ee24-131">Schließen Sie das `teamCreationMode` Instanzattribut mit dem `migration` Wert in die POST-Anforderung ein, um das neue Team explizit als für die Migration erstellt zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="3ee24-131">Include the `teamCreationMode` instance attribute with the `migration` value in the POST request to explicitly identify the new team as being created for migration.</span></span>  

> [!NOTE]
> <span data-ttu-id="3ee24-132">Das `createdDateTime` Feld wird nur für Instanzen eines Teams oder Kanals ausgefüllt, die migriert wurden.</span><span class="sxs-lookup"><span data-stu-id="3ee24-132">The `createdDateTime` field will only be populated for instances of a team or channel that have been migrated.</span></span>

<!-- markdownlint-disable MD001 -->

#### <a name="permission"></a><span data-ttu-id="3ee24-133">Berechtigung</span><span class="sxs-lookup"><span data-stu-id="3ee24-133">Permission</span></span>

|<span data-ttu-id="3ee24-134">ScopeName</span><span class="sxs-lookup"><span data-stu-id="3ee24-134">ScopeName</span></span>|<span data-ttu-id="3ee24-135">DisplayName</span><span class="sxs-lookup"><span data-stu-id="3ee24-135">DisplayName</span></span>|<span data-ttu-id="3ee24-136">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3ee24-136">Description</span></span>|<span data-ttu-id="3ee24-137">Typ</span><span class="sxs-lookup"><span data-stu-id="3ee24-137">Type</span></span>|<span data-ttu-id="3ee24-138">Administratorzustimmung?</span><span class="sxs-lookup"><span data-stu-id="3ee24-138">Admin Consent?</span></span>|<span data-ttu-id="3ee24-139">Behandelte Entitäten/APIs</span><span class="sxs-lookup"><span data-stu-id="3ee24-139">Entities/APIs covered</span></span>|
|-|-|-|-|-|-|
|`Teamwork.Migrate.All`|<span data-ttu-id="3ee24-140">Migration zu Microsoft Teams verwalten</span><span class="sxs-lookup"><span data-stu-id="3ee24-140">Manage migration to Microsoft Teams</span></span>|<span data-ttu-id="3ee24-141">Erstellen und Verwalten von Ressourcen für die Migration zu Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="3ee24-141">Creating and managing resources for migration to Microsoft Teams.</span></span>|<span data-ttu-id="3ee24-142">**Nur-Anwendung**</span><span class="sxs-lookup"><span data-stu-id="3ee24-142">**Application-only**</span></span>|<span data-ttu-id="3ee24-143">**Ja**</span><span class="sxs-lookup"><span data-stu-id="3ee24-143">**Yes**</span></span>|`POST /teams`|

#### <a name="request-create-a-team-in-migration-state"></a><span data-ttu-id="3ee24-144">Anforderung (Erstellen eines Teams im Migrationsstatus)</span><span class="sxs-lookup"><span data-stu-id="3ee24-144">Request (create a team in migration state)</span></span>

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

#### <a name="response"></a><span data-ttu-id="3ee24-145">Antwort</span><span class="sxs-lookup"><span data-stu-id="3ee24-145">Response</span></span>

```http
HTTP/1.1 202 Accepted
Location: /teams/{team-id}/operations/{operation-id}
Content-Location: /teams/{team-id}
```

#### <a name="error-message"></a><span data-ttu-id="3ee24-146">Fehlermeldung</span><span class="sxs-lookup"><span data-stu-id="3ee24-146">Error message</span></span>

```http
400 Bad Request
```

<span data-ttu-id="3ee24-147">Sie können die Fehlermeldung in den folgenden Szenarien erhalten:</span><span class="sxs-lookup"><span data-stu-id="3ee24-147">You can receive the error message in the following scenarios:</span></span>

* <span data-ttu-id="3ee24-148">Wenn `createdDateTime` für die Zukunft festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="3ee24-148">If `createdDateTime` is set for future.</span></span>
* <span data-ttu-id="3ee24-149">Wenn `createdDateTime` richtig angegeben, aber `teamCreationMode` das Instanzattribut fehlt oder auf einen ungültigen Wert festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="3ee24-149">If `createdDateTime` is correctly specified, but `teamCreationMode` instance attribute is missing or set to invalid value.</span></span>

## <a name="step-2-create-a-channel"></a><span data-ttu-id="3ee24-150">Schritt 2: Erstellen eines Kanals</span><span class="sxs-lookup"><span data-stu-id="3ee24-150">Step 2: Create a channel</span></span>

<span data-ttu-id="3ee24-151">Das Erstellen eines Kanals für die importierten Nachrichten ähnelt dem Szenario "Team erstellen":</span><span class="sxs-lookup"><span data-stu-id="3ee24-151">Creating a channel for the imported messages is similar to the create team scenario:</span></span>

> <span data-ttu-id="3ee24-152">[Erstellen Sie einen neuen Kanal](/graph/api/channel-post?view=graph-rest-v1.0&tabs=http&preserve-view=true) mit einem Back-in-Timestamp mithilfe der Kanalressourceneigenschaft. `createdDateTime`</span><span class="sxs-lookup"><span data-stu-id="3ee24-152">[Create a new channel](/graph/api/channel-post?view=graph-rest-v1.0&tabs=http&preserve-view=true) with a back-in-time timestamp using the channel resource `createdDateTime` property.</span></span> <span data-ttu-id="3ee24-153">Platzieren Sie den neuen Kanal in einem speziellen Zustand, der `migration mode` Benutzer von den meisten Chataktivitäten innerhalb des Kanals bis zum Abschluss des Migrationsvorgangs einschränkt.</span><span class="sxs-lookup"><span data-stu-id="3ee24-153">Place the new channel in `migration mode`, a special state that restricts users from most chat activities within the channel until the migration process is complete.</span></span> <span data-ttu-id="3ee24-154">Schließen Sie das `channelCreationMode` Instanzattribut mit dem `migration` Wert in die POST-Anforderung ein, um das neue Team explizit als für die Migration erstellt zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="3ee24-154">Include the `channelCreationMode` instance attribute with the `migration` value in the POST request to explicitly identify the new team as being created for migration.</span></span>  
<!-- markdownlint-disable MD024 -->
#### <a name="permission"></a><span data-ttu-id="3ee24-155">Berechtigung</span><span class="sxs-lookup"><span data-stu-id="3ee24-155">Permission</span></span>

|<span data-ttu-id="3ee24-156">ScopeName</span><span class="sxs-lookup"><span data-stu-id="3ee24-156">ScopeName</span></span>|<span data-ttu-id="3ee24-157">DisplayName</span><span class="sxs-lookup"><span data-stu-id="3ee24-157">DisplayName</span></span>|<span data-ttu-id="3ee24-158">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3ee24-158">Description</span></span>|<span data-ttu-id="3ee24-159">Typ</span><span class="sxs-lookup"><span data-stu-id="3ee24-159">Type</span></span>|<span data-ttu-id="3ee24-160">Administratorzustimmung?</span><span class="sxs-lookup"><span data-stu-id="3ee24-160">Admin Consent?</span></span>|<span data-ttu-id="3ee24-161">Behandelte Entitäten/APIs</span><span class="sxs-lookup"><span data-stu-id="3ee24-161">Entities/APIs covered</span></span>|
|-|-|-|-|-|-|
|`Teamwork.Migrate.All`|<span data-ttu-id="3ee24-162">Migration zu Microsoft Teams verwalten</span><span class="sxs-lookup"><span data-stu-id="3ee24-162">Manage migration to Microsoft Teams</span></span>|<span data-ttu-id="3ee24-163">Erstellen und Verwalten von Ressourcen für die Migration zu Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="3ee24-163">Creating and managing resources for migration to Microsoft Teams.</span></span>|<span data-ttu-id="3ee24-164">**Nur-Anwendung**</span><span class="sxs-lookup"><span data-stu-id="3ee24-164">**Application-only**</span></span>|<span data-ttu-id="3ee24-165">**Ja**</span><span class="sxs-lookup"><span data-stu-id="3ee24-165">**Yes**</span></span>|`POST /teams`|

#### <a name="request-create-a-channel-in-migration-state"></a><span data-ttu-id="3ee24-166">Anforderung (Erstellen eines Kanals im Migrationsstatus)</span><span class="sxs-lookup"><span data-stu-id="3ee24-166">Request (create a channel in migration state)</span></span>

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

#### <a name="response"></a><span data-ttu-id="3ee24-167">Antwort</span><span class="sxs-lookup"><span data-stu-id="3ee24-167">Response</span></span>

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

#### <a name="error-message"></a><span data-ttu-id="3ee24-168">Fehlermeldung</span><span class="sxs-lookup"><span data-stu-id="3ee24-168">Error message</span></span>

```http
400 Bad Request
```
<span data-ttu-id="3ee24-169">Sie können die Fehlermeldung in den folgenden Szenarien erhalten:</span><span class="sxs-lookup"><span data-stu-id="3ee24-169">You can receive the error message in the following scenarios:</span></span>

* <span data-ttu-id="3ee24-170">Wenn `createdDateTime` für die Zukunft festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="3ee24-170">If `createdDateTime` is set for future.</span></span>
* <span data-ttu-id="3ee24-171">Wenn `createdDateTime` richtig angegeben ist, das `channelCreationMode` Instanzattribut jedoch fehlt oder auf einen ungültigen Wert festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="3ee24-171">If `createdDateTime` is correctly specified but `channelCreationMode` instance attribute is missing or set to invalid value.</span></span>

## <a name="step-3-import-messages"></a><span data-ttu-id="3ee24-172">Schritt 3: Importieren von Nachrichten</span><span class="sxs-lookup"><span data-stu-id="3ee24-172">Step 3: Import messages</span></span>

<span data-ttu-id="3ee24-173">Nachdem das Team und der Kanal erstellt wurden, können Sie mit dem Senden von Back-in-Time-Nachrichten mithilfe der `createdDateTime` `from` Schlüssel im Anforderungstext beginnen.</span><span class="sxs-lookup"><span data-stu-id="3ee24-173">After the team and channel have been created, you can begin sending back-in-time messages using the `createdDateTime`  and `from` keys in the request body.</span></span>

> [!NOTE]
> * <span data-ttu-id="3ee24-174">Nachrichten, die mit `createdDateTime` früher als dem Nachrichtenthread importiert `createdDateTime` wurden, werden nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="3ee24-174">Messages imported with `createdDateTime` earlier than the message thread `createdDateTime` is not supported.</span></span>
> * <span data-ttu-id="3ee24-175">`createdDateTime` muss nachrichtenübergreifend im selben Thread eindeutig sein.</span><span class="sxs-lookup"><span data-stu-id="3ee24-175">`createdDateTime` must be unique across messages in the same thread.</span></span>
> * <span data-ttu-id="3ee24-176">`createdDateTime` unterstützt Zeitstempel mit Millisekunden-Genauigkeit.</span><span class="sxs-lookup"><span data-stu-id="3ee24-176">`createdDateTime` supports timestamps with milliseconds precision.</span></span> <span data-ttu-id="3ee24-177">Wenn die eingehende Anforderungsnachricht beispielsweise den Wert `createdDateTime` *2020-09-16T05:50:31.0025302Z* hat, wird sie in *2020-09-16T05:50:31.002Z* konvertiert, wenn die Nachricht aufgenommen wird.</span><span class="sxs-lookup"><span data-stu-id="3ee24-177">For example, if the incoming request message has the value of `createdDateTime` set as *2020-09-16T05:50:31.0025302Z*, then it would be converted to *2020-09-16T05:50:31.002Z* when the message is ingested.</span></span>

#### <a name="request-post-message-that-is-text-only"></a><span data-ttu-id="3ee24-178">Anforderung (NUR-TEXT-POST-Nachricht)</span><span class="sxs-lookup"><span data-stu-id="3ee24-178">Request (POST message that is text-only)</span></span>

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

#### <a name="response"></a><span data-ttu-id="3ee24-179">Antwort</span><span class="sxs-lookup"><span data-stu-id="3ee24-179">Response</span></span>

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

#### <a name="error-message"></a><span data-ttu-id="3ee24-180">Fehlermeldung</span><span class="sxs-lookup"><span data-stu-id="3ee24-180">Error message</span></span>

```http
400 Bad Request
```

#### <a name="request-post-a-message-with-inline-image"></a><span data-ttu-id="3ee24-181">Anforderung (POST eine Nachricht mit Inlinebild)</span><span class="sxs-lookup"><span data-stu-id="3ee24-181">Request (POST a message with inline image)</span></span>

> [!NOTE]
> * <span data-ttu-id="3ee24-182">In diesem Szenario gibt es keine speziellen Berechtigungsbereiche, da die Anforderung Teil von `chatMessage` ist.</span><span class="sxs-lookup"><span data-stu-id="3ee24-182">There are no special permission scopes in this scenario since the request is part of `chatMessage`.</span></span>
> * <span data-ttu-id="3ee24-183">Hier gelten die Bereiche, die `chatMessage` gelten.</span><span class="sxs-lookup"><span data-stu-id="3ee24-183">The scopes for `chatMessage` apply here.</span></span>

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

#### <a name="response"></a><span data-ttu-id="3ee24-184">Antwort</span><span class="sxs-lookup"><span data-stu-id="3ee24-184">Response</span></span>

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

## <a name="step-4-complete-migration-mode"></a><span data-ttu-id="3ee24-185">Schritt 4: Abschließen des Migrationsmodus</span><span class="sxs-lookup"><span data-stu-id="3ee24-185">Step 4: Complete migration mode</span></span>

<span data-ttu-id="3ee24-186">Nachdem der Nachrichtenmigrationsprozess abgeschlossen ist, werden sowohl das Team als auch der Kanal mithilfe der Methode aus dem Migrationsmodus  `completeMigration` ausgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="3ee24-186">After the message migration process has completed, both the team and channel are taken out of migration mode using the  `completeMigration` method.</span></span> <span data-ttu-id="3ee24-187">In diesem Schritt werden die Team- und Kanalressourcen für die allgemeine Verwendung durch Teammitglieder geöffnet.</span><span class="sxs-lookup"><span data-stu-id="3ee24-187">This step opens the team and channel resources for general use by team members.</span></span> <span data-ttu-id="3ee24-188">Die Aktion ist an die `team` Instanz gebunden.</span><span class="sxs-lookup"><span data-stu-id="3ee24-188">The action is bound to the `team` instance.</span></span> <span data-ttu-id="3ee24-189">Bevor das Team abgeschlossen ist, müssen alle Kanäle außerhalb des Migrationsmodus abgeschlossen sein.</span><span class="sxs-lookup"><span data-stu-id="3ee24-189">Before the team completes, all channels must be completed out of migration mode.</span></span>

#### <a name="request-end-channel-migration-mode"></a><span data-ttu-id="3ee24-190">Anforderung (Ende des Kanalmigrationsmodus)</span><span class="sxs-lookup"><span data-stu-id="3ee24-190">Request (end channel migration mode)</span></span>

```http
POST https://graph.microsoft.com/v1.0/teams/team-id/channels/channel-id/completeMigration

```

#### <a name="response"></a><span data-ttu-id="3ee24-191">Antwort</span><span class="sxs-lookup"><span data-stu-id="3ee24-191">Response</span></span>

```http
HTTP/1.1 204 NoContent
```

#### <a name="request-end-team-migration-mode"></a><span data-ttu-id="3ee24-192">Anforderung (Teammigrationsmodus beenden)</span><span class="sxs-lookup"><span data-stu-id="3ee24-192">Request (end team migration mode)</span></span>

```http
POST https://graph.microsoft.com/v1.0/teams/team-id/completeMigration
```

#### <a name="response"></a><span data-ttu-id="3ee24-193">Antwort</span><span class="sxs-lookup"><span data-stu-id="3ee24-193">Response</span></span>

```http
HTTP/1.1 204 NoContent
```

<span data-ttu-id="3ee24-194">Aktion, die für eine `team` aufgerufen wird oder die sich nicht in `channel` `migrationMode` befindet.</span><span class="sxs-lookup"><span data-stu-id="3ee24-194">Action called on a `team` or `channel` that is not in `migrationMode`.</span></span>

## <a name="step-five-add-team-members"></a><span data-ttu-id="3ee24-195">Schritt 5: Hinzufügen von Teammitgliedern</span><span class="sxs-lookup"><span data-stu-id="3ee24-195">Step five: Add team members</span></span>

<span data-ttu-id="3ee24-196">Sie können ein Mitglied zu einem Team [hinzufügen, indem Sie die Teams-Benutzeroberfläche](https://support.microsoft.com/office/add-members-to-a-team-in-teams-aff2249d-b456-4bc3-81e7-52327b6b38e9) verwenden, oder Microsoft Graph [Mitglieder-API hinzufügen:](/graph/api/group-post-members?view=graph-rest-beta&tabs=http&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="3ee24-196">You can add a member to a team [using the Teams UI](https://support.microsoft.com/office/add-members-to-a-team-in-teams-aff2249d-b456-4bc3-81e7-52327b6b38e9) or Microsoft Graph [add member](/graph/api/group-post-members?view=graph-rest-beta&tabs=http&preserve-view=true) API:</span></span>

#### <a name="request-add-member"></a><span data-ttu-id="3ee24-197">Anforderung (Mitglied hinzufügen)</span><span class="sxs-lookup"><span data-stu-id="3ee24-197">Request (add member)</span></span>

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

#### <a name="response"></a><span data-ttu-id="3ee24-198">Antwort</span><span class="sxs-lookup"><span data-stu-id="3ee24-198">Response</span></span>

```http
HTTP/1.1 204 No Content
```

## <a name="tips-and-additional-information"></a><span data-ttu-id="3ee24-199">Tipps und zusätzliche Informationen</span><span class="sxs-lookup"><span data-stu-id="3ee24-199">Tips and additional information</span></span>

<!-- markdownlint-disable MD001 -->
<!-- markdownlint-disable MD026 -->

* <span data-ttu-id="3ee24-200">Nachdem die `completeMigration` Anforderung gestellt wurde, können Sie keine weiteren Nachrichten in das Team importieren.</span><span class="sxs-lookup"><span data-stu-id="3ee24-200">After the `completeMigration` request is made, you cannot import further messages into the team.</span></span>

* <span data-ttu-id="3ee24-201">Sie können dem neuen Team nur Teammitglieder hinzufügen, nachdem die `completeMigration` Anforderung eine erfolgreiche Antwort zurückgegeben hat.</span><span class="sxs-lookup"><span data-stu-id="3ee24-201">You can only add team members to the new team after the `completeMigration` request has returned a successful response.</span></span>

* <span data-ttu-id="3ee24-202">Einschränkung: Nachrichten werden mit fünf RPS pro Kanal importiert.</span><span class="sxs-lookup"><span data-stu-id="3ee24-202">Throttling: Messages import at five RPS per channel.</span></span>

* <span data-ttu-id="3ee24-203">Wenn Sie eine Korrektur an den Migrationsergebnissen vornehmen müssen, müssen Sie das Team löschen und die Schritte wiederholen, um das Team und den Kanal zu erstellen und die Nachrichten erneut zu migrieren.</span><span class="sxs-lookup"><span data-stu-id="3ee24-203">If you need to make a correction to the migration results, you must delete the team and repeat the steps to create the team and channel and re-migrate the messages.</span></span>

> [!NOTE]
> <span data-ttu-id="3ee24-204">Derzeit sind Inlinebilder der einzige Medientyp, der vom Importnachrichten-API-Schema unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="3ee24-204">Currently, inline images are the only type of media supported by the import message API schema.</span></span>

##### <a name="import-content-scope"></a><span data-ttu-id="3ee24-205">Importieren des Inhaltsbereichs</span><span class="sxs-lookup"><span data-stu-id="3ee24-205">Import content scope</span></span>

<span data-ttu-id="3ee24-206">Die folgende Tabelle enthält den Inhaltsbereich:</span><span class="sxs-lookup"><span data-stu-id="3ee24-206">The following table provides the content scope:</span></span>

|<span data-ttu-id="3ee24-207">In-Scope</span><span class="sxs-lookup"><span data-stu-id="3ee24-207">In-scope</span></span> | <span data-ttu-id="3ee24-208">Derzeit außerhalb des Gültigkeitsbereichs</span><span class="sxs-lookup"><span data-stu-id="3ee24-208">Currently out-of-scope</span></span>|
|----------|--------------------------|
|<span data-ttu-id="3ee24-209">Team- und Kanalnachrichten</span><span class="sxs-lookup"><span data-stu-id="3ee24-209">Team and channel messages</span></span>|<span data-ttu-id="3ee24-210">1:1- und Gruppenchatnachrichten</span><span class="sxs-lookup"><span data-stu-id="3ee24-210">1:1 and group chat messages</span></span>|
|<span data-ttu-id="3ee24-211">Erstellungszeitpunkt der ursprünglichen Nachricht</span><span class="sxs-lookup"><span data-stu-id="3ee24-211">Created time of the original message</span></span>|<span data-ttu-id="3ee24-212">Private Kanäle</span><span class="sxs-lookup"><span data-stu-id="3ee24-212">Private channels</span></span>|
|<span data-ttu-id="3ee24-213">Inlinebilder als Teil der Nachricht</span><span class="sxs-lookup"><span data-stu-id="3ee24-213">Inline images as part of the message</span></span>|<span data-ttu-id="3ee24-214">Bei Erwähnungen</span><span class="sxs-lookup"><span data-stu-id="3ee24-214">At mentions</span></span>|
|<span data-ttu-id="3ee24-215">Links zu vorhandenen Dateien in SPO oder OneDrive</span><span class="sxs-lookup"><span data-stu-id="3ee24-215">Links to existing files in SPO or OneDrive</span></span>|<span data-ttu-id="3ee24-216">Reaktionen</span><span class="sxs-lookup"><span data-stu-id="3ee24-216">Reactions</span></span>|
|<span data-ttu-id="3ee24-217">Nachrichten mit Rich-Text</span><span class="sxs-lookup"><span data-stu-id="3ee24-217">Messages with rich text</span></span>|<span data-ttu-id="3ee24-218">Videos</span><span class="sxs-lookup"><span data-stu-id="3ee24-218">Videos</span></span>|
|<span data-ttu-id="3ee24-219">Nachrichtenantwortkette</span><span class="sxs-lookup"><span data-stu-id="3ee24-219">Message reply chain</span></span>|<span data-ttu-id="3ee24-220">Ankündigungen</span><span class="sxs-lookup"><span data-stu-id="3ee24-220">Announcements</span></span>|
|<span data-ttu-id="3ee24-221">Verarbeitung mit hohem Durchsatz</span><span class="sxs-lookup"><span data-stu-id="3ee24-221">High throughput processing</span></span>|<span data-ttu-id="3ee24-222">Codeausschnitte</span><span class="sxs-lookup"><span data-stu-id="3ee24-222">Code snippets</span></span>|
||<span data-ttu-id="3ee24-223">Sticker</span><span class="sxs-lookup"><span data-stu-id="3ee24-223">Stickers</span></span>|
||<span data-ttu-id="3ee24-224">Emojis</span><span class="sxs-lookup"><span data-stu-id="3ee24-224">Emojis</span></span>|
||<span data-ttu-id="3ee24-225">Zitate</span><span class="sxs-lookup"><span data-stu-id="3ee24-225">Quotes</span></span>|
||<span data-ttu-id="3ee24-226">Beiträge zwischen Kanälen querstellen</span><span class="sxs-lookup"><span data-stu-id="3ee24-226">Cross posts between channels</span></span>|


## <a name="see-also"></a><span data-ttu-id="3ee24-227">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="3ee24-227">See also</span></span>

[<span data-ttu-id="3ee24-228">Integration von Microsoft Graph und Teams</span><span class="sxs-lookup"><span data-stu-id="3ee24-228">Microsoft Graph and Teams integration</span></span>](/graph/teams-concept-overview)
