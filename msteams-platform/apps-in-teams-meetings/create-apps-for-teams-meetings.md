---
title: Apps für Teams-Besprechungen erstellen
author: laujan
description: Erstellen von Apps für Teams-Besprechungen
ms.topic: conceptual
ms.author: lajanuar
keywords: Rollen-API für Teams-Apps-Besprechungen für Benutzerteilnehmer
ms.openlocfilehash: bd0f53ae34a23bdbbdc2e6f3992c7dd0836e9f28
ms.sourcegitcommit: 5cb3453e918bec1173899e7591b48a48113cf8f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2021
ms.locfileid: "50449493"
---
# <a name="create-apps-for-teams-meetings"></a><span data-ttu-id="7396c-104">Apps für Teams-Besprechungen erstellen</span><span class="sxs-lookup"><span data-stu-id="7396c-104">Create apps for Teams meetings</span></span>

## <a name="prerequisites-and-considerations"></a><span data-ttu-id="7396c-105">Voraussetzungen und Überlegungen</span><span class="sxs-lookup"><span data-stu-id="7396c-105">Prerequisites and considerations</span></span>

* <span data-ttu-id="7396c-106">Apps in Besprechungen erfordern grundlegende Kenntnisse der [Teams-App-Entwicklung.](../overview.md)</span><span class="sxs-lookup"><span data-stu-id="7396c-106">Apps in meetings require some basic knowledge of [Teams app development](../overview.md).</span></span> <span data-ttu-id="7396c-107">Eine App in einer Besprechung kann aus Features [](../messaging-extensions/what-are-messaging-extensions.md) für Registerkarten, [Bots](../tabs/what-are-tabs.md)und Messagingerweiterungen bestehen und erfordert Updates für das Teams-App-Manifest, um anzugeben, dass die App für Besprechungen verfügbar ist. [](../bots/what-are-bots.md) [](#update-your-app-manifest)</span><span class="sxs-lookup"><span data-stu-id="7396c-107">An app in a meeting can comprise of [tabs](../tabs/what-are-tabs.md), [bots](../bots/what-are-bots.md), and [messaging extensions](../messaging-extensions/what-are-messaging-extensions.md) features and will require updates to the Teams [app manifest](#update-your-app-manifest) to indicate that the app is available for meetings</span></span>

* <span data-ttu-id="7396c-108">Damit Ihre App im Besprechungslebenszyklus als Registerkarte funktioniert, muss sie konfigurierbare Registerkarten im [Gruppenchatbereich](../resources/schema/manifest-schema.md#configurabletabs) unterstützen (siehe Erstellen einer [Gruppenregisterkarte](../build-your-first-app/build-channel-tab.md)).</span><span class="sxs-lookup"><span data-stu-id="7396c-108">For your app to function in the meeting lifecycle as a tab, it must support configurable tabs in the [groupchat scope](../resources/schema/manifest-schema.md#configurabletabs) (see how to [build a group tab](../build-your-first-app/build-channel-tab.md)).</span></span> <span data-ttu-id="7396c-109">Wenn Sie `groupchat` den Bereich unterstützen, wird Ihre App in [Chats](teams-apps-in-meetings.md#pre-meeting-app-experience) vor und [nach besprechungen](teams-apps-in-meetings.md#post-meeting-app-experience) aktiviert.</span><span class="sxs-lookup"><span data-stu-id="7396c-109">Supporting the `groupchat` scope will enable your app in [pre-meeting](teams-apps-in-meetings.md#pre-meeting-app-experience) and [post-meeting](teams-apps-in-meetings.md#post-meeting-app-experience) chats.</span></span>

* <span data-ttu-id="7396c-110">Besprechungs-API-URL-Parameter erfordern möglicherweise , und die tenantId Diese sind im Rahmen der `meetingId` `userId` Teams Client SDK- und Botaktivität verfügbar. [](/onedrive/find-your-office-365-tenant-id)</span><span class="sxs-lookup"><span data-stu-id="7396c-110">Meeting API URL parameters may require `meetingId`, `userId`, and the [tenantId](/onedrive/find-your-office-365-tenant-id) These are available as part of the Teams Client SDK and bot activity.</span></span> <span data-ttu-id="7396c-111">Darüber hinaus können zuverlässige Informationen zur Benutzer-ID und Mandanten-ID mithilfe der [Tab-SSO-Authentifizierung abgerufen werden.](../tabs/how-to/authentication/auth-aad-sso.md)</span><span class="sxs-lookup"><span data-stu-id="7396c-111">Additionally, reliable information for user ID and tenant ID can be retrieved using [Tab SSO authentication](../tabs/how-to/authentication/auth-aad-sso.md).</span></span>

* <span data-ttu-id="7396c-112">Einige Besprechungs-APIs, z. B. , erfordern eine `GetParticipant` [Botregistrierung und -ID,](../build-your-first-app/build-bot.md) um Authentifizierungstoken zu generieren.</span><span class="sxs-lookup"><span data-stu-id="7396c-112">Some meeting APIs, such as `GetParticipant`, require a [bot registration and ID](../build-your-first-app/build-bot.md) to generate auth tokens.</span></span>

* <span data-ttu-id="7396c-113">Sie müssen die allgemeinen Richtlinien zum [Entwerfen von Teams-Registerkarten für](../tabs/design/tabs.md) Szenarien vor und nach Besprechungen einhalten.</span><span class="sxs-lookup"><span data-stu-id="7396c-113">You must adhere to general [Teams tab design guidelines](../tabs/design/tabs.md) for pre- and post-meeting scenarios.</span></span> <span data-ttu-id="7396c-114">Informationen zu Erfahrungen während Besprechungen finden Sie [in](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-tab) den Entwurfsrichtlinien für Besprechungsdialogfeldern [](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-dialog) und Besprechungsdialogfeldern.</span><span class="sxs-lookup"><span data-stu-id="7396c-114">For experiences during meetings, refer to the [in-meeting tab](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-tab) and [in-meeting dialog](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-dialog) design guidelines.</span></span>

* <span data-ttu-id="7396c-115">Damit Ihre App in Echtzeit aktualisiert werden kann, muss sie basierend auf den Ereignisaktivitäten in der Besprechung auf dem neuesten Stand sein.</span><span class="sxs-lookup"><span data-stu-id="7396c-115">For your app to update in real time, it must be up-to-date based on event activities in the meeting.</span></span> <span data-ttu-id="7396c-116">Diese Ereignisse können sich innerhalb des Besprechungsdialogfelds (siehe Abschlussparameter in ) und andere Oberflächen im `bot Id` `Notification Signal API` gesamten Besprechungslebenszyklus</span><span class="sxs-lookup"><span data-stu-id="7396c-116">These events can be within the in-meeting dialog (refer to completion `bot Id` parameter in `Notification Signal API`) and other surfaces across the meeting lifecycle</span></span>

## <a name="meeting-apps-api-reference"></a><span data-ttu-id="7396c-117">Apireferenz für Besprechungs-Apps</span><span class="sxs-lookup"><span data-stu-id="7396c-117">Meeting apps API reference</span></span>

|<span data-ttu-id="7396c-118">API</span><span class="sxs-lookup"><span data-stu-id="7396c-118">API</span></span>|<span data-ttu-id="7396c-119">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="7396c-119">Description</span></span>|<span data-ttu-id="7396c-120">Anforderung</span><span class="sxs-lookup"><span data-stu-id="7396c-120">Request</span></span>|<span data-ttu-id="7396c-121">Quelle</span><span class="sxs-lookup"><span data-stu-id="7396c-121">Source</span></span>|
|---|---|----|---|
|<span data-ttu-id="7396c-122">**GetUserContext**</span><span class="sxs-lookup"><span data-stu-id="7396c-122">**GetUserContext**</span></span>| <span data-ttu-id="7396c-123">Erhalten Sie Kontextinformationen, um relevante Inhalte auf einer Registerkarte Teams anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="7396c-123">Get contextual information to display relevant content in a Teams tab.</span></span> |<span data-ttu-id="7396c-124">_**microsoftTeams.getContext( ( ) => { /*...\* / } )*\*_</span><span class="sxs-lookup"><span data-stu-id="7396c-124">_**microsoftTeams.getContext( ( ) => {  /*...*/ } )**_</span></span>|<span data-ttu-id="7396c-125">Microsoft Teams client SDK</span><span class="sxs-lookup"><span data-stu-id="7396c-125">Microsoft Teams client SDK</span></span>|
|<span data-ttu-id="7396c-126">**GetParticipant**</span><span class="sxs-lookup"><span data-stu-id="7396c-126">**GetParticipant**</span></span>|<span data-ttu-id="7396c-127">Diese API ermöglicht einem Bot das Abrufen von Teilnehmerinformationen nach Besprechungs-ID und Teilnehmer-ID.</span><span class="sxs-lookup"><span data-stu-id="7396c-127">This API allows a bot to fetch a participant information by meeting id and participant id.</span></span>|<span data-ttu-id="7396c-128">**GET** _**/v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}**_</span><span class="sxs-lookup"><span data-stu-id="7396c-128">**GET** _**/v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}**_</span></span> |<span data-ttu-id="7396c-129">Microsoft Bot Framework SDK</span><span class="sxs-lookup"><span data-stu-id="7396c-129">Microsoft Bot Framework SDK</span></span>|
|<span data-ttu-id="7396c-130">**NotificationSignal**</span><span class="sxs-lookup"><span data-stu-id="7396c-130">**NotificationSignal**</span></span> |<span data-ttu-id="7396c-131">Besprechungssignale werden mithilfe der folgenden vorhandenen Unterhaltungsbenachrichtigungs-API (für Benutzer-Bot-Chat) zugestellt.</span><span class="sxs-lookup"><span data-stu-id="7396c-131">Meeting signals will be delivered using the following existing conversation notification API (for user-bot chat).</span></span> <span data-ttu-id="7396c-132">Mit dieser API können Entwickler basierend auf der Aktion des Endbenutzers signalisieren, dass eine Dialogblase in besprechungsbezogenen Fällen angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="7396c-132">This API allows developers to signal based on end-user action to show-case an in-meeting dialog bubble.</span></span>|<span data-ttu-id="7396c-133">**POST** _**/v3/conversations/{conversationId}/activities**_</span><span class="sxs-lookup"><span data-stu-id="7396c-133">**POST** _**/v3/conversations/{conversationId}/activities**_</span></span>|<span data-ttu-id="7396c-134">Microsoft Bot Framework SDK</span><span class="sxs-lookup"><span data-stu-id="7396c-134">Microsoft Bot Framework SDK</span></span>|

### <a name="getusercontext"></a><span data-ttu-id="7396c-135">GetUserContext</span><span class="sxs-lookup"><span data-stu-id="7396c-135">GetUserContext</span></span>

<span data-ttu-id="7396c-136">Informationen zum [](../tabs/how-to/access-teams-context.md#getting-context-by-using-the-microsoft-teams-javascript-library) Identifizieren und Abrufen von Kontextinformationen für Ihre Registerkarteninhalte finden Sie in der Dokumentation zum Abrufen des Kontexts für Ihre Registerkarteninhalte.</span><span class="sxs-lookup"><span data-stu-id="7396c-136">Please refer to our [Get context for your Teams tab](../tabs/how-to/access-teams-context.md#getting-context-by-using-the-microsoft-teams-javascript-library) documentation for guidance on identifying and  retrieving contextual information for your tab content.</span></span> <span data-ttu-id="7396c-137">Im Rahmen der Erweiterbarkeit von Besprechungen wurde ein neuer Wert für die Antwortnutzlast hinzugefügt:</span><span class="sxs-lookup"><span data-stu-id="7396c-137">As part of meetings extensibility, a new value has been added for the response payload:</span></span>

<span data-ttu-id="7396c-138">✔ **meetingId**: wird von einer Registerkarte verwendet, wenn sie im Besprechungskontext ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="7396c-138">✔ **meetingId**: used by a tab when running in the meeting context.</span></span>

### <a name="getparticipant-api"></a><span data-ttu-id="7396c-139">GetParticipant-API</span><span class="sxs-lookup"><span data-stu-id="7396c-139">GetParticipant API</span></span>

> [!NOTE]
>
> * <span data-ttu-id="7396c-140">Zwischenspeichern Sie keine Teilnehmerrollen, da der Besprechungsorganisator eine Rolle jederzeit ändern kann.</span><span class="sxs-lookup"><span data-stu-id="7396c-140">Do not cache participant roles since the meeting organizer can change a role at any point in time.</span></span>
>
> * <span data-ttu-id="7396c-141">Teams unterstützt derzeit keine großen Verteilerlisten oder Listengrößen von mehr als 350 Teilnehmern für die `GetParticipant` API.</span><span class="sxs-lookup"><span data-stu-id="7396c-141">Teams does not currently support large distribution lists or roster sizes of more than 350 participants for the `GetParticipant` API.</span></span>

#### <a name="query-parameters"></a><span data-ttu-id="7396c-142">Abfrageparameter</span><span class="sxs-lookup"><span data-stu-id="7396c-142">Query parameters</span></span>

|<span data-ttu-id="7396c-143">Wert</span><span class="sxs-lookup"><span data-stu-id="7396c-143">Value</span></span>|<span data-ttu-id="7396c-144">Typ</span><span class="sxs-lookup"><span data-stu-id="7396c-144">Type</span></span>|<span data-ttu-id="7396c-145">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="7396c-145">Required</span></span>|<span data-ttu-id="7396c-146">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="7396c-146">Description</span></span>|
|---|---|----|---|
|<span data-ttu-id="7396c-147">**meetingId**</span><span class="sxs-lookup"><span data-stu-id="7396c-147">**meetingId**</span></span>| <span data-ttu-id="7396c-148">string</span><span class="sxs-lookup"><span data-stu-id="7396c-148">string</span></span> | <span data-ttu-id="7396c-149">Ja</span><span class="sxs-lookup"><span data-stu-id="7396c-149">Yes</span></span> | <span data-ttu-id="7396c-150">Der Besprechungsbezeichner ist über Bot Invoke und Teams Client SDK verfügbar.</span><span class="sxs-lookup"><span data-stu-id="7396c-150">The meeting identifier is available through Bot Invoke and Teams Client SDK.</span></span>|
|<span data-ttu-id="7396c-151">**participantId**</span><span class="sxs-lookup"><span data-stu-id="7396c-151">**participantId**</span></span>| <span data-ttu-id="7396c-152">string</span><span class="sxs-lookup"><span data-stu-id="7396c-152">string</span></span> | <span data-ttu-id="7396c-153">Ja</span><span class="sxs-lookup"><span data-stu-id="7396c-153">Yes</span></span> | <span data-ttu-id="7396c-154">Die participantId ist die Benutzer-ID.</span><span class="sxs-lookup"><span data-stu-id="7396c-154">The participantId is the user ID.</span></span> <span data-ttu-id="7396c-155">Sie ist in Tab SSO, Bot Invoke und Teams Client SDK verfügbar.</span><span class="sxs-lookup"><span data-stu-id="7396c-155">It is available in Tab SSO, Bot Invoke, and Teams Client SDK.</span></span> <span data-ttu-id="7396c-156">Es wird dringend empfohlen, eine participantId aus dem Tab-SSO zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="7396c-156">It is highly recommended to get a participantId from the Tab SSO.</span></span> |
|<span data-ttu-id="7396c-157">**tenantId**</span><span class="sxs-lookup"><span data-stu-id="7396c-157">**tenantId**</span></span>| <span data-ttu-id="7396c-158">string</span><span class="sxs-lookup"><span data-stu-id="7396c-158">string</span></span> | <span data-ttu-id="7396c-159">Ja</span><span class="sxs-lookup"><span data-stu-id="7396c-159">Yes</span></span> | <span data-ttu-id="7396c-160">Die tenantId ist für die Mandantenbenutzer erforderlich.</span><span class="sxs-lookup"><span data-stu-id="7396c-160">The tenantId is required for the tenant users.</span></span> <span data-ttu-id="7396c-161">Sie ist in Tab SSO, Bot Invoke und Teams Client SDK verfügbar.</span><span class="sxs-lookup"><span data-stu-id="7396c-161">It is available in Tab SSO, Bot Invoke, and Teams Client SDK.</span></span> <span data-ttu-id="7396c-162">Es wird dringend empfohlen, eine tenantId aus dem Tab-SSO zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="7396c-162">It is highly recommended to get a tenantId from the Tab SSO.</span></span> |

#### <a name="example"></a><span data-ttu-id="7396c-163">Beispiel</span><span class="sxs-lookup"><span data-stu-id="7396c-163">Example</span></span>

# <a name="cnet"></a>[<span data-ttu-id="7396c-164">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="7396c-164">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
  TeamsMeetingParticipant participant = GetMeetingParticipantAsync(turnContext, "yourMeetingId", "yourParticipantId", "yourTenantId");
  TeamsChannelAccount member = participant.User;
  MeetingParticipantInfo meetingInfo = participant.Meeting;
  ConversationAccount conversation = participant.Conversation;

  await turnContext.SendActivityAsync(MessageFactory.Text($"The participant role is: {meetingInfo.Role}"), cancellationToken);
}

```

# <a name="javascript"></a>[<span data-ttu-id="7396c-165">JavaScript</span><span class="sxs-lookup"><span data-stu-id="7396c-165">JavaScript</span></span>](#tab/javascript)

```typescript

export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onMessage(async (context, next) => {
            TeamsMeetingParticipant participant = GetMeetingParticipantAsync(turnContext, "yourMeetingId", "yourParticipantId", "yourTenantId");
            let member = participant.user;
            let meetingInfo = participant.meeting;
            let conversation = participant.conversation;
            
            await context.sendActivity(`The participant role is: '${meetingInfo.role}'`);
            await next();
        });
    }
}

```

# <a name="json"></a>[<span data-ttu-id="7396c-166">Json</span><span class="sxs-lookup"><span data-stu-id="7396c-166">JSON</span></span>](#tab/json)

```http
GET /v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}
```

<span data-ttu-id="7396c-167">Der Antworttext ist:</span><span class="sxs-lookup"><span data-stu-id="7396c-167">The response body is:</span></span>

```json
{
   "user":{
      "id":"29:1JKiJGPAX9TTxtGxhVo0wLx_zwzo-gG8Z-X03306vBwi9p-xMTEbDXsT6KH7-0kkTS8cD-2zkrsoV6f5WJ6_aYw",
      "aadObjectId":"e236c4bf-88b1-4f3a-b1d7-8891dfc332b5",
      "name":"Bob Young",
      "givenName":"Bob",
      "surname":"Young",
      "email":"Bob.young@microsoft.com",
      "userPrincipalName":"Bob.young@microsoft.com",
      "tenantId":"2fe477ab-0efc-4dfd-bde2-484374e2c373",
      "userRole":"user"
   },
   "meeting":{
      "role ":"Presenter",
      "inMeeting":true
   },
   "conversation":{
      "id":"<conversation id>",
      "isGroup":true
   }
}
```

* * *

#### <a name="response-codes"></a><span data-ttu-id="7396c-168">Antwortcodes</span><span class="sxs-lookup"><span data-stu-id="7396c-168">Response codes</span></span>

* <span data-ttu-id="7396c-169">**403**: Die App darf keine Teilnehmerinformationen erhalten.</span><span class="sxs-lookup"><span data-stu-id="7396c-169">**403**: The app is not allowed to get participant information.</span></span> <span data-ttu-id="7396c-170">Dies ist die häufigste Fehlerantwort und wird ausgelöst, wenn die App nicht in der Besprechung installiert ist.</span><span class="sxs-lookup"><span data-stu-id="7396c-170">This is the most common error response and is triggered if the app is not installed in the meeting.</span></span> <span data-ttu-id="7396c-171">Beispiel: Wenn die App vom Mandantenadministrator deaktiviert oder während der Risikominderung von Livesite blockiert wird.</span><span class="sxs-lookup"><span data-stu-id="7396c-171">For example, if the app is disabled by tenant admin or blocked during livesite mitigation.</span></span>
* <span data-ttu-id="7396c-172">**200**: Teilnehmerinformationen wurden erfolgreich abgerufen.</span><span class="sxs-lookup"><span data-stu-id="7396c-172">**200**: Participant information successfully retrieved.</span></span>
* <span data-ttu-id="7396c-173">**401**: Ungültiges Token.</span><span class="sxs-lookup"><span data-stu-id="7396c-173">**401**: Invalid token.</span></span>
* <span data-ttu-id="7396c-174">**404**: Teilnehmer kann nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="7396c-174">**404**: Participant cannot be found.</span></span>
* <span data-ttu-id="7396c-175">**500**: Die Besprechung ist entweder abgelaufen (mehr als 60 Tage seit dem Ende der Besprechung), oder der Teilnehmer verfügt nicht über Berechtigungen basierend auf seiner Rolle.</span><span class="sxs-lookup"><span data-stu-id="7396c-175">**500**: The meeting has either expired (more than 60 days since the meeting ended) or the participant does not have permissions based on their role.</span></span>


<span data-ttu-id="7396c-176">**Bald verfügbar**</span><span class="sxs-lookup"><span data-stu-id="7396c-176">**Coming Soon**</span></span>

* <span data-ttu-id="7396c-177">**404**: Die Besprechung ist entweder abgelaufen, oder der Teilnehmer kann nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="7396c-177">**404**: The meeting has either expired or participant cannot be found.</span></span>


### <a name="notificationsignal-api"></a><span data-ttu-id="7396c-178">NotificationSignal-API</span><span class="sxs-lookup"><span data-stu-id="7396c-178">NotificationSignal API</span></span>

<span data-ttu-id="7396c-179">Alle Benutzer in einer Besprechung erhalten die Benachrichtigungen, die über die NotificationSignal-API gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="7396c-179">All users in a meeting receive the notifications sent through the NotificationSignal API.</span></span>

> [!NOTE]
> <span data-ttu-id="7396c-180">Derzeit wird das Senden von Zielbenachrichtigungen nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="7396c-180">Currently, sending targetted notifications is not supported.</span></span>
> <span data-ttu-id="7396c-181">Wenn ein Besprechungsdialogfeld aufgerufen wird, wird derselbe Inhalt auch als Chatnachricht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="7396c-181">When an in-meeting dialog is invoked, the same content will also be presented as a chat message.</span></span>

#### <a name="query-parameters"></a><span data-ttu-id="7396c-182">Abfrageparameter</span><span class="sxs-lookup"><span data-stu-id="7396c-182">Query parameters</span></span>

|<span data-ttu-id="7396c-183">Wert</span><span class="sxs-lookup"><span data-stu-id="7396c-183">Value</span></span>|<span data-ttu-id="7396c-184">Typ</span><span class="sxs-lookup"><span data-stu-id="7396c-184">Type</span></span>|<span data-ttu-id="7396c-185">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="7396c-185">Required</span></span>|<span data-ttu-id="7396c-186">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="7396c-186">Description</span></span>|
|---|---|----|---|
|<span data-ttu-id="7396c-187">**conversationId**</span><span class="sxs-lookup"><span data-stu-id="7396c-187">**conversationId**</span></span>| <span data-ttu-id="7396c-188">string</span><span class="sxs-lookup"><span data-stu-id="7396c-188">string</span></span> | <span data-ttu-id="7396c-189">Ja</span><span class="sxs-lookup"><span data-stu-id="7396c-189">Yes</span></span> | <span data-ttu-id="7396c-190">Die Unterhaltungs-ID ist als Teil des Botaufrufs verfügbar.</span><span class="sxs-lookup"><span data-stu-id="7396c-190">The conversation identifier is available as part of bot invoke</span></span> |

#### <a name="example"></a><span data-ttu-id="7396c-191">Beispiel</span><span class="sxs-lookup"><span data-stu-id="7396c-191">Example</span></span>

<span data-ttu-id="7396c-192">Der `Bot ID` wird im Manifest deklariert, und der Bot empfängt ein Ergebnisobjekt.</span><span class="sxs-lookup"><span data-stu-id="7396c-192">The `Bot ID` is declared in the manifest and the bot receives a result object.</span></span> <span data-ttu-id="7396c-193">Im folgenden Beispiel ist der Parameter von optional `completionBotId` `externalResourceUrl` in der angeforderten Nutzlast:</span><span class="sxs-lookup"><span data-stu-id="7396c-193">In the following example, the `completionBotId` parameter of the `externalResourceUrl` is optional in the requested payload:</span></span>

> [!NOTE]
> * <span data-ttu-id="7396c-194">Die `externalResourceUrl` Parameter für Breite und Höhe müssen in Pixel angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="7396c-194">The `externalResourceUrl` width and height parameters must be in pixels.</span></span> <span data-ttu-id="7396c-195">Um sicherzustellen, dass die Abmessungen innerhalb der zulässigen Grenzwerte liegen, finden Sie unter [Entwurfsrichtlinien](design/designing-apps-in-meetings.md).</span><span class="sxs-lookup"><span data-stu-id="7396c-195">To ensure the dimensions are within the allowed limits, see [design guidelines](design/designing-apps-in-meetings.md).</span></span>
> * <span data-ttu-id="7396c-196">Die URL ist die Im Besprechungsdialogfeld `<iframe>` geladene Seite.</span><span class="sxs-lookup"><span data-stu-id="7396c-196">The URL is the page loaded as an `<iframe>` in the in-meeting dialog.</span></span> <span data-ttu-id="7396c-197">Die Domäne muss sich im Array der App `validDomains` im App-Manifest befinden.</span><span class="sxs-lookup"><span data-stu-id="7396c-197">The domain must be in the app's `validDomains` array in your app manifest.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="7396c-198">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="7396c-198">C#/.NET</span></span>](#tab/dotnet)

```csharp
Activity activity = MessageFactory.Text("This is a meeting signal test");

activity.ChannelData = new TeamsChannelData
  {
    Notification = new NotificationInfo()
                    {
                        AlertInMeeting = true,
                        ExternalResourceUrl = "https://teams.microsoft.com/l/bubble/APP_ID?url=<url>&height=<height>&width=<width>&title=<title>&completionBotId=BOT_APP_ID"
                    }
  };
await turnContext.SendActivityAsync(activity).ConfigureAwait(false);
```

# <a name="javascript"></a>[<span data-ttu-id="7396c-199">JavaScript</span><span class="sxs-lookup"><span data-stu-id="7396c-199">JavaScript</span></span>](#tab/javascript)

```javascript

const replyActivity = MessageFactory.text('Hi'); // this could be an adaptive card instead
replyActivity.channelData = {
    notification: {
        alertInMeeting: true,
        externalResourceUrl: 'https://teams.microsoft.com/l/bubble/APP_ID?url=<url>&height=<height>&width=<width>&title=<title>&completionBotId=BOT_APP_ID’
    }
};
await context.sendActivity(replyActivity);
```

# <a name="json"></a>[<span data-ttu-id="7396c-200">Json</span><span class="sxs-lookup"><span data-stu-id="7396c-200">JSON</span></span>](#tab/json)

```http
POST /v3/conversations/{conversationId}/activities

{
    "type": "message",
    "text": "John Phillips assigned you a weekly todo",
    "summary": "Don't forget to meet with Marketing next week",
    "channelData": {
        "notification": {
            "alertInMeeting": true,
            "externalResourceUrl": "https://teams.microsoft.com/l/bubble/APP_ID?url=<url>&height=<height>&width=<width>&title=<title>&completionBotId=BOT_APP_ID"
        }
    },
    "replyToId": "1493070356924"
}
```

* * *

#### <a name="response-codes"></a><span data-ttu-id="7396c-201">Antwortcodes</span><span class="sxs-lookup"><span data-stu-id="7396c-201">Response Codes</span></span>

* <span data-ttu-id="7396c-202">**201**: Aktivität mit Signal wird erfolgreich gesendet.</span><span class="sxs-lookup"><span data-stu-id="7396c-202">**201**: Activity with signal is successfully sent.</span></span> 
* <span data-ttu-id="7396c-203">**401**: Ungültiges Token.</span><span class="sxs-lookup"><span data-stu-id="7396c-203">**401**: Invalid token.</span></span>
* <span data-ttu-id="7396c-204">**403**: Die App kann das Signal nicht senden.</span><span class="sxs-lookup"><span data-stu-id="7396c-204">**403**: The app is unable to send the signal.</span></span> <span data-ttu-id="7396c-205">Dies kann aus verschiedenen Gründen geschehen, z. B. wenn der Mandantenadministrator die App deaktiviert, die App während der Livewebsitemigration blockiert wird und so weiter.</span><span class="sxs-lookup"><span data-stu-id="7396c-205">This can happen due to various reasons such as the tenant admin disables the app, the app is blocked during live site migration, and so on.</span></span> <span data-ttu-id="7396c-206">In diesem Fall enthält die Nutzlast eine detaillierte Fehlermeldung.</span><span class="sxs-lookup"><span data-stu-id="7396c-206">In this case, the payload contains a detailed error message.</span></span> 
* <span data-ttu-id="7396c-207">**404**: Besprechungschat ist nicht vorhanden.</span><span class="sxs-lookup"><span data-stu-id="7396c-207">**404**: Meeting chat does not exist.</span></span>
 

## <a name="enable-your-app-for-teams-meetings"></a><span data-ttu-id="7396c-208">Aktivieren Ihrer App für Teams-Besprechungen</span><span class="sxs-lookup"><span data-stu-id="7396c-208">Enable your app for Teams meetings</span></span>

### <a name="update-your-app-manifest"></a><span data-ttu-id="7396c-209">Aktualisieren Des App-Manifests</span><span class="sxs-lookup"><span data-stu-id="7396c-209">Update your app manifest</span></span>

<span data-ttu-id="7396c-210">Die Funktionen der Besprechungs-App werden in Ihrem App-Manifest über die **konfigurierbarenTabs-Bereiche**  ->  und **Kontextarrays** deklariert.</span><span class="sxs-lookup"><span data-stu-id="7396c-210">The meetings app capabilities are declared in your app manifest through the **configurableTabs** -> **scopes** and **context** arrays.</span></span> <span data-ttu-id="7396c-211">*Scope* definiert, für wen *und welchen Kontext* definiert wird, wo Ihre App verfügbar sein soll.</span><span class="sxs-lookup"><span data-stu-id="7396c-211">*Scope* defines to whom and *context* defines where your app will be available.</span></span>

> [!NOTE]
> <span data-ttu-id="7396c-212">Verwenden Sie [Developer Preview Manifestschema,](../resources/schema/manifest-schema-dev-preview.md) um dies in Ihrem App-Manifest auszuprobieren.</span><span class="sxs-lookup"><span data-stu-id="7396c-212">Please use [Developer Preview manifest schema](../resources/schema/manifest-schema-dev-preview.md) to try this in your app manifest.</span></span>

```json

"configurableTabs": [
    {
      "configurationUrl": "https://contoso.com/teamstab/configure",
      "canUpdateConfiguration": true,
      "scopes": [
        "team",
        "groupchat"
      ],
      "context":[
        "channelTab",
        "privateChatTab",
        "meetingChatTab",
        "meetingDetailsTab",
        "meetingSidePanel"
     ]
    }
  ]
```

### <a name="context-property"></a><span data-ttu-id="7396c-213">Context-Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="7396c-213">Context property</span></span>

<span data-ttu-id="7396c-214">Die Registerkarte und die Eigenschaften funktionieren in Übereinstimmung, damit Sie bestimmen können, wo Ihre `context` App angezeigt werden `scopes` soll.</span><span class="sxs-lookup"><span data-stu-id="7396c-214">The tab `context` and `scopes` properties work in harmony to allow you to determine where you want your app to appear.</span></span> <span data-ttu-id="7396c-215">Registerkarten im `team` Bereich oder können mehrere `groupchat` Kontexte haben.</span><span class="sxs-lookup"><span data-stu-id="7396c-215">Tabs in the `team` or `groupchat` scope can have more than one context.</span></span> <span data-ttu-id="7396c-216">Die möglichen Werte für die Context-Eigenschaft sind wie folgt:</span><span class="sxs-lookup"><span data-stu-id="7396c-216">The possible values for the context property are as follows:</span></span>

* <span data-ttu-id="7396c-217">**channelTab**: eine Registerkarte in der Kopfzeile eines Teamkanals.</span><span class="sxs-lookup"><span data-stu-id="7396c-217">**channelTab**: a tab in the header of a team channel.</span></span>
* <span data-ttu-id="7396c-218">**privateChatTab**: eine Registerkarte in der Kopfzeile eines Gruppenchats zwischen einer Gruppe von Benutzern, die sich nicht im Kontext eines Teams oder einer Besprechung befindet.</span><span class="sxs-lookup"><span data-stu-id="7396c-218">**privateChatTab**: a tab in the header of a group chat between a set of users not in the context of a team or meeting.</span></span>
* <span data-ttu-id="7396c-219">**meetingChatTab**: eine Registerkarte in der Kopfzeile eines Gruppenchats zwischen einer Gruppe von Benutzern im Kontext einer geplanten Besprechung.</span><span class="sxs-lookup"><span data-stu-id="7396c-219">**meetingChatTab**: a tab in the header of a group chat between a set of users in the context of a scheduled meeting.</span></span>
* <span data-ttu-id="7396c-220">**meetingDetailsTab**: eine Registerkarte in der Kopfzeile der Besprechungsdetailsetage des Kalenders.</span><span class="sxs-lookup"><span data-stu-id="7396c-220">**meetingDetailsTab**: a tab in the header of the meeting details view of the calendar.</span></span>
* <span data-ttu-id="7396c-221">**meetingSidePanel**: ein in-Meeting-Panel, das über die einheitliche Leiste (U-Leiste) geöffnet wird.</span><span class="sxs-lookup"><span data-stu-id="7396c-221">**meetingSidePanel**: an in-meeting panel opened via the unified bar (u-bar).</span></span>

> [!NOTE]
> <span data-ttu-id="7396c-222">Die "Context"-Eigenschaft wird derzeit nicht unterstützt und wird daher auf mobilen Clients ignoriert.</span><span class="sxs-lookup"><span data-stu-id="7396c-222">"Context" property is currently not supported and thus will be ignored on mobile clients</span></span>

## <a name="configure-your-app-for-meeting-scenarios"></a><span data-ttu-id="7396c-223">Konfigurieren Ihrer App für Besprechungsszenarien</span><span class="sxs-lookup"><span data-stu-id="7396c-223">Configure your app for meeting scenarios</span></span>

> [!NOTE]
> * <span data-ttu-id="7396c-224">Damit Ihre App im Registerkartenkatalog angezeigt wird, muss sie konfigurierbare **Registerkarten** und den **Gruppenchatbereich unterstützen.**</span><span class="sxs-lookup"><span data-stu-id="7396c-224">For your app to be visible in the tab gallery it needs to **support configurable tabs** and the **group chat scope**.</span></span>
>
> * <span data-ttu-id="7396c-225">Mobile Clients unterstützen Registerkarten nur in Pre- und Post Meeting Surfaces.</span><span class="sxs-lookup"><span data-stu-id="7396c-225">Mobile clients support Tabs only in Pre and Post Meeting Surfaces.</span></span> <span data-ttu-id="7396c-226">Die Besprechungserfahrungen (In-Meeting-Dialog und Registerkarte) auf mobilen Geräten werden in Kürze verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="7396c-226">The in-meeting experiences (in-meeting dialog and tab) on mobile will be available soon.</span></span> <span data-ttu-id="7396c-227">Befolgen Sie [die Anleitungen für Registerkarten auf Mobilgeräten,](../tabs/design/tabs-mobile.md) wenn Sie Ihre Registerkarten für Mobilgeräte erstellen.</span><span class="sxs-lookup"><span data-stu-id="7396c-227">Follow the [guidance for tabs on mobile](../tabs/design/tabs-mobile.md) when creating your tabs for mobile.</span></span>

### <a name="before-a-meeting"></a><span data-ttu-id="7396c-228">Vor einer Besprechung</span><span class="sxs-lookup"><span data-stu-id="7396c-228">Before a meeting</span></span>

<span data-ttu-id="7396c-229">Benutzer mit Organisator- und/oder Organisatorrollen fügen einer Besprechung registerkarten mithilfe  der Schaltfläche plus ➕ auf den Seiten Besprechungschat und **Besprechungsdetails** hinzu.</span><span class="sxs-lookup"><span data-stu-id="7396c-229">Users with organizer and/or presenter roles add tabs to a meeting using the plus ➕ button in the meeting **Chat** and meeting **details** pages.</span></span> <span data-ttu-id="7396c-230">Nachrichtenerweiterungen werden über die Ellipsen-/Überlaufmenüleiste hinzugefügt, &#x25CF;&#x25CF;&#x25CF; sich unterhalb des Verfassennachrichtenbereichs im Chat befindet.</span><span class="sxs-lookup"><span data-stu-id="7396c-230">Messaging extensions are added to via the ellipses/overflow menu &#x25CF;&#x25CF;&#x25CF; located beneath the compose message area in the chat.</span></span> <span data-ttu-id="7396c-231">Bots werden einem Besprechungschat mithilfe der Taste " hinzugefügt und **@** **Bots erhalten ausgewählt.**</span><span class="sxs-lookup"><span data-stu-id="7396c-231">Bots are added to a meeting chat using the "**@**" key and selecting **Get bots**.</span></span>

<span data-ttu-id="7396c-232">✔ Die Benutzeridentität *muss* über [Tabs SSO bestätigt werden.](../tabs/how-to/authentication/auth-aad-sso.md)</span><span class="sxs-lookup"><span data-stu-id="7396c-232">✔ The user identity *must* be confirmed via [Tabs SSO](../tabs/how-to/authentication/auth-aad-sso.md).</span></span> <span data-ttu-id="7396c-233">Nach dieser Authentifizierung kann die App die Benutzerrolle über die GetParticipant-API abrufen.</span><span class="sxs-lookup"><span data-stu-id="7396c-233">Following this authentication, the app can retrieve the user role via the GetParticipant API.</span></span>

 <span data-ttu-id="7396c-234">✔ Basierend auf der Benutzerrolle kann die App nun rollenspezifische Erfahrungen präsentieren.</span><span class="sxs-lookup"><span data-stu-id="7396c-234">✔ Based on the user role, the app will now have the capability to present role specific experiences.</span></span> <span data-ttu-id="7396c-235">Beispielsweise kann eine Abruf-App nur Organisatoren und Organisatoren das Erstellen einer neuen Umfrage ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="7396c-235">For example, a polling app can allow only organizers and presenters to create a new poll.</span></span>

> <span data-ttu-id="7396c-236">**HINWEIS:** Rollenzuweisungen können geändert werden, während eine Besprechung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="7396c-236">**NOTE**: Role assignments can be changed while a meeting is in progress.</span></span>  <span data-ttu-id="7396c-237">*Weitere Informationen* [finden Sie unter Rollen in einer Teams-Besprechung.](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019)</span><span class="sxs-lookup"><span data-stu-id="7396c-237">*See* [Roles in a Teams meeting](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).</span></span> 

### <a name="during-a-meeting"></a><span data-ttu-id="7396c-238">Während einer Besprechung</span><span class="sxs-lookup"><span data-stu-id="7396c-238">During a meeting</span></span>

#### <a name="sidepanel"></a><span data-ttu-id="7396c-239">**sidePanel**</span><span class="sxs-lookup"><span data-stu-id="7396c-239">**sidePanel**</span></span>

<span data-ttu-id="7396c-240">✔ Fügen Sie in Ihrem App-Manifest  dem Kontextarray wie oben beschrieben **sidePanel** hinzu.</span><span class="sxs-lookup"><span data-stu-id="7396c-240">✔ In your app manifest add **sidePanel** to the **context** array as described above.</span></span>

<span data-ttu-id="7396c-241">✔ In der Besprechung und in allen Szenarien wird die App auf einer Registerkarte in der Besprechung gerendert, die eine Breite von 320 px hat.</span><span class="sxs-lookup"><span data-stu-id="7396c-241">✔ In the meeting as well as in all scenarios, the app will be rendered in an in-meeting tab that is 320px in width.</span></span> <span data-ttu-id="7396c-242">Ihre Registerkarte muss dafür optimiert sein.</span><span class="sxs-lookup"><span data-stu-id="7396c-242">Your tab must be optimized for this.</span></span> <span data-ttu-id="7396c-243">*Siehe*, [FrameContext-Schnittstelle](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/framecontext?view=msteams-client-js-latest&preserve-view=true
)</span><span class="sxs-lookup"><span data-stu-id="7396c-243">*See*, [FrameContext interface](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/framecontext?view=msteams-client-js-latest&preserve-view=true
)</span></span>

<span data-ttu-id="7396c-244">✔Refer an das [Teams SDK,](../tabs/how-to/access-teams-context.md#user-context) um die **userContext-API** zu verwenden, um Anforderungen entsprechend weiter zu routen.</span><span class="sxs-lookup"><span data-stu-id="7396c-244">✔Refer to the [Teams SDK](../tabs/how-to/access-teams-context.md#user-context) to use the **userContext** API to route requests accordingly.</span></span>

<span data-ttu-id="7396c-245">✔ Lesen Sie den [Teams-Authentifizierungsfluss für Registerkarten](../tabs/how-to/authentication/auth-flow-tab.md).</span><span class="sxs-lookup"><span data-stu-id="7396c-245">✔ Refer to the [Teams authentication flow for tabs](../tabs/how-to/authentication/auth-flow-tab.md).</span></span> <span data-ttu-id="7396c-246">Der Authentifizierungsfluss für Registerkarten ähnelt dem Authentifizierungsfluss für Websites.</span><span class="sxs-lookup"><span data-stu-id="7396c-246">Authentication flow for tabs is very similar to the auth flow for websites.</span></span> <span data-ttu-id="7396c-247">Daher können Registerkarten OAuth 2.0 direkt verwenden.</span><span class="sxs-lookup"><span data-stu-id="7396c-247">Thus, tabs can use OAuth 2.0 directly.</span></span> <span data-ttu-id="7396c-248">*Siehe auch*, [Microsoft Identity Platform und OAuth 2.0 Authorization Code Flow](/azure/active-directory/develop/v2-oauth2-auth-code-flow).</span><span class="sxs-lookup"><span data-stu-id="7396c-248">*See also*, [Microsoft identity platform and OAuth 2.0 authorization code flow](/azure/active-directory/develop/v2-oauth2-auth-code-flow).</span></span>

<span data-ttu-id="7396c-249">✔ Nachrichtenerweiterung sollte wie erwartet funktionieren, wenn sich ein Benutzer in einer Besprechungsansicht befindet und Nachrichtenerweiterungskarten verfassen können.</span><span class="sxs-lookup"><span data-stu-id="7396c-249">✔ Message extension should work as expected when a user is in an in-meeting view and should be able to post compose message extension cards.</span></span>

<span data-ttu-id="7396c-250">✔ AppName in der Besprechung – QuickInfo sollte den App-Namen in der Besprechungs-U-Leiste enthalten.</span><span class="sxs-lookup"><span data-stu-id="7396c-250">✔ AppName in-meeting - Tooltip should state the app name in-meeting U-bar.</span></span>

#### <a name="in-meeting-dialog"></a><span data-ttu-id="7396c-251">**Dialogfeld "Besprechung"**</span><span class="sxs-lookup"><span data-stu-id="7396c-251">**In-meeting dialog**</span></span>

<span data-ttu-id="7396c-252">✔ Sie müssen die [Entwurfsrichtlinien für Besprechungsdialogfeldern einhalten.](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)</span><span class="sxs-lookup"><span data-stu-id="7396c-252">✔ You must adhere to the [in-meeting dialog design guidelines](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog).</span></span>

<span data-ttu-id="7396c-253">✔ Lesen Sie den [Teams-Authentifizierungsfluss für Registerkarten](../tabs/how-to/authentication/auth-flow-tab.md).</span><span class="sxs-lookup"><span data-stu-id="7396c-253">✔ Refer to the [Teams authentication flow for tabs](../tabs/how-to/authentication/auth-flow-tab.md).</span></span>

<span data-ttu-id="7396c-254">✔ Verwenden Sie die [NotificationSignal-API,](create-apps-for-teams-meetings.md#notificationsignal-api) um zu signalisieren, dass eine Blasenbenachrichtigung ausgelöst werden muss.</span><span class="sxs-lookup"><span data-stu-id="7396c-254">✔ Use the [NotificationSignal API](create-apps-for-teams-meetings.md#notificationsignal-api) to signal that a bubble notification needs to be triggered.</span></span>

<span data-ttu-id="7396c-255">✔ Als Teil der Benachrichtigungsanforderungsnutzlast die URL ein, in der der anzuzeigende Inhalt gehostet wird.</span><span class="sxs-lookup"><span data-stu-id="7396c-255">✔ As part of the notification request payload, include the URL where the content to be showcased is hosted.</span></span>

<span data-ttu-id="7396c-256">✔ In-Meeting-Dialogfeld darf kein Aufgabenmodul verwenden.</span><span class="sxs-lookup"><span data-stu-id="7396c-256">✔ In-meeting dialog must not use task module.</span></span>

> [!NOTE]
>
> * <span data-ttu-id="7396c-257">Diese Benachrichtigungen sind beständig.</span><span class="sxs-lookup"><span data-stu-id="7396c-257">These notifications are persistent in nature.</span></span> <span data-ttu-id="7396c-258">Sie müssen die [**submitTask()-Funktion**](../task-modules-and-cards/task-modules/task-modules-bots.md#submitting-the-result-of-a-task-module) aufrufen, um automatisch zu schließen, nachdem ein Benutzer eine Aktion in der Webansicht ergreift.</span><span class="sxs-lookup"><span data-stu-id="7396c-258">You must invoke the [**submitTask()**](../task-modules-and-cards/task-modules/task-modules-bots.md#submitting-the-result-of-a-task-module) function to auto-dismiss after a user takes an action in the web-view.</span></span> <span data-ttu-id="7396c-259">Dies ist eine Anforderung für die App-Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="7396c-259">This is a requirement for app submission.</span></span> <span data-ttu-id="7396c-260">*Siehe auch*, [Teams SDK: task module](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="7396c-260">*See also*, [Teams SDK: task module](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true).</span></span>
>
> * <span data-ttu-id="7396c-261">Wenn Sie möchten, dass Ihre App anonyme Benutzer unterstützt, muss die Nutzlast der ursprünglichen Aufrufanforderung auf den Anforderungsmetadaten (ID des Benutzers) im Objekt und nicht auf den Anforderungsmetadaten `from.id` `from` `from.aadObjectId` (Azure Active Directory ID des Benutzers) beruhen.</span><span class="sxs-lookup"><span data-stu-id="7396c-261">If you want your app to support anonymous users, your initial invoke request payload must rely on the `from.id`  (ID of the user) request metadata in the `from` object, not the `from.aadObjectId` (Azure Active Directory ID of the user) request metadata.</span></span> <span data-ttu-id="7396c-262">*Weitere* Informationen finden Sie unter Verwenden [von Aufgabenmodulen in Registerkarten](../task-modules-and-cards/task-modules/task-modules-tabs.md) [und Erstellen und Senden des Aufgabenmoduls.](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request)</span><span class="sxs-lookup"><span data-stu-id="7396c-262">*See* [Using task modules in tabs](../task-modules-and-cards/task-modules/task-modules-tabs.md) and [Create and send the task module](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request).</span></span>

### <a name="after-a-meeting"></a><span data-ttu-id="7396c-263">Nach einer Besprechung</span><span class="sxs-lookup"><span data-stu-id="7396c-263">After a meeting</span></span>

<span data-ttu-id="7396c-264">Die Konfigurationen nach der Besprechung und vor der Besprechung sind äquivalent.</span><span class="sxs-lookup"><span data-stu-id="7396c-264">The post-meeting and pre-meeting configurations are equivalent.</span></span>

## <a name="meeting-app-sample"></a><span data-ttu-id="7396c-265">Beispiel für Besprechungs-App</span><span class="sxs-lookup"><span data-stu-id="7396c-265">Meeting app sample</span></span>

 > [!div class="nextstepaction"]
> [<span data-ttu-id="7396c-266">App für den Besprechungstokengenerator</span><span class="sxs-lookup"><span data-stu-id="7396c-266">Meeting token generator app</span></span>](https://github.com/OfficeDev/microsoft-teams-sample-meetings-token)
