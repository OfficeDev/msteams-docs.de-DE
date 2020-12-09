---
title: Apps für Teams-Besprechungen erstellen
author: laujan
description: Erstellen von Apps für Microsoft Teams-Besprechungen
ms.topic: conceptual
ms.author: lajanuar
keywords: Teams-apps-Besprechungen Benutzer Teilnehmer-Rollen-API
ms.openlocfilehash: a086050b7cdef671fcbd187b68d707280e8df359
ms.sourcegitcommit: c102da958759c13aa9e0f81bde1cffb34a8bef34
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "49605231"
---
# <a name="create-apps-for-teams-meetings"></a><span data-ttu-id="bdbfb-104">Apps für Teams-Besprechungen erstellen</span><span class="sxs-lookup"><span data-stu-id="bdbfb-104">Create apps for Teams meetings</span></span>

## <a name="prerequisites-and-considerations"></a><span data-ttu-id="bdbfb-105">Voraussetzungen und Überlegungen</span><span class="sxs-lookup"><span data-stu-id="bdbfb-105">Prerequisites and considerations</span></span>

1. <span data-ttu-id="bdbfb-106">Apps in Besprechungen erfordern grundlegende Kenntnisse der [Teams-App-Entwicklung](../overview.md).</span><span class="sxs-lookup"><span data-stu-id="bdbfb-106">Apps in meetings require some basic knowledge of [Teams app development](../overview.md).</span></span> <span data-ttu-id="bdbfb-107">Eine app in einer Besprechung kann aus [Registerkarten](../tabs/what-are-tabs.md), [Bots](../bots/what-are-bots.md)und [Messaging Erweiterungs](../messaging-extensions/what-are-messaging-extensions.md) Features bestehen und erfordert Aktualisierungen des Teams-APP- [Manifests](#update-your-app-manifest) , um anzugeben, dass die APP für Besprechungen zur Verfügung steht.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-107">An app in a meeting can comprise of [tabs](../tabs/what-are-tabs.md), [bots](../bots/what-are-bots.md), and [messaging extensions](../messaging-extensions/what-are-messaging-extensions.md) features and will require updates to the Teams [app manifest](#update-your-app-manifest) to indicate that the app is available for meetings</span></span>

1. <span data-ttu-id="bdbfb-108">Damit Ihre APP im Besprechungs Lebenszyklus als Registerkarte funktioniert, muss Sie konfigurierbare Registerkarten im [Groupchat-Bereich](../resources/schema/manifest-schema.md#configurabletabs)unterstützen.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-108">For your app to function in the meeting lifecycle as a tab, it must support configurable tabs in the [groupchat scope](../resources/schema/manifest-schema.md#configurabletabs).</span></span> <span data-ttu-id="bdbfb-109">*Weitere Informationen finden Sie unter* [Erweitern Ihrer Teams-App mit einer benutzerdefinierten Registerkarte](../tabs/how-to/add-tab.md). Durch die Unterstützung des `groupchat` Bereichs wird Ihre APP in [Besprechungen vor](teams-apps-in-meetings.md#pre-meeting-app-experience) und [nach](teams-apps-in-meetings.md#post-meeting-app-experience) dem Chatten aktiviert.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-109">*See* [Extend your Teams app with a custom tab](../tabs/how-to/add-tab.md). Supporting the `groupchat` scope will enable your app in [pre-meeting](teams-apps-in-meetings.md#pre-meeting-app-experience) and [post-meeting](teams-apps-in-meetings.md#post-meeting-app-experience) chats.</span></span>

1. <span data-ttu-id="bdbfb-110">Die URL-Parameter der Besprechungs-API erfordern möglicherweise, `meetingId` `userId` und die [Mandanten](/onedrive/find-your-office-365-tenant-id) -Nr sind im Rahmen des Teams-Client-SDK und der Bot-Aktivität verfügbar.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-110">Meeting API URL parameters may require `meetingId`, `userId`, and the [tenantId](/onedrive/find-your-office-365-tenant-id) These are available as part of the Teams Client SDK and bot activity.</span></span> <span data-ttu-id="bdbfb-111">Außerdem können zuverlässige Informationen für Benutzer-ID und Mandanten-ID mithilfe der [Registerkarten-SSO-Authentifizierung](../tabs/how-to/authentication/auth-aad-sso.md)abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-111">Additionally, reliable information for user ID and tenant ID can be retrieved using [Tab SSO authentication](../tabs/how-to/authentication/auth-aad-sso.md).</span></span>

1. <span data-ttu-id="bdbfb-112">Einige Besprechungs-APIs, wie zum Beispiel, `GetParticipant` erfordern eine [bot-Registrierung und eine bot-APP-ID](../bots/how-to/create-a-bot-for-teams.md#with-an-azure-subscription) zum Generieren von auth-Token.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-112">Some meeting APIs, such as `GetParticipant` will require a [bot registration and bot app ID](../bots/how-to/create-a-bot-for-teams.md#with-an-azure-subscription) to generate auth tokens.</span></span>

1. <span data-ttu-id="bdbfb-113">Als Entwickler müssen Sie sich an die allgemeinen [Entwurfsrichtlinien für Teams-Registerkarten](../tabs/design/tabs.md) für vor-und nach Besprechungen sowie an die [in-Meeting-Dialogfeld Richtlinien](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog) für das in-Meeting-Dialogfeld halten, das während einer Teams-Besprechung ausgelöst wurde.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-113">As a developer, you must adhere to general [Teams tab design guidelines](../tabs/design/tabs.md) for pre- and post-meeting scenarios as well as the [in-meeting dialog guidelines](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog) for in-meeting dialog triggered during a Teams meeting.</span></span>

1. <span data-ttu-id="bdbfb-114">Beachten Sie, dass die app in der Regel auf dem neuesten Stand sein muss, damit Ihre APP in Echtzeit aktualisiert werden kann, wenn Sie auf den Ereignis Aktivitäten in der Besprechung basiert.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-114">Please note that in order for your app to be updated in real-time, it must be up-to-date based on event activities in the meeting.</span></span> <span data-ttu-id="bdbfb-115">Diese Ereignisse können sich innerhalb des in-Meeting-Dialogs befinden (siehe completion- `bot Id` Parameter in `Notification Signal API` ) und andere Oberflächen im gesamten Besprechungs Lebenszyklus.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-115">These events can be within the in-meeting dialog (refer to completion `bot Id` parameter in `Notification Signal API`) and other surfaces across the meeting lifecycle</span></span>

## <a name="meeting-apps-api-reference"></a><span data-ttu-id="bdbfb-116">Besprechungs-apps-API-Referenz</span><span class="sxs-lookup"><span data-stu-id="bdbfb-116">Meeting apps API reference</span></span>

|<span data-ttu-id="bdbfb-117">API</span><span class="sxs-lookup"><span data-stu-id="bdbfb-117">API</span></span>|<span data-ttu-id="bdbfb-118">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bdbfb-118">Description</span></span>|<span data-ttu-id="bdbfb-119">Anforderung</span><span class="sxs-lookup"><span data-stu-id="bdbfb-119">Request</span></span>|<span data-ttu-id="bdbfb-120">Source</span><span class="sxs-lookup"><span data-stu-id="bdbfb-120">Source</span></span>|
|---|---|----|---|
|<span data-ttu-id="bdbfb-121">**Getusercontext**</span><span class="sxs-lookup"><span data-stu-id="bdbfb-121">**GetUserContext**</span></span>| <span data-ttu-id="bdbfb-122">Abrufen von Kontextinformationen zum Anzeigen relevanter Inhalte auf einer Registerkarte Teams.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-122">Get contextual information to display relevant content in a Teams tab.</span></span> |<span data-ttu-id="bdbfb-123">_**verläuft. GetContext (() => {/*...\* / } )*\*_</span><span class="sxs-lookup"><span data-stu-id="bdbfb-123">_**microsoftTeams.getContext( ( ) => {  /*...*/ } )**_</span></span>|<span data-ttu-id="bdbfb-124">Microsoft Teams-Client-SDK</span><span class="sxs-lookup"><span data-stu-id="bdbfb-124">Microsoft Teams client SDK</span></span>|
|<span data-ttu-id="bdbfb-125">**Getparticipant**</span><span class="sxs-lookup"><span data-stu-id="bdbfb-125">**GetParticipant**</span></span>|<span data-ttu-id="bdbfb-126">Mit dieser API kann ein bot eine Teilnehmer Information nach Besprechungs-ID und Teilnehmer-ID abrufen.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-126">This API allows a bot to fetch a participant information by meeting id and participant id.</span></span>|<span data-ttu-id="bdbfb-127">**GET** _**/V1/Meetings/{meetingId}/participants/{participantId} abrufen? Mandanten-Nr = {Mandanten** -Nr}_</span><span class="sxs-lookup"><span data-stu-id="bdbfb-127">**GET** _**/v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}**_</span></span> |<span data-ttu-id="bdbfb-128">Microsoft bot Framework SDK</span><span class="sxs-lookup"><span data-stu-id="bdbfb-128">Microsoft Bot Framework SDK</span></span>|
|<span data-ttu-id="bdbfb-129">**NotificationSignal**</span><span class="sxs-lookup"><span data-stu-id="bdbfb-129">**NotificationSignal**</span></span> |<span data-ttu-id="bdbfb-130">Besprechungs Signale werden über die folgende vorhandene Benachrichtigungs-API für Unterhaltungen (für Benutzer-bot-Chat) übermittelt.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-130">Meeting signals will be delivered using the following existing conversation notification API (for user-bot chat).</span></span> <span data-ttu-id="bdbfb-131">Mit dieser API können Entwickler basierend auf der Endbenutzer Aktion signalisieren, dass eine Dialog Blase in einer Besprechung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-131">This API allows developers to signal based on end-user action to show-case an in-meeting dialog bubble.</span></span>|<span data-ttu-id="bdbfb-132">**Post** _**/V3/Conversations/{conversationId}/Activities**_</span><span class="sxs-lookup"><span data-stu-id="bdbfb-132">**POST** _**/v3/conversations/{conversationId}/activities**_</span></span>|<span data-ttu-id="bdbfb-133">Microsoft bot Framework SDK</span><span class="sxs-lookup"><span data-stu-id="bdbfb-133">Microsoft Bot Framework SDK</span></span>|

### <a name="getusercontext"></a><span data-ttu-id="bdbfb-134">Getusercontext</span><span class="sxs-lookup"><span data-stu-id="bdbfb-134">GetUserContext</span></span>

<span data-ttu-id="bdbfb-135">Eine Anleitung zum Identifizieren und Abrufen von Kontextinformationen für die Registerkarteninhalte finden Sie in der Dokumentation zu [Get Context for your Teams](../tabs/how-to/access-teams-context.md#getting-context-by-using-the-microsoft-teams-javascript-library) .</span><span class="sxs-lookup"><span data-stu-id="bdbfb-135">Please refer to our [Get context for your Teams tab](../tabs/how-to/access-teams-context.md#getting-context-by-using-the-microsoft-teams-javascript-library) documentation for guidance on identifying and  retrieving contextual information for your tab content.</span></span> <span data-ttu-id="bdbfb-136">Im Rahmen der Erweiterbarkeit von Besprechungen wurde für die Antwort Nutzlast ein neuer Wert hinzugefügt:</span><span class="sxs-lookup"><span data-stu-id="bdbfb-136">As part of meetings extensibility, a new value has been added for the response payload:</span></span>

<span data-ttu-id="bdbfb-137">✔- **Besprechungs**-Nr: wird von einer Registerkarte bei der Ausführung im Besprechungs Kontext verwendet.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-137">✔ **meetingId**: used by a tab when running in the meeting context.</span></span>

### <a name="getparticipant-api"></a><span data-ttu-id="bdbfb-138">Getparticipant-API</span><span class="sxs-lookup"><span data-stu-id="bdbfb-138">GetParticipant API</span></span>

> [!NOTE]
>
> * <span data-ttu-id="bdbfb-139">Sie sollten keine Teilnehmerrollen Zwischenspeichern, da der Besprechungsorganisator zu einem beliebigen Zeitpunkt eine Rolle ändern kann.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-139">Do not cache participant roles since the meeting organizer can change a role at any point in time.</span></span>
>
> * <span data-ttu-id="bdbfb-140">Microsoft Teams unterstützt derzeit keine großen Verteilerlisten oder Dienstplan Größen von mehr als 350 Teilnehmern für die `GetParticipant` API.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-140">Teams does not currently support large distribution lists or roster sizes of more than 350 participants for the `GetParticipant` API.</span></span>
>
> * <span data-ttu-id="bdbfb-141">Die Unterstützung für das bot Framework SDK wird in Kürze verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-141">Support for the Bot Framework SDK is coming soon.</span></span>


#### <a name="request"></a><span data-ttu-id="bdbfb-142">Anforderung</span><span class="sxs-lookup"><span data-stu-id="bdbfb-142">Request</span></span>

```http
GET /v3/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}
```

<span data-ttu-id="bdbfb-143">*Siehe* [bot Framework-API-Referenz](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="bdbfb-143">*See* the [Bot Framework API reference](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0&preserve-view=true).</span></span>

<!-- markdownlint-disable MD025 -->

<span data-ttu-id="bdbfb-144">**C#-Beispiel**</span><span class="sxs-lookup"><span data-stu-id="bdbfb-144">**C# example**</span></span>

```csharp
   // Get role for the user who sent a message to your bot
   var senderRole = await TeamsInfo.GetMeetingParticipantAsync(turnContext);
```

* * *
<!-- markdownlint-disable MD001 -->

#### <a name="query-parameters"></a><span data-ttu-id="bdbfb-145">Abfrageparameter</span><span class="sxs-lookup"><span data-stu-id="bdbfb-145">Query parameters</span></span>

|<span data-ttu-id="bdbfb-146">Wert</span><span class="sxs-lookup"><span data-stu-id="bdbfb-146">Value</span></span>|<span data-ttu-id="bdbfb-147">Typ</span><span class="sxs-lookup"><span data-stu-id="bdbfb-147">Type</span></span>|<span data-ttu-id="bdbfb-148">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="bdbfb-148">Required</span></span>|<span data-ttu-id="bdbfb-149">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bdbfb-149">Description</span></span>|
|---|---|----|---|
|<span data-ttu-id="bdbfb-150">**meetingId**</span><span class="sxs-lookup"><span data-stu-id="bdbfb-150">**meetingId**</span></span>| <span data-ttu-id="bdbfb-151">string</span><span class="sxs-lookup"><span data-stu-id="bdbfb-151">string</span></span> | <span data-ttu-id="bdbfb-152">Ja</span><span class="sxs-lookup"><span data-stu-id="bdbfb-152">Yes</span></span> | <span data-ttu-id="bdbfb-153">Die Besprechungs-ID ist über bot Invoke und Microsoft Teams Client SDK verfügbar.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-153">The meeting identifier is available via Bot Invoke and Teams Client SDK.</span></span>|
|<span data-ttu-id="bdbfb-154">**Teilnehmer-Nr**</span><span class="sxs-lookup"><span data-stu-id="bdbfb-154">**participantId**</span></span>| <span data-ttu-id="bdbfb-155">string</span><span class="sxs-lookup"><span data-stu-id="bdbfb-155">string</span></span> | <span data-ttu-id="bdbfb-156">Ja</span><span class="sxs-lookup"><span data-stu-id="bdbfb-156">Yes</span></span> | <span data-ttu-id="bdbfb-157">Dieses Feld ist die Benutzer-ID und steht in der Registerkarte "SSO", im bot-Invoke und im Microsoft Teams-Client-SDK zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-157">This field is the User ID and it is available in Tab SSO, Bot Invoke, and Teams Client SDK.</span></span> <span data-ttu-id="bdbfb-158">Die Registerkarte SSO wird dringend empfohlen.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-158">Tab SSO is highly recommended</span></span>|
|<span data-ttu-id="bdbfb-159">**tenantId**</span><span class="sxs-lookup"><span data-stu-id="bdbfb-159">**tenantId**</span></span>| <span data-ttu-id="bdbfb-160">string</span><span class="sxs-lookup"><span data-stu-id="bdbfb-160">string</span></span> | <span data-ttu-id="bdbfb-161">Ja</span><span class="sxs-lookup"><span data-stu-id="bdbfb-161">Yes</span></span> | <span data-ttu-id="bdbfb-162">Dies ist für Mandanten Benutzer erforderlich.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-162">This required for tenant users.</span></span> <span data-ttu-id="bdbfb-163">Sie ist in Tab SSO, bot Invoke und Microsoft Teams Client SDK verfügbar.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-163">It is available in Tab SSO, Bot Invoke, and Teams Client SDK.</span></span> <span data-ttu-id="bdbfb-164">Die Registerkarte SSO wird dringend empfohlen.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-164">Tab SSO is highly recommended</span></span>|

#### <a name="response-payload"></a><span data-ttu-id="bdbfb-165">Antwort Nutzlast</span><span class="sxs-lookup"><span data-stu-id="bdbfb-165">Response Payload</span></span>
<!-- markdownlint-disable MD036 -->

<span data-ttu-id="bdbfb-166">**Rolle** unter "Besprechung" kann *Organisator*, *Referent* oder *Teilnehmer* sein.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-166">**role** under "meeting" can be *Organizer*, *Presenter*, or *Attendee*.</span></span>

<span data-ttu-id="bdbfb-167">**Beispiel 1**</span><span class="sxs-lookup"><span data-stu-id="bdbfb-167">**Example 1**</span></span>

```json
{
   "user":{
      "id":"29:1JKiJGPAX9TTxtGxhVo0wLx_zwzo-gG8Z-X03306vBwi9p-xMTEbDXsT6KH7-0kkTS8cD-2zkrsoV6f5WJ6_aYw",
      "aadObjectId":"6aebbad0-e5a5-424a-834a-20fb051f3c1a",
      "name":"Allan Deyoung",
      "givenName":"Allan",
      "surname":"Deyoung",
      "email":"Allan.Deyoung@microsoft.com",
      "userPrincipalName":"Allan.Deyoung@microsoft.com",
      "tenantId":"72f988bf-86f1-41af-91ab-2d7cd011db47",
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

#### <a name="response-codes"></a><span data-ttu-id="bdbfb-168">Antwortcodes</span><span class="sxs-lookup"><span data-stu-id="bdbfb-168">Response codes</span></span>

<span data-ttu-id="bdbfb-169">**403**: die APP darf keine Teilnehmer Informationen erhalten.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-169">**403**: The app is not allowed to get participant information.</span></span> <span data-ttu-id="bdbfb-170">Dies ist die häufigste Fehlerantwort und wird ausgelöst, wenn die APP nicht in der Besprechung installiert ist, beispielsweise wenn Sie vom mandantenadministrator deaktiviert oder während einer Live-Websitemigration blockiert wird.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-170">This will be the most common error response and is triggered when the app is not installed in the meeting such as when it is disabled by tenant admin or blocked during live site migration.</span></span>  
<span data-ttu-id="bdbfb-171">**200**: Teilnehmer Informationen erfolgreich abgerufen.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-171">**200**: Participant information successfully retrieved.</span></span>  
<span data-ttu-id="bdbfb-172">**401**: Ungültiges Token.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-172">**401**: Invalid token.</span></span>  
<span data-ttu-id="bdbfb-173">**404**: Teilnehmer kann nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-173">**404**: Participant cannot be found.</span></span> 
<span data-ttu-id="bdbfb-174">**500**: die Besprechung ist entweder abgelaufen (mehr als 60 Tage seit der Beendigung der Besprechung) oder der Teilnehmer verfügt nicht über die Berechtigungen basierend auf seiner Rolle.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-174">**500**: The meeting is either expired (more than 60 days since the meeting ended) or the participant does not have permissions based on their role.</span></span>

<span data-ttu-id="bdbfb-175">**Bald verfügbar**</span><span class="sxs-lookup"><span data-stu-id="bdbfb-175">**Coming Soon**</span></span>

<span data-ttu-id="bdbfb-176">**404**: die Besprechung ist entweder abgelaufen oder der Teilnehmer kann nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-176">**404**: the meeting has either expired or participant cannot be found.</span></span> 

<!-- markdownlint-disable MD024 -->
### <a name="notificationsignal-api"></a><span data-ttu-id="bdbfb-177">NotificationSignal-API</span><span class="sxs-lookup"><span data-stu-id="bdbfb-177">NotificationSignal API</span></span>

> [!NOTE]
> <span data-ttu-id="bdbfb-178">Wenn ein in-Meeting-Dialogfeld aufgerufen wird, wird derselbe Inhalt auch als Chatnachricht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-178">When an in-meeting dialog is invoked, the same content will also be presented as a chat message.</span></span>

#### <a name="request"></a><span data-ttu-id="bdbfb-179">Anforderung</span><span class="sxs-lookup"><span data-stu-id="bdbfb-179">Request</span></span>

```http
POST /v3/conversations/{conversationId}/activities
```

#### <a name="query-parameters"></a><span data-ttu-id="bdbfb-180">Abfrageparameter</span><span class="sxs-lookup"><span data-stu-id="bdbfb-180">Query parameters</span></span>

|<span data-ttu-id="bdbfb-181">Wert</span><span class="sxs-lookup"><span data-stu-id="bdbfb-181">Value</span></span>|<span data-ttu-id="bdbfb-182">Typ</span><span class="sxs-lookup"><span data-stu-id="bdbfb-182">Type</span></span>|<span data-ttu-id="bdbfb-183">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="bdbfb-183">Required</span></span>|<span data-ttu-id="bdbfb-184">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bdbfb-184">Description</span></span>|
|---|---|----|---|
|<span data-ttu-id="bdbfb-185">**conversationId**</span><span class="sxs-lookup"><span data-stu-id="bdbfb-185">**conversationId**</span></span>| <span data-ttu-id="bdbfb-186">string</span><span class="sxs-lookup"><span data-stu-id="bdbfb-186">string</span></span> | <span data-ttu-id="bdbfb-187">Ja</span><span class="sxs-lookup"><span data-stu-id="bdbfb-187">Yes</span></span> | <span data-ttu-id="bdbfb-188">Die Konversations-ID ist im Rahmen von bot Invoke verfügbar</span><span class="sxs-lookup"><span data-stu-id="bdbfb-188">The conversation identifier is available as part of bot invoke</span></span> |

#### <a name="request-payload"></a><span data-ttu-id="bdbfb-189">Anforderungsnutzlast</span><span class="sxs-lookup"><span data-stu-id="bdbfb-189">Request payload</span></span>

> [!NOTE]
>
> *  <span data-ttu-id="bdbfb-190">In der angeforderten Nutzlast unten `completionBotId` ist der Parameter des-Parameters `externalResourceUrl` ein optional.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-190">In the requested payload below, the `completionBotId` parameter of the `externalResourceUrl`is an optional.</span></span> <span data-ttu-id="bdbfb-191">Es ist das `Bot ID` , das im Manifest deklariert wird.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-191">It is the `Bot ID` that is declared in the manifest.</span></span> <span data-ttu-id="bdbfb-192">Der bot erhält ein Result-Objekt.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-192">The bot will receive a result object.</span></span>
> * <span data-ttu-id="bdbfb-193">Die externalResourceUrl-Parameter width und Height müssen in Pixel angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-193">The externalResourceUrl width and height parameters must be in pixels.</span></span> <span data-ttu-id="bdbfb-194">Lesen Sie die [Entwurfsrichtlinien](design/designing-apps-in-meetings.md) , um sicherzustellen, dass sich die Dimensionen innerhalb der zulässigen Grenzen befinden.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-194">Refer to the [design guidelines](design/designing-apps-in-meetings.md) to ensure the dimensions are within the allowed limits.</span></span>
> * <span data-ttu-id="bdbfb-195">Die URL ist die Seite, die als `<iframe>` innerhalb des in-Meeting-Dialogs geladen wird.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-195">The URL is the page loaded as an `<iframe>` inside the in-meeting dialog.</span></span> <span data-ttu-id="bdbfb-196">Die Domäne der URL muss sich in Ihrem App-Manifest im APP- `validDomains` Array befinden.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-196">The URL's domain must be in the app's `validDomains` array in your app manifest.</span></span>


# <a name="json"></a>[<span data-ttu-id="bdbfb-197">Json</span><span class="sxs-lookup"><span data-stu-id="bdbfb-197">JSON</span></span>](#tab/json)

```json
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

# <a name="cnet"></a>[<span data-ttu-id="bdbfb-198">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="bdbfb-198">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="javascript"></a>[<span data-ttu-id="bdbfb-199">JavaScript</span><span class="sxs-lookup"><span data-stu-id="bdbfb-199">JavaScript</span></span>](#tab/javascript)

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

* * *

> [!IMPORTANT]
> <span data-ttu-id="bdbfb-200">Die URL in der Inhalts Blase (taskInfo-URL) muss in der Liste [gültiger Domänen](../resources/schema/manifest-schema.md#validdomains) enthalten sein, die im App-Manifest für Teams enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-200">The URL in the content bubble (taskInfo URL) must be included in the [valid domains](../resources/schema/manifest-schema.md#validdomains) list included in the Teams app manifest.</span></span>

#### <a name="response-codes"></a><span data-ttu-id="bdbfb-201">Antwort Codes</span><span class="sxs-lookup"><span data-stu-id="bdbfb-201">Response Codes</span></span>

<span data-ttu-id="bdbfb-202">**201**: Aktivität mit Signal wurde erfolgreich gesendet</span><span class="sxs-lookup"><span data-stu-id="bdbfb-202">**201**: activity with signal is successfully sent</span></span>  
<span data-ttu-id="bdbfb-203">**401**: Ungültiges Token</span><span class="sxs-lookup"><span data-stu-id="bdbfb-203">**401**: invalid token</span></span>  
<span data-ttu-id="bdbfb-204">**403**: die APP darf das Signal nicht senden.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-204">**403**: the app is not allowed to send the signal.</span></span> <span data-ttu-id="bdbfb-205">In diesem Fall sollte die Nutzlast eine ausführlichere Fehlermeldung enthalten.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-205">In this case, the payload should contain more detail error message.</span></span> <span data-ttu-id="bdbfb-206">Es kann viele Gründe geben: app, die vom mandantenadministrator deaktiviert, während einer Live-Standort Minderung blockiert wird, usw.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-206">There can be many reasons: app disabled by tenant admin, blocked during live site mitigation, etc.</span></span>  
<span data-ttu-id="bdbfb-207">**404**: Besprechungs Chat nicht vorhanden</span><span class="sxs-lookup"><span data-stu-id="bdbfb-207">**404**: meeting chat doesn't exist</span></span>  

## <a name="enable-your-app-for-teams-meetings"></a><span data-ttu-id="bdbfb-208">Aktivieren Ihrer APP für Microsoft Teams-Besprechungen</span><span class="sxs-lookup"><span data-stu-id="bdbfb-208">Enable your app for Teams meetings</span></span>

### <a name="update-your-app-manifest"></a><span data-ttu-id="bdbfb-209">Aktualisieren des App-Manifests</span><span class="sxs-lookup"><span data-stu-id="bdbfb-209">Update your app manifest</span></span>

<span data-ttu-id="bdbfb-210">Die APP-Funktionen für Besprechungen werden in Ihrem App-Manifest über die **configurableTabs**  ->  -**Bereiche** und **Kontext** Arrays deklariert.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-210">The meetings app capabilities are declared in your app manifest via the **configurableTabs** -> **scopes** and **context** arrays.</span></span> <span data-ttu-id="bdbfb-211">*Scope* definiert, an wen und in welchem *Kontext* definiert wird, wo Ihre app verfügbar sein wird.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-211">*Scope* defines to whom and *context* defines where your app will be available.</span></span>

> [!NOTE]
> * <span data-ttu-id="bdbfb-212">Verwenden Sie das [Manifest-Schema für Entwicklervorschau](../resources/schema/manifest-schema-dev-preview.md) , um dieses in Ihrem App-Manifest zu testen.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-212">Please use [Developer Preview manifest schema](../resources/schema/manifest-schema-dev-preview.md) to try this in your app manifest.</span></span>

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

### <a name="context-property"></a><span data-ttu-id="bdbfb-213">Context-Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="bdbfb-213">Context property</span></span>

<span data-ttu-id="bdbfb-214">Die Registerkarte `context` und die `scopes` Eigenschaften funktionieren in Harmonie, damit Sie bestimmen können, wo Ihre APP angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-214">The tab `context` and `scopes` properties work in harmony to allow you to determine where you want your app to appear.</span></span> <span data-ttu-id="bdbfb-215">Registerkarten im `team` `groupchat` Bereich oder können mehr als einen Kontext aufweisen.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-215">Tabs in the `team` or `groupchat` scope can have more than one context.</span></span> <span data-ttu-id="bdbfb-216">Die möglichen Werte für die Context-Eigenschaft lauten wie folgt:</span><span class="sxs-lookup"><span data-stu-id="bdbfb-216">The possible values for the context property are as follows:</span></span>

* <span data-ttu-id="bdbfb-217">**channelTab**: eine Registerkarte in der Kopfzeile eines Team Kanals.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-217">**channelTab**: a tab in the header of a team channel.</span></span>
* <span data-ttu-id="bdbfb-218">**privateChatTab**: eine Registerkarte in der Kopfzeile eines Gruppenchats zwischen einer Gruppe von Benutzern, die sich nicht im Kontext eines Teams oder einer Besprechung befinden.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-218">**privateChatTab**: a tab in the header of a group chat between a set of users not in the context of a team or meeting.</span></span>
* <span data-ttu-id="bdbfb-219">**meetingChatTab**: eine Registerkarte in der Kopfzeile eines Gruppenchats zwischen einer Gruppe von Benutzern im Kontext einer geplanten Besprechung.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-219">**meetingChatTab**: a tab in the header of a group chat between a set of users in the context of a scheduled meeting.</span></span>
* <span data-ttu-id="bdbfb-220">**meetingDetailsTab**: eine Registerkarte in der Kopfzeile der Ansicht "Besprechungsdetails" des Kalenders.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-220">**meetingDetailsTab**: a tab in the header of the meeting details view of the calendar.</span></span>
* <span data-ttu-id="bdbfb-221">**meetingSidePanel**: ein in-Meeting-Bereich, der über den einheitlichen Balken geöffnet wird (u-Leiste).</span><span class="sxs-lookup"><span data-stu-id="bdbfb-221">**meetingSidePanel**: an in-meeting panel opened via the unified bar (u-bar).</span></span>

> [!NOTE]
> <span data-ttu-id="bdbfb-222">Die Eigenschaft "Context" wird derzeit nicht unterstützt und wird daher auf mobilen Clients ignoriert.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-222">"Context" property is currently not supported and thus will be ignored on mobile clients</span></span>

## <a name="configure-your-app-for-meeting-scenarios"></a><span data-ttu-id="bdbfb-223">Konfigurieren Ihrer APP für Besprechungs Szenarien</span><span class="sxs-lookup"><span data-stu-id="bdbfb-223">Configure your app for meeting scenarios</span></span>

> [!NOTE]
> * <span data-ttu-id="bdbfb-224">Damit Ihre APP im Registerkarten Katalog sichtbar ist, muss Sie **konfigurierbare Registerkarten** und den **Gruppenchat Bereich** unterstützen.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-224">For your app to be visible in the tab gallery it needs to **support configurable tabs** and the **group chat scope**.</span></span>
>
> * <span data-ttu-id="bdbfb-225">Mobile Clients unterstützen Registerkarten nur in Pre-und Post-Besprechungs Oberflächen.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-225">Mobile clients support Tabs only in Pre and Post Meeting Surfaces.</span></span> <span data-ttu-id="bdbfb-226">Die in-Meeting-Erlebnisse (in-Meeting-Dialog und Tab) auf mobilen Geräten werden in Kürze verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-226">The in-meeting experiences (in-meeting dialog and tab) on mobile will be available soon.</span></span> <span data-ttu-id="bdbfb-227">Befolgten Sie die [Anleitungen für Registerkarten auf mobilen Geräten](../tabs/design/tabs-mobile.md) beim Erstellen Ihrer Registerkarten für mobile Geräte.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-227">Follow the [guidance for tabs on mobile](../tabs/design/tabs-mobile.md) when creating your tabs for mobile.</span></span>

### <a name="before-a-meeting"></a><span data-ttu-id="bdbfb-228">Vor einer Besprechung</span><span class="sxs-lookup"><span data-stu-id="bdbfb-228">Before a meeting</span></span>

<span data-ttu-id="bdbfb-229">Benutzer mit Organizer-und/oder Presenter-Rollen fügen mithilfe der Schaltfläche Plus ➕ auf der Seite Besprechungs- **Chat** und Besprechungs **Details** Registerkarten zu einer Besprechung hinzu.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-229">Users with organizer and/or presenter roles add tabs to a meeting using the plus ➕ button in the meeting **Chat** and meeting **details** pages.</span></span> <span data-ttu-id="bdbfb-230">Messaging Erweiterungen werden über das Menü Ellipsen/Überlauf hinzugefügt, &#x25CF;&#x25CF;&#x25CF; unterhalb des Bereichs zum Verfassen von Nachrichten im Chat angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-230">Messaging extensions are added to via the ellipses/overflow menu &#x25CF;&#x25CF;&#x25CF; located beneath the compose message area in the chat.</span></span> <span data-ttu-id="bdbfb-231">Bots werden mit der Taste "" zu einem Besprechungs Chat hinzugefügt **@** und die Option **Bots abrufen** ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-231">Bots are added to a meeting chat using the "**@**" key and selecting **Get bots**.</span></span>

<span data-ttu-id="bdbfb-232">✔ Die Benutzeridentität *muss* über die [Registerkarten SSO](../tabs/how-to/authentication/auth-aad-sso.md)bestätigt werden.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-232">✔ The user identity *must* be confirmed via [Tabs SSO](../tabs/how-to/authentication/auth-aad-sso.md).</span></span> <span data-ttu-id="bdbfb-233">Nach dieser Authentifizierung kann die APP die Benutzerrolle über die getteilnehmer-API abrufen.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-233">Following this authentication, the app can retrieve the user role via the GetParticipant API.</span></span>

 <span data-ttu-id="bdbfb-234">✔ Basierend auf der Benutzerrolle kann die App nun rollenspezifische Erlebnisse vorlegen.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-234">✔ Based on the user role, the app will now have the capability to present role specific experiences.</span></span> <span data-ttu-id="bdbfb-235">Beispielsweise kann eine Polling-app nur Organisatoren und Referenten das Erstellen einer neuen Umfrage gestatten.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-235">For example, a polling app can allow only organizers and presenters to create a new poll.</span></span>

> <span data-ttu-id="bdbfb-236">**Hinweis**: Rollenzuweisungen können geändert werden, während eine Besprechung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-236">**NOTE**: Role assignments can be changed while a meeting is in progress.</span></span>  <span data-ttu-id="bdbfb-237">*Siehe* [roles in a Teams Meeting](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).</span><span class="sxs-lookup"><span data-stu-id="bdbfb-237">*See* [Roles in a Teams meeting](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).</span></span> 

### <a name="during-a-meeting"></a><span data-ttu-id="bdbfb-238">Während einer Besprechung</span><span class="sxs-lookup"><span data-stu-id="bdbfb-238">During a meeting</span></span>

#### <a name="sidepanel"></a><span data-ttu-id="bdbfb-239">**sidePanel**</span><span class="sxs-lookup"><span data-stu-id="bdbfb-239">**sidePanel**</span></span>

<span data-ttu-id="bdbfb-240">✔ In Ihrem App-Manifest fügen Sie **sidePanel** dem **Kontext** Array hinzu, wie oben beschrieben.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-240">✔ In your app manifest add **sidePanel** to the **context** array as described above.</span></span>

<span data-ttu-id="bdbfb-241">✔ In der Besprechung als auch in allen Szenarien wird die app in einer in-Meeting-Registerkarte gerendert, die 320 Pixel groß in der Breite ist.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-241">✔ In the meeting as well as in all scenarios, the app will be rendered in an in-meeting tab that is 320px in width.</span></span> <span data-ttu-id="bdbfb-242">Die Registerkarte muss dafür optimiert werden.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-242">Your tab must be optimized for this.</span></span> <span data-ttu-id="bdbfb-243">*Siehe*, [framecontext-Schnittstelle](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/framecontext?view=msteams-client-js-latest&preserve-view=true
)</span><span class="sxs-lookup"><span data-stu-id="bdbfb-243">*See*, [FrameContext interface](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/framecontext?view=msteams-client-js-latest&preserve-view=true
)</span></span>

<span data-ttu-id="bdbfb-244">✔ Sie im Microsoft [Teams-SDK](../tabs/how-to/access-teams-context.md#user-context) nach, um die **benutzercontext** -API zu verwenden, um Anforderungen entsprechend weiterzuleiten.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-244">✔Refer to the [Teams SDK](../tabs/how-to/access-teams-context.md#user-context) to use the **userContext** API to route requests accordingly.</span></span>

<span data-ttu-id="bdbfb-245">✔ Bezieht sich auf den Microsoft [Teams-Authentifizierungs Fluss für Registerkarten](../tabs/how-to/authentication/auth-flow-tab.md).</span><span class="sxs-lookup"><span data-stu-id="bdbfb-245">✔ Refer to the [Teams authentication flow for tabs](../tabs/how-to/authentication/auth-flow-tab.md).</span></span> <span data-ttu-id="bdbfb-246">Der Authentifizierungs Fluss für Registerkarten ähnelt dem auth-Fluss für Websites.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-246">Authentication flow for tabs is very similar to the auth flow for websites.</span></span> <span data-ttu-id="bdbfb-247">Daher können Registerkarten OAuth 2,0 direkt verwenden.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-247">Thus, tabs can use OAuth 2.0 directly.</span></span> <span data-ttu-id="bdbfb-248">*Siehe auch*, [Microsoft Identity Platform und OAuth 2,0-Autorisierungscode Fluss](/azure/active-directory/develop/v2-oauth2-auth-code-flow).</span><span class="sxs-lookup"><span data-stu-id="bdbfb-248">*See also*, [Microsoft identity platform and OAuth 2.0 authorization code flow](/azure/active-directory/develop/v2-oauth2-auth-code-flow).</span></span>

<span data-ttu-id="bdbfb-249">✔ Nachrichten Erweiterung sollte wie erwartet funktionieren, wenn sich ein Benutzer in einer Besprechungs Ansicht befindet und in der Lage sein sollte, Verfassen von Nachrichten Erweiterungskarten bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-249">✔ Message extension should work as expected when a user is in an in-meeting view and should be able to post compose message extension cards.</span></span>

<span data-ttu-id="bdbfb-250">✔ AppName in-Meeting-ToolTip sollte den APP-Namen in der Besprechungs-U-Leiste angeben.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-250">✔ AppName in-meeting - Tooltip should state the app name in-meeting U-bar.</span></span>

#### <a name="in-meeting-dialog"></a><span data-ttu-id="bdbfb-251">**Dialogfeld "Besprechung"**</span><span class="sxs-lookup"><span data-stu-id="bdbfb-251">**In-meeting dialog**</span></span>

<span data-ttu-id="bdbfb-252">✔ Sie die Entwurfsrichtlinien für das [in-Meeting-Dialogfeld](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)einhalten.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-252">✔ You must adhere to the [in-meeting dialog design guidelines](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog).</span></span>

<span data-ttu-id="bdbfb-253">✔ Bezieht sich auf den Microsoft [Teams-Authentifizierungs Fluss für Registerkarten](../tabs/how-to/authentication/auth-flow-tab.md).</span><span class="sxs-lookup"><span data-stu-id="bdbfb-253">✔ Refer to the [Teams authentication flow for tabs](../tabs/how-to/authentication/auth-flow-tab.md).</span></span>

<span data-ttu-id="bdbfb-254">✔ Verwenden Sie die [Benachrichtigungs](/graph/api/resources/notifications-api-overview?view=graph-rest-beta&preserve-view=true) -API, um zu signalisieren, dass eine Blasen Benachrichtigung ausgelöst werden muss.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-254">✔ Use the [notification](/graph/api/resources/notifications-api-overview?view=graph-rest-beta&preserve-view=true) API to signal that a bubble notification needs to be triggered.</span></span>

<span data-ttu-id="bdbfb-255">✔ Als Teil der Nutzlast der Benachrichtigungsanforderung enthalten die URL, in der der zu präsentierende Inhalt gehostet wird.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-255">✔ As part of the notification request payload, include the URL where the content to be showcased is hosted.</span></span>

<span data-ttu-id="bdbfb-256">✔ In-Meeting-Dialogfeld darf nicht Aufgabenmodul verwenden.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-256">✔ In-meeting dialog must not use task module.</span></span>

> [!NOTE]
>
> * <span data-ttu-id="bdbfb-257">Diese Benachrichtigungen sind in der Natur persistent.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-257">These notifications are persistent in nature.</span></span> <span data-ttu-id="bdbfb-258">Sie müssen die [**submitTask ()**](../task-modules-and-cards/task-modules/task-modules-bots.md#submitting-the-result-of-a-task-module) -Funktion aufrufen, um automatisch zu entlassen, nachdem ein Benutzer eine Aktion in der-Webansicht durchführt.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-258">You must invoke the [**submitTask()**](../task-modules-and-cards/task-modules/task-modules-bots.md#submitting-the-result-of-a-task-module) function to auto-dismiss after a user takes an action in the web-view.</span></span> <span data-ttu-id="bdbfb-259">Dies ist eine Voraussetzung für die APP-Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-259">This is a requirement for app submission.</span></span> <span data-ttu-id="bdbfb-260">*Siehe auch* Microsoft [Teams SDK: Aufgabenmodul](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="bdbfb-260">*See also*, [Teams SDK: task module](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true).</span></span>
>
> * <span data-ttu-id="bdbfb-261">Wenn Ihre APP anonyme Benutzer unterstützen soll, muss ihre anfängliche Anforderungsnutzlast auf die `from.id`  (ID der Benutzer)-Anforderungs Metadaten im `from` Objekt und nicht auf die `from.aadObjectId` Anforderungs Metadaten (Azure Active Directory ID des Benutzers) zurückgreifen.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-261">If you want your app to support anonymous users, your initial invoke request payload must rely on the `from.id`  (ID of the user) request metadata in the `from` object, not the `from.aadObjectId` (Azure Active Directory ID of the user) request metadata.</span></span> <span data-ttu-id="bdbfb-262">*Weitere Informationen finden Sie unter* [Verwenden von Aufgaben Modulen in Registerkarten](../task-modules-and-cards/task-modules/task-modules-tabs.md) und [Erstellen und Senden des Aufgabenmoduls](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request).</span><span class="sxs-lookup"><span data-stu-id="bdbfb-262">*See* [Using task modules in tabs](../task-modules-and-cards/task-modules/task-modules-tabs.md) and [Create and send the task module](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request).</span></span>

### <a name="after-a-meeting"></a><span data-ttu-id="bdbfb-263">Nach einer Besprechung</span><span class="sxs-lookup"><span data-stu-id="bdbfb-263">After a meeting</span></span>

<span data-ttu-id="bdbfb-264">Die Konfigurationen nach der Besprechung und vor der Besprechung sind äquivalent.</span><span class="sxs-lookup"><span data-stu-id="bdbfb-264">The post-meeting and pre-meeting configurations are equivalent.</span></span>

## <a name="meeting-app-sample"></a><span data-ttu-id="bdbfb-265">Beispiel für eine Besprechungs-App</span><span class="sxs-lookup"><span data-stu-id="bdbfb-265">Meeting app sample</span></span>

 > [!div class="nextstepaction"]
> [<span data-ttu-id="bdbfb-266">App für die Besprechungs Token-Generator</span><span class="sxs-lookup"><span data-stu-id="bdbfb-266">Meeting token generator app</span></span>](https://github.com/OfficeDev/microsoft-teams-sample-meetings-token)
