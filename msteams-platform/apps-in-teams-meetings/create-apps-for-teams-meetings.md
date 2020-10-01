---
title: Apps für Teams-Besprechungen erstellen
author: laujan
description: Erstellen von Apps für Microsoft Teams-Besprechungen
ms.topic: conceptual
ms.author: lajanuar
keywords: Teams-apps-Besprechungen Benutzer Teilnehmer-Rollen-API
ms.openlocfilehash: 847e79d188a52892cda8732a2b58cee068cb5e95
ms.sourcegitcommit: e92408e751a8f51028908ab7e2415a8051a536c0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2020
ms.locfileid: "48326305"
---
# <a name="create-apps-for-teams-meetings-release-preview"></a><span data-ttu-id="3e5b9-104">Erstellen von Apps für Microsoft Teams-Besprechungen (Veröffentlichungs Vorschau)</span><span class="sxs-lookup"><span data-stu-id="3e5b9-104">Create apps for Teams meetings (Release Preview)</span></span>

>[!IMPORTANT]
> <span data-ttu-id="3e5b9-105">In der Microsoft Teams-Versions Vorschau hervorgehobene Features werden nur für frühere Einblicke und Feedback Zwecke bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-105">Features highlighted in Microsoft Teams Release Preview are provided for early insight and feedback purposes only.</span></span> <span data-ttu-id="3e5b9-106">Sie können Änderungen unterziehen, bevor Sie aktiviert werden können.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-106">They may undergo changes before they can be enabled.</span></span>

## <a name="prerequisites-and-considerations"></a><span data-ttu-id="3e5b9-107">Voraussetzungen und Überlegungen</span><span class="sxs-lookup"><span data-stu-id="3e5b9-107">Prerequisites and considerations</span></span>

1. <span data-ttu-id="3e5b9-108">Apps in Besprechungen erfordern grundlegende Kenntnisse der [Teams-App-Entwicklung](../overview.md).</span><span class="sxs-lookup"><span data-stu-id="3e5b9-108">Apps in meetings require some basic knowledge of [Teams app development](../overview.md).</span></span> <span data-ttu-id="3e5b9-109">Eine app in einer Besprechung kann aus [Registerkarten](../tabs/what-are-tabs.md), [Bots](../bots/what-are-bots.md)und [Messaging Erweiterungs](../messaging-extensions/what-are-messaging-extensions.md) Features bestehen und erfordert Aktualisierungen des Teams-APP- [Manifests](#update-your-app-manifest) , um anzugeben, dass die APP für Besprechungen zur Verfügung steht.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-109">An app in a meeting can comprise of [tabs](../tabs/what-are-tabs.md), [bots](../bots/what-are-bots.md), and [messaging extensions](../messaging-extensions/what-are-messaging-extensions.md) features and will require updates to the Teams [app manifest](#update-your-app-manifest) to indicate that the app is available for meetings</span></span>

1. <span data-ttu-id="3e5b9-110">Damit Ihre APP im Besprechungs Lebenszyklus als Registerkarte funktioniert, muss Sie konfigurierbare Registerkarten im [Groupchat-Bereich](../resources/schema/manifest-schema.md#configurabletabs)unterstützen.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-110">For your app to function in the meeting lifecycle as a tab, it must support configurable tabs in the [groupchat scope](../resources/schema/manifest-schema.md#configurabletabs).</span></span> <span data-ttu-id="3e5b9-111">*Weitere Informationen finden Sie unter* [Erweitern Ihrer Teams-App mit einer benutzerdefinierten Registerkarte](../tabs/how-to/add-tab.md). Durch die Unterstützung des `groupchat` Bereichs wird Ihre APP in [Besprechungen vor](teams-apps-in-meetings.md#pre-meeting-app-experience) und [nach](teams-apps-in-meetings.md#post-meeting-app-experience) dem Chatten aktiviert.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-111">*See* [Extend your Teams app with a custom tab](../tabs/how-to/add-tab.md). Supporting the `groupchat` scope will enable your app in [pre-meeting](teams-apps-in-meetings.md#pre-meeting-app-experience) and [post-meeting](teams-apps-in-meetings.md#post-meeting-app-experience) chats.</span></span>

1. <span data-ttu-id="3e5b9-112">Die URL-Parameter der Besprechungs-API erfordern möglicherweise, `meetingId` `userId` und die [Mandanten](/onedrive/find-your-office-365-tenant-id) -Nr sind im Rahmen des Teams-Client-SDK und der Bot-Aktivität verfügbar.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-112">Meeting API URL parameters may require `meetingId`, `userId`, and the [tenantId](/onedrive/find-your-office-365-tenant-id) These are available as part of the Teams Client SDK and bot activity.</span></span> <span data-ttu-id="3e5b9-113">Außerdem können zuverlässige Informationen für Benutzer-ID und Mandanten-ID mithilfe der [Registerkarten-SSO-Authentifizierung](../tabs/how-to/authentication/auth-aad-sso.md)abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-113">Additionally, reliable information for user ID and tenant ID can be retrieved using [Tab SSO authentication](../tabs/how-to/authentication/auth-aad-sso.md).</span></span>

1. <span data-ttu-id="3e5b9-114">Einige Besprechungs-APIs, wie zum Beispiel, `GetParticipant` erfordern eine [bot-Registrierung und eine bot-APP-ID](../bots/how-to/create-a-bot-for-teams.md#with-an-azure-subscription) zum Generieren von auth-Token.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-114">Some meeting APIs, such as `GetParticipant` will require a [bot registration and bot app ID](../bots/how-to/create-a-bot-for-teams.md#with-an-azure-subscription) to generate auth tokens.</span></span>

1. <span data-ttu-id="3e5b9-115">Entwickler müssen sich an die allgemeinen [Entwurfsrichtlinien für Teams-Registerkarten](../tabs/design/tabs.md) für Pre-und Post-Meeting-Szenarien sowie die [in-Meeting-Dialogfeld Richtlinien](design/designing-in-meeting-dialog.md) für das in-Meeting-Dialogfeld halten, das während einer Teambesprechung ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-115">Developers must adhere to general [Teams tab design guidelines](../tabs/design/tabs.md) for pre- and post-meeting scenarios as well as the [in-meeting dialog guidelines](design/designing-in-meeting-dialog.md) for in-meeting dialog triggered during a Teams meeting.</span></span>

## <a name="meeting-apps-api-reference"></a><span data-ttu-id="3e5b9-116">Besprechungs-apps-API-Referenz</span><span class="sxs-lookup"><span data-stu-id="3e5b9-116">Meeting apps API reference</span></span>

|<span data-ttu-id="3e5b9-117">API</span><span class="sxs-lookup"><span data-stu-id="3e5b9-117">API</span></span>|<span data-ttu-id="3e5b9-118">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3e5b9-118">Description</span></span>|<span data-ttu-id="3e5b9-119">Anforderung</span><span class="sxs-lookup"><span data-stu-id="3e5b9-119">Request</span></span>|<span data-ttu-id="3e5b9-120">Quelle</span><span class="sxs-lookup"><span data-stu-id="3e5b9-120">Source</span></span>|
|---|---|----|---|
|<span data-ttu-id="3e5b9-121">**Getusercontext**</span><span class="sxs-lookup"><span data-stu-id="3e5b9-121">**GetUserContext**</span></span>| <span data-ttu-id="3e5b9-122">Abrufen von Kontextinformationen zum Anzeigen relevanter Inhalte auf einer Registerkarte Teams.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-122">Get contextual information to display relevant content in a Teams tab.</span></span> |<span data-ttu-id="3e5b9-123">_**verläuft. GetContext (() => {/*...\* / } )*\*_</span><span class="sxs-lookup"><span data-stu-id="3e5b9-123">_**microsoftTeams.getContext( ( ) => {  /*...*/ } )**_</span></span>|<span data-ttu-id="3e5b9-124">Microsoft Teams-Client-SDK</span><span class="sxs-lookup"><span data-stu-id="3e5b9-124">Microsoft Teams client SDK</span></span>|
|<span data-ttu-id="3e5b9-125">**Getparticipant**</span><span class="sxs-lookup"><span data-stu-id="3e5b9-125">**GetParticipant**</span></span>|<span data-ttu-id="3e5b9-126">Mit dieser API kann ein bot eine Teilnehmer Information nach Besprechungs-ID und Teilnehmer-ID abrufen.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-126">This API allows a bot to fetch a participant information by meeting id and participant id.</span></span>|<span data-ttu-id="3e5b9-127">**GET** _ **/V1/Meetings/{meetingId}/participants/{participantId} abrufen? Mandanten-Nr = {Mandanten** -Nr}_</span><span class="sxs-lookup"><span data-stu-id="3e5b9-127">**GET** _**/v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}**_</span></span> |<span data-ttu-id="3e5b9-128">Microsoft bot Framework SDK</span><span class="sxs-lookup"><span data-stu-id="3e5b9-128">Microsoft Bot Framework SDK</span></span>|
|<span data-ttu-id="3e5b9-129">**NotificationSignal**</span><span class="sxs-lookup"><span data-stu-id="3e5b9-129">**NotificationSignal**</span></span> |<span data-ttu-id="3e5b9-130">Besprechungs Signale werden über die folgende vorhandene Benachrichtigungs-API für Unterhaltungen (für Benutzer-bot-Chat) übermittelt.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-130">Meeting signals will be delivered using the following existing conversation notification API (for user-bot chat).</span></span> <span data-ttu-id="3e5b9-131">Mit dieser API können Entwickler basierend auf der Endbenutzer Aktion signalisieren, dass eine Dialog Blase in einer Besprechung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-131">This API allows developers to signal based on end-user action to show-case an in-meeting dialog bubble.</span></span>|<span data-ttu-id="3e5b9-132">**Post** _ **/V3/Conversations/{conversationId}/Activities**_</span><span class="sxs-lookup"><span data-stu-id="3e5b9-132">**POST** _**/v3/conversations/{conversationId}/activities**_</span></span>|<span data-ttu-id="3e5b9-133">Microsoft bot Framework SDK</span><span class="sxs-lookup"><span data-stu-id="3e5b9-133">Microsoft Bot Framework SDK</span></span>|

### <a name="getusercontext"></a><span data-ttu-id="3e5b9-134">Getusercontext</span><span class="sxs-lookup"><span data-stu-id="3e5b9-134">GetUserContext</span></span>

<span data-ttu-id="3e5b9-135">Eine Anleitung zum Identifizieren und Abrufen von Kontextinformationen für die Registerkarteninhalte finden Sie in der Dokumentation zu [Get Context for your Teams](../tabs/how-to/access-teams-context.md#getting-context-by-using-the-microsoft-teams-javascript-library) .</span><span class="sxs-lookup"><span data-stu-id="3e5b9-135">Please refer to our [Get context for your Teams tab](../tabs/how-to/access-teams-context.md#getting-context-by-using-the-microsoft-teams-javascript-library) documentation for guidance on identifying and  retrieving contextual information for your tab content.</span></span> <span data-ttu-id="3e5b9-136">Im Rahmen der Erweiterbarkeit von Besprechungen wurde für die Antwort Nutzlast ein neuer Wert hinzugefügt:</span><span class="sxs-lookup"><span data-stu-id="3e5b9-136">As part of meetings extensibility, a new value has been added for the response payload:</span></span>

<span data-ttu-id="3e5b9-137">✔- **Besprechungs**-Nr: wird von einer Registerkarte bei der Ausführung im Besprechungs Kontext verwendet.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-137">✔ **meetingId**: used by a tab when running in the meeting context.</span></span>

### <a name="getparticipant-api"></a><span data-ttu-id="3e5b9-138">Getparticipant-API</span><span class="sxs-lookup"><span data-stu-id="3e5b9-138">GetParticipant API</span></span>

> [!NOTE]
>
> * <span data-ttu-id="3e5b9-139">Sie sollten keine Teilnehmerrollen Zwischenspeichern, da der Besprechungsorganisator zu einem beliebigen Zeitpunkt eine Rolle ändern kann.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-139">Do not cache participant roles since the meeting organizer can change a role at any point in time.</span></span>
>
> * <span data-ttu-id="3e5b9-140">Microsoft Teams unterstützt derzeit keine großen Verteilerlisten oder Dienstplan Größen von mehr als 350 Teilnehmern für die `GetParticipant` API.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-140">Teams does not currently support large distribution lists or roster sizes of more than 350 participants for the `GetParticipant` API.</span></span>
>
> * <span data-ttu-id="3e5b9-141">Die Unterstützung für das bot Framework SDK wird in Kürze verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-141">Support for the Bot Framework SDK is coming soon.</span></span>

#### <a name="request"></a><span data-ttu-id="3e5b9-142">Anforderung</span><span class="sxs-lookup"><span data-stu-id="3e5b9-142">Request</span></span>

```http
GET /v3/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}
```

<span data-ttu-id="3e5b9-143">*Siehe* [bot Framework-API-Referenz](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="3e5b9-143">*See* the [Bot Framework API reference](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0&preserve-view=true).</span></span>

<!-- markdownlint-disable MD025 -->

<span data-ttu-id="3e5b9-144">**C#-Beispiel**</span><span class="sxs-lookup"><span data-stu-id="3e5b9-144">**C# Example**</span></span>

```csharp
string meetingId = "meetingid?";
string participantId = "participantidhere";
var connectorClient = turnContext.TurnState.Get<IConnectorClient>();
var creds = connectorClient.Credentials as AppCredentials;
var bearerToken = await creds.GetTokenAsync().ConfigureAwait(false);
var request = new HttpRequestMessage();
request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", bearerToken);
request.Method = new HttpMethod("GET");
request.RequestUri = new System.Uri(Path.Combine(connectorClient.BaseUri.OriginalString, $"/meetings/{meetingId}/participants/{participantId}"));
HttpResponseMessage response = await (connectorClient as ServiceClient<ConnectorClient>).HttpClient.SendAsync(request, cancellationToken).ConfigureAwait(false);
if (response.StatusCode == System.Net.HttpStatusCode.OK)
{
    var content = await response.Content.ReadAsStringAsync().ConfigureAwait(false);
    var theObject = Rest.Serialization.SafeJsonConvert.DeserializeObject<WhateverObjectIsReturned>(content, connectorClient.DeserializationSettings);
```

* * *
<!-- markdownlint-disable MD001 -->

#### <a name="query-parameters"></a><span data-ttu-id="3e5b9-145">Abfrageparameter</span><span class="sxs-lookup"><span data-stu-id="3e5b9-145">Query parameters</span></span>

<span data-ttu-id="3e5b9-146">**Besprechungs**-Nr.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-146">**meetingId**.</span></span> <span data-ttu-id="3e5b9-147">Die Besprechungs-ID ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-147">The meeting identifier is required.</span></span>  
<span data-ttu-id="3e5b9-148">**Teilnehmer**-Nr.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-148">**participantId**.</span></span> <span data-ttu-id="3e5b9-149">Die Teilnehmer-ID ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-149">The participant identifier is required.</span></span>  
<span data-ttu-id="3e5b9-150">**Mandanten**-Nr.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-150">**tenantId**.</span></span> <span data-ttu-id="3e5b9-151">[Mandanten-ID](/onedrive/find-your-office-365-tenant-id) des Teilnehmers.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-151">[Tenant id](/onedrive/find-your-office-365-tenant-id) of the participant.</span></span> <span data-ttu-id="3e5b9-152">Für Mandanten Benutzer erforderlich.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-152">Required for tenant user.</span></span>

#### <a name="response-payload"></a><span data-ttu-id="3e5b9-153">Antwort Nutzlast</span><span class="sxs-lookup"><span data-stu-id="3e5b9-153">Response Payload</span></span>
<!-- markdownlint-disable MD036 -->

<span data-ttu-id="3e5b9-154">**Beispiel 1**</span><span class="sxs-lookup"><span data-stu-id="3e5b9-154">**Example 1**</span></span>

```json
{
    "meetingRole":"Presenter",
    "conversation":{
            "isGroup": true,
            "id": "19:meeting_NDQxMzg1YjUtMGIzNC00Yjc1LWFmYWYtYzk1MGY2MTMwNjE0@thread.v2"
        }
}
```

<span data-ttu-id="3e5b9-155">**meetingRole** kann *Organisator*, *Referent*oder *Teilnehmer*sein.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-155">**meetingRole** can be *Organizer*, *Presenter*, or *Attendee*.</span></span>

<span data-ttu-id="3e5b9-156">**Beispiel 2**</span><span class="sxs-lookup"><span data-stu-id="3e5b9-156">**Example 2**</span></span>

```json
{
   "meetingRole":"Presenter",
   "conversation":{
      "isGroup":true,
      "id":"19:meeting_NDQxMzg1YjUtMGIzNC00Yjc1LWFmYWYtYzk1MGY2MTMwNjE0@thread.v2"
   }
}
```

#### <a name="response-codes"></a><span data-ttu-id="3e5b9-157">Antwort Codes</span><span class="sxs-lookup"><span data-stu-id="3e5b9-157">Response Codes</span></span>

<span data-ttu-id="3e5b9-158">**403**: die APP darf keine Teilnehmer Informationen erhalten.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-158">**403**: the app is not allowed to get participant information.</span></span> <span data-ttu-id="3e5b9-159">Dies ist die häufigste Fehlerantwort und wird ausgelöst, wenn die APP nicht in der Besprechung installiert wird, beispielsweise wenn die APP vom mandantenadministrator deaktiviert oder während der Live-Website Minderung blockiert wird.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-159">This will be the most common error response and is triggered when the app is not installed in the meeting such as when the app is disabled by tenant admin or blocked during live site mitigation.</span></span>  
<span data-ttu-id="3e5b9-160">**200**: Teilnehmer Informationen erfolgreich abgerufen</span><span class="sxs-lookup"><span data-stu-id="3e5b9-160">**200**: participant information successfully retrieved</span></span>  
<span data-ttu-id="3e5b9-161">**401**: Ungültiges Token</span><span class="sxs-lookup"><span data-stu-id="3e5b9-161">**401**: invalid token</span></span>  
<span data-ttu-id="3e5b9-162">**404**: die Besprechung ist nicht vorhanden, oder der Teilnehmer kann nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-162">**404**: the meeting doesn't exist or participant can’t be found.</span></span>

<!-- markdownlint-disable MD024 -->
### <a name="notificationsignal-api"></a><span data-ttu-id="3e5b9-163">NotificationSignal-API</span><span class="sxs-lookup"><span data-stu-id="3e5b9-163">NotificationSignal API</span></span>

> [!NOTE]
> <span data-ttu-id="3e5b9-164">Wenn ein in-Meeting-Dialogfeld aufgerufen wird, wird derselbe Inhalt auch als Chatnachricht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-164">When an in-meeting dialog is invoked, the same content will also be presented as a chat message.</span></span>

#### <a name="request"></a><span data-ttu-id="3e5b9-165">Anforderung</span><span class="sxs-lookup"><span data-stu-id="3e5b9-165">Request</span></span>

```http
POST /v3/conversations/{conversationId}/activities
```

#### <a name="query-parameters"></a><span data-ttu-id="3e5b9-166">Abfrageparameter</span><span class="sxs-lookup"><span data-stu-id="3e5b9-166">Query parameters</span></span>

<span data-ttu-id="3e5b9-167">**Conversation**-ID: der Konversationsbezeichner.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-167">**conversationId**: The conversation identifier.</span></span> <span data-ttu-id="3e5b9-168">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="3e5b9-168">Required</span></span>

#### <a name="request-payload"></a><span data-ttu-id="3e5b9-169">Anforderungsnutzlast</span><span class="sxs-lookup"><span data-stu-id="3e5b9-169">Request Payload</span></span>

# <a name="json"></a>[<span data-ttu-id="3e5b9-170">Json</span><span class="sxs-lookup"><span data-stu-id="3e5b9-170">JSON</span></span>](#tab/json)

```json
{
    "type": "message",
    "text": "John Phillips assigned you a weekly todo",
    "summary": "Don't forget to meet with Marketing next week",
    "channelData": {
    "notification": {
    "alertInMeeting": true,
    "externalResourceUrl": "https://teams.microsoft.com/l/bubble/APP_ID?url=&height=&width=&title=<TaskInfo.title>"
    }
},
    "replyToId": "1493070356924"
    }
```

# <a name="cnet"></a>[<span data-ttu-id="3e5b9-171">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="3e5b9-171">C#/.NET</span></span>](#tab/dotnet)

```csharp
Activity activity = MessageFactory.Text("This is a meeting signal test");
MeetingNotification notification = new MeetingNotification
{
    AlertInMeeting = true,
    ExternalResourceUrl = "https://teams.microsoft.com/l/bubble/APP_ID?url=&height=&width=&title=<TaskInfo.title>"
};
activity.ChannelData = new TeamsChannelData
{
    Notification = notification
};
await turnContext.SendActivityAsync(activity).ConfigureAwait(false);
```

# <a name="javascript"></a>[<span data-ttu-id="3e5b9-172">JavaScript</span><span class="sxs-lookup"><span data-stu-id="3e5b9-172">JavaScript</span></span>](#tab/javascript)

```javascript

const replyActivity = MessageFactory.text('Hi'); // this could be an adaptive card instead
        replyActivity.channelData = {
            notification: {
                alertInMeeting: true,
                externalResourceUrl: 'https://teams.microsoft.com/l/bubble/APP_ID?url=<TaskInfo.url>&height=<TaskInfo.height>&width=<TaskInfo.width>&title=<TaskInfo.title>’
            }
        };
        await context.sendActivity(replyActivity);
```

* * *

> [!IMPORTANT]
> <span data-ttu-id="3e5b9-173">Die URL in der Inhalts Blase (taskInfo-URL) muss in der Liste [gültiger Domänen](../resources/schema/manifest-schema.md#validdomains) enthalten sein, die im App-Manifest für Teams enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-173">The URL in the content bubble (taskInfo URL) must be included in the [valid domains](../resources/schema/manifest-schema.md#validdomains) list included in the Teams app manifest.</span></span>

#### <a name="response-codes"></a><span data-ttu-id="3e5b9-174">Antwort Codes</span><span class="sxs-lookup"><span data-stu-id="3e5b9-174">Response Codes</span></span>

<span data-ttu-id="3e5b9-175">**201**: Aktivität mit Signal wurde erfolgreich gesendet</span><span class="sxs-lookup"><span data-stu-id="3e5b9-175">**201**: activity with signal is successfully sent</span></span>  
<span data-ttu-id="3e5b9-176">**401**: Ungültiges Token</span><span class="sxs-lookup"><span data-stu-id="3e5b9-176">**401**: invalid token</span></span>  
<span data-ttu-id="3e5b9-177">**403**: die APP darf das Signal nicht senden.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-177">**403**: the app is not allowed to send the signal.</span></span> <span data-ttu-id="3e5b9-178">In diesem Fall sollte die Nutzlast eine ausführlichere Fehlermeldung enthalten.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-178">In this case, the payload should contain more detail error message.</span></span> <span data-ttu-id="3e5b9-179">Es kann viele Gründe geben: app, die vom mandantenadministrator deaktiviert, während einer Live-Standort Minderung blockiert wird, usw.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-179">There can be many reasons: app disabled by tenant admin, blocked during live site mitigation, etc.</span></span>  
<span data-ttu-id="3e5b9-180">**404**: Besprechungs Chat nicht vorhanden</span><span class="sxs-lookup"><span data-stu-id="3e5b9-180">**404**: meeting chat doesn't exist</span></span>  

## <a name="enable-your-app-for-teams-meetings"></a><span data-ttu-id="3e5b9-181">Aktivieren Ihrer APP für Microsoft Teams-Besprechungen</span><span class="sxs-lookup"><span data-stu-id="3e5b9-181">Enable your app for Teams meetings</span></span>

### <a name="update-your-app-manifest"></a><span data-ttu-id="3e5b9-182">Aktualisieren des App-Manifests</span><span class="sxs-lookup"><span data-stu-id="3e5b9-182">Update your app manifest</span></span>

<span data-ttu-id="3e5b9-183">Die APP-Funktionen für Besprechungen werden in Ihrem App-Manifest über die **configurableTabs**  ->  -**Bereiche** und **Kontext** Arrays deklariert.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-183">The meetings app capabilities are declared in your app manifest via the **configurableTabs** -> **scopes** and **context** arrays.</span></span> <span data-ttu-id="3e5b9-184">*Scope* definiert, an wen und in welchem *Kontext* definiert wird, wo Ihre app verfügbar sein wird.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-184">*Scope* defines to whom and *context* defines where your app will be available.</span></span>

> [!NOTE]
> <span data-ttu-id="3e5b9-185">Verwenden Sie das [Manifest-Schema für Entwicklervorschau](../resources/schema/manifest-schema-dev-preview.md) , um dieses in Ihrem App-Manifest zu testen.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-185">Please use [Developer Preview manifest schema](../resources/schema/manifest-schema-dev-preview.md) to try this in your app manifest.</span></span>

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

### <a name="context-property"></a><span data-ttu-id="3e5b9-186">Context-Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="3e5b9-186">Context property</span></span>

<span data-ttu-id="3e5b9-187">Die Registerkarte `context` und die `scopes` Eigenschaften funktionieren in Harmonie, damit Sie bestimmen können, wo Ihre APP angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-187">The tab `context` and `scopes` properties work in harmony to allow you to determine where you want your app to appear.</span></span> <span data-ttu-id="3e5b9-188">Registerkarten im `team` `groupchat` Bereich oder können mehr als einen Kontext aufweisen.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-188">Tabs in the `team` or `groupchat` scope can have more than one context.</span></span> <span data-ttu-id="3e5b9-189">Die möglichen Werte für die Context-Eigenschaft lauten wie folgt:</span><span class="sxs-lookup"><span data-stu-id="3e5b9-189">The possible values for the context property are as follows:</span></span>

* <span data-ttu-id="3e5b9-190">**channelTab**: eine Registerkarte in der Kopfzeile eines Team Kanals.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-190">**channelTab**: a tab in the header of a team channel.</span></span>
* <span data-ttu-id="3e5b9-191">**privateChatTab**: eine Registerkarte in der Kopfzeile eines Gruppenchats zwischen einer Gruppe von Benutzern, die sich nicht im Kontext eines Teams oder einer Besprechung befinden.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-191">**privateChatTab**: a tab in the header of a group chat between a set of users not in the context of a team or meeting.</span></span>
* <span data-ttu-id="3e5b9-192">**meetingChatTab**: eine Registerkarte in der Kopfzeile eines Gruppenchats zwischen einer Gruppe von Benutzern im Kontext einer geplanten Besprechung.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-192">**meetingChatTab**: a tab in the header of a group chat between a set of users in the context of a scheduled meeting.</span></span>
* <span data-ttu-id="3e5b9-193">**meetingDetailsTab**: eine Registerkarte in der Kopfzeile der Ansicht "Besprechungsdetails" des Kalenders.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-193">**meetingDetailsTab**: a tab in the header of the meeting details view of the calendar.</span></span>
* <span data-ttu-id="3e5b9-194">**meetingSidePanel**: ein in-Meeting-Bereich, der über den einheitlichen Balken geöffnet wird (u-Leiste).</span><span class="sxs-lookup"><span data-stu-id="3e5b9-194">**meetingSidePanel**: an in-meeting panel opened via the unified bar (u-bar).</span></span>

## <a name="configure-your-app-for-meeting-scenarios"></a><span data-ttu-id="3e5b9-195">Konfigurieren Ihrer APP für Besprechungs Szenarien</span><span class="sxs-lookup"><span data-stu-id="3e5b9-195">Configure your app for meeting scenarios</span></span>

> [!NOTE]
> <span data-ttu-id="3e5b9-196">Damit Ihre APP im Registerkarten Katalog sichtbar ist, muss Sie **konfigurierbare Registerkarten** und den **Gruppenchat Bereich**unterstützen.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-196">For your app to be visible in the tab gallery it needs to **support configurable tabs** and the **group chat scope**.</span></span>

### <a name="pre-meeting"></a><span data-ttu-id="3e5b9-197">Pre-Meeting</span><span class="sxs-lookup"><span data-stu-id="3e5b9-197">Pre-meeting</span></span>

<span data-ttu-id="3e5b9-198">Benutzer mit Organizer-und/oder Presenter-Rollen fügen mithilfe der Schaltfläche Plus ➕ auf der Seite Besprechungs- **Chat** und Besprechungs **Details** Registerkarten zu einer Besprechung hinzu.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-198">Users with organizer and/or presenter roles add tabs to a meeting using the plus ➕ button in the meeting **Chat** and meeting **details** pages.</span></span> <span data-ttu-id="3e5b9-199">Messaging Erweiterungen werden über das Menü Ellipsen/Überlauf hinzugefügt, &#x25CF;&#x25CF;&#x25CF; unterhalb des Bereichs zum Verfassen von Nachrichten im Chat angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-199">Messaging extensions are added to via the ellipses/overflow menu &#x25CF;&#x25CF;&#x25CF; located beneath the compose message area in the chat.</span></span> <span data-ttu-id="3e5b9-200">Bots werden mit der Taste "" zu einem Besprechungs Chat hinzugefügt **@** und die Option **Bots abrufen**ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-200">Bots are added to a meeting chat using the "**@**" key and selecting **Get bots**.</span></span>

<span data-ttu-id="3e5b9-201">✔ Die Benutzeridentität *muss* über die [Registerkarten SSO](../tabs/how-to/authentication/auth-aad-sso.md)bestätigt werden.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-201">✔ The user identity *must* be confirmed via [Tabs SSO](../tabs/how-to/authentication/auth-aad-sso.md).</span></span> <span data-ttu-id="3e5b9-202">Nach dieser Authentifizierung kann die APP die Benutzerrolle über die getteilnehmer-API abrufen.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-202">Following this authentication, the app can retrieve the user role via the GetParticipant API.</span></span>

 <span data-ttu-id="3e5b9-203">✔ Basierend auf der Benutzerrolle kann die App nun rollenspezifische Erlebnisse vorlegen.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-203">✔ Based on the user role, the app will now have the capability to present role specific experiences.</span></span> <span data-ttu-id="3e5b9-204">Beispielsweise kann eine Polling-app nur Organisatoren und Referenten das Erstellen einer neuen Umfrage gestatten.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-204">For example, a polling app can allow only organizers and presenters to create a new poll.</span></span>

> <span data-ttu-id="3e5b9-205">**Hinweis**: Rollenzuweisungen können geändert werden, während eine Besprechung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-205">**NOTE**: Role assignments can be changed while a meeting is in progress.</span></span>  <span data-ttu-id="3e5b9-206">*Siehe* [roles in a Teams Meeting](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).</span><span class="sxs-lookup"><span data-stu-id="3e5b9-206">*See* [Roles in a Teams meeting](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).</span></span> 

### <a name="in-meeting"></a><span data-ttu-id="3e5b9-207">In-Meeting</span><span class="sxs-lookup"><span data-stu-id="3e5b9-207">In-meeting</span></span>

#### <a name="sidepanel"></a><span data-ttu-id="3e5b9-208">**sidePanel**</span><span class="sxs-lookup"><span data-stu-id="3e5b9-208">**sidePanel**</span></span>

<span data-ttu-id="3e5b9-209">✔ In Ihrem App-Manifest fügen Sie **sidePanel** dem **Kontext** Array hinzu, wie oben beschrieben.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-209">✔ In your app manifest add **sidePanel** to the **context** array as described above.</span></span>

<span data-ttu-id="3e5b9-210">✔ In der Besprechung als auch in allen Szenarien wird die app in einer in-Meeting-Registerkarte gerendert, die 320 Pixel groß in der Breite ist.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-210">✔ In the meeting as well as in all scenarios, the app will be rendered in an in-meeting tab that is 320px in width.</span></span> <span data-ttu-id="3e5b9-211">Die Registerkarte muss dafür optimiert werden.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-211">Your tab must be optimized for this.</span></span> <span data-ttu-id="3e5b9-212">*Siehe*, [framecontext-Schnittstelle](/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="3e5b9-212">*See*, [FrameContext interface](/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest&preserve-view=true)</span></span>

<span data-ttu-id="3e5b9-213">✔ Sie im Microsoft [Teams-SDK](../tabs/how-to/access-teams-context.md#user-context) nach, um die **benutzercontext** -API zu verwenden, um Anforderungen entsprechend weiterzuleiten.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-213">✔Refer to the [Teams SDK](../tabs/how-to/access-teams-context.md#user-context) to use the **userContext** API to route requests accordingly.</span></span>

<span data-ttu-id="3e5b9-214">✔ Bezieht sich auf den Microsoft [Teams-Authentifizierungs Fluss für Registerkarten](../tabs/how-to/authentication/auth-flow-tab.md).</span><span class="sxs-lookup"><span data-stu-id="3e5b9-214">✔ Refer to the [Teams authentication flow for tabs](../tabs/how-to/authentication/auth-flow-tab.md).</span></span> <span data-ttu-id="3e5b9-215">Der Authentifizierungs Fluss für Registerkarten ähnelt dem auth-Fluss für Websites.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-215">Authentication flow for tabs is very similar to the auth flow for websites.</span></span> <span data-ttu-id="3e5b9-216">Daher können Registerkarten OAuth 2,0 direkt verwenden.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-216">Thus, tabs can use OAuth 2.0 directly.</span></span> <span data-ttu-id="3e5b9-217">*Siehe auch*, [Microsoft Identity Platform und OAuth 2,0-Autorisierungscode Fluss](/azure/active-directory/develop/v2-oauth2-auth-code-flow).</span><span class="sxs-lookup"><span data-stu-id="3e5b9-217">*See also*, [Microsoft identity platform and OAuth 2.0 authorization code flow](/azure/active-directory/develop/v2-oauth2-auth-code-flow).</span></span>

#### <a name="in-meeting-dialog"></a><span data-ttu-id="3e5b9-218">**in-Meeting-Dialog**</span><span class="sxs-lookup"><span data-stu-id="3e5b9-218">**in-meeting dialog**</span></span>

<span data-ttu-id="3e5b9-219">✔ Sie die Entwurfsrichtlinien für das [in-Meeting-Dialogfeld](design/designing-in-meeting-dialog.md)einhalten.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-219">✔ You must adhere to the [in-meeting dialog design guidelines](design/designing-in-meeting-dialog.md).</span></span>

<span data-ttu-id="3e5b9-220">✔ Bezieht sich auf den Microsoft [Teams-Authentifizierungs Fluss für Registerkarten](../tabs/how-to/authentication/auth-flow-tab.md).</span><span class="sxs-lookup"><span data-stu-id="3e5b9-220">✔ Refer to the [Teams authentication flow for tabs](../tabs/how-to/authentication/auth-flow-tab.md).</span></span>

<span data-ttu-id="3e5b9-221">✔ Verwenden Sie die [Benachrichtigungs](/graph/api/resources/notifications-api-overview?view=graph-rest-beta&preserve-view=true) -API, um zu signalisieren, dass eine Blasen Benachrichtigung ausgelöst werden muss.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-221">✔ Use the [notification](/graph/api/resources/notifications-api-overview?view=graph-rest-beta&preserve-view=true) API to signal that a bubble notification needs to be triggered.</span></span>

<span data-ttu-id="3e5b9-222">✔ Als Teil der Nutzlast der Benachrichtigungsanforderung enthalten die URL, in der der zu präsentierende Inhalt gehostet wird.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-222">✔ As part of the notification request payload, include the URL where the content to be showcased is hosted.</span></span>

> [!NOTE]
>
> * <span data-ttu-id="3e5b9-223">Diese Benachrichtigungen sind in der Natur persistent.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-223">These notifications are persistent in nature.</span></span> <span data-ttu-id="3e5b9-224">Sie müssen die [**submitTask ()**](../task-modules-and-cards/task-modules/task-modules-bots.md#submitting-the-result-of-a-task-module) -Funktion aufrufen, um automatisch zu entlassen, nachdem ein Benutzer eine Aktion in der-Webansicht durchführt.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-224">You must invoke the [**submitTask()**](../task-modules-and-cards/task-modules/task-modules-bots.md#submitting-the-result-of-a-task-module) function to auto-dismiss after a user takes an action in the web-view.</span></span> <span data-ttu-id="3e5b9-225">Dies ist eine Voraussetzung für die APP-Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-225">This is a requirement for app submission.</span></span> <span data-ttu-id="3e5b9-226">*Siehe auch*Microsoft [Teams SDK: Aufgabenmodul](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="3e5b9-226">*See also*, [Teams SDK: task module](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true).</span></span>
>
> * <span data-ttu-id="3e5b9-227">Wenn Ihre APP anonyme Benutzer unterstützen soll, muss ihre anfängliche Anforderungsnutzlast auf die `from.id`  (ID der Benutzer)-Anforderungs Metadaten im `from` Objekt und nicht auf die `from.aadObjectId` Anforderungs Metadaten (Azure Active Directory ID des Benutzers) zurückgreifen.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-227">If you want your app to support anonymous users, your initial invoke request payload must rely on the `from.id`  (ID of the user) request metadata in the `from` object, not the `from.aadObjectId` (Azure Active Directory ID of the user) request metadata.</span></span> <span data-ttu-id="3e5b9-228">*Weitere Informationen finden Sie unter* [Verwenden von Aufgaben Modulen in Registerkarten](../task-modules-and-cards/task-modules/task-modules-tabs.md) und [Erstellen und Senden des Aufgabenmoduls](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request).</span><span class="sxs-lookup"><span data-stu-id="3e5b9-228">*See* [Using task modules in tabs](../task-modules-and-cards/task-modules/task-modules-tabs.md) and [Create and send the task module](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request).</span></span>

### <a name="post-meeting"></a><span data-ttu-id="3e5b9-229">Nachbesprechung</span><span class="sxs-lookup"><span data-stu-id="3e5b9-229">Post-meeting</span></span>

<span data-ttu-id="3e5b9-230">Die Konfigurationen nach der Besprechung und vor der Besprechung sind äquivalent.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-230">The post-meeting and pre-meeting configurations are equivalent.</span></span>

## <a name="meeting-app-sample"></a><span data-ttu-id="3e5b9-231">Beispiel für eine Besprechungs-App</span><span class="sxs-lookup"><span data-stu-id="3e5b9-231">Meeting app sample</span></span>

 > [!div class="nextstepaction"]
> [<span data-ttu-id="3e5b9-232">App für die Besprechungs Token-Generator</span><span class="sxs-lookup"><span data-stu-id="3e5b9-232">Meeting token generator app</span></span>](https://github.com/OfficeDev/microsoft-teams-sample-meetings-token)
