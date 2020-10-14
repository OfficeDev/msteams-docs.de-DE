---
title: Apps für Teams-Besprechungen erstellen
author: laujan
description: Erstellen von Apps für Microsoft Teams-Besprechungen
ms.topic: conceptual
ms.author: lajanuar
keywords: Teams-apps-Besprechungen Benutzer Teilnehmer-Rollen-API
ms.openlocfilehash: e80dd50590d9e0828ab094c691a6b8e07ace3b0c
ms.sourcegitcommit: d61f14053fc695bc1956bf50e83956613c19ccca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2020
ms.locfileid: "48452624"
---
# <a name="create-apps-for-teams-meetings-developer-preview"></a><span data-ttu-id="dd456-104">Erstellen von Apps für Microsoft Teams-Besprechungen (Entwicklervorschau)</span><span class="sxs-lookup"><span data-stu-id="dd456-104">Create apps for Teams meetings (Developer Preview)</span></span>

>[!IMPORTANT]
> <span data-ttu-id="dd456-105">In der Entwicklervorschau von Microsoft Teams enthaltene Features werden nur für frühere Zugriffs-, Test-und Feedback Zwecke bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="dd456-105">Features included in Microsoft Teams Developer Preview are provided for early-access, testing, and feedback purposes only.</span></span> <span data-ttu-id="dd456-106">Sie werden möglicherweise geändert, bevor Sie in der öffentlichen Version verfügbar werden und sollten nicht in Produktionsanwendungen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="dd456-106">They may undergo changes before becoming available in the public release and should not be used in production applications.</span></span>

## <a name="prerequisites-and-considerations"></a><span data-ttu-id="dd456-107">Voraussetzungen und Überlegungen</span><span class="sxs-lookup"><span data-stu-id="dd456-107">Prerequisites and considerations</span></span>

1. <span data-ttu-id="dd456-108">Apps in Besprechungen erfordern grundlegende Kenntnisse der [Teams-App-Entwicklung](../overview.md).</span><span class="sxs-lookup"><span data-stu-id="dd456-108">Apps in meetings require some basic knowledge of [Teams app development](../overview.md).</span></span> <span data-ttu-id="dd456-109">Eine app in einer Besprechung kann aus [Registerkarten](../tabs/what-are-tabs.md), [Bots](../bots/what-are-bots.md)und [Messaging Erweiterungs](../messaging-extensions/what-are-messaging-extensions.md) Features bestehen und erfordert Aktualisierungen des Teams-APP- [Manifests](#update-your-app-manifest) , um anzugeben, dass die APP für Besprechungen zur Verfügung steht.</span><span class="sxs-lookup"><span data-stu-id="dd456-109">An app in a meeting can comprise of [tabs](../tabs/what-are-tabs.md), [bots](../bots/what-are-bots.md), and [messaging extensions](../messaging-extensions/what-are-messaging-extensions.md) features and will require updates to the Teams [app manifest](#update-your-app-manifest) to indicate that the app is available for meetings</span></span>

1. <span data-ttu-id="dd456-110">Damit Ihre APP im Besprechungs Lebenszyklus als Registerkarte funktioniert, muss Sie konfigurierbare Registerkarten im [Groupchat-Bereich](../resources/schema/manifest-schema.md#configurabletabs)unterstützen.</span><span class="sxs-lookup"><span data-stu-id="dd456-110">For your app to function in the meeting lifecycle as a tab, it must support configurable tabs in the [groupchat scope](../resources/schema/manifest-schema.md#configurabletabs).</span></span> <span data-ttu-id="dd456-111">*Weitere Informationen finden Sie unter* [Erweitern Ihrer Teams-App mit einer benutzerdefinierten Registerkarte](../tabs/how-to/add-tab.md). Durch die Unterstützung des `groupchat` Bereichs wird Ihre APP in [Besprechungen vor](teams-apps-in-meetings.md#pre-meeting-app-experience) und [nach](teams-apps-in-meetings.md#post-meeting-app-experience) dem Chatten aktiviert.</span><span class="sxs-lookup"><span data-stu-id="dd456-111">*See* [Extend your Teams app with a custom tab](../tabs/how-to/add-tab.md). Supporting the `groupchat` scope will enable your app in [pre-meeting](teams-apps-in-meetings.md#pre-meeting-app-experience) and [post-meeting](teams-apps-in-meetings.md#post-meeting-app-experience) chats.</span></span>

1. <span data-ttu-id="dd456-112">Die URL-Parameter der Besprechungs-API erfordern möglicherweise, `meetingId` `userId` und die [Mandanten](/onedrive/find-your-office-365-tenant-id) -Nr sind im Rahmen des Teams-Client-SDK und der Bot-Aktivität verfügbar.</span><span class="sxs-lookup"><span data-stu-id="dd456-112">Meeting API URL parameters may require `meetingId`, `userId`, and the [tenantId](/onedrive/find-your-office-365-tenant-id) These are available as part of the Teams Client SDK and bot activity.</span></span> <span data-ttu-id="dd456-113">Außerdem können zuverlässige Informationen für Benutzer-ID und Mandanten-ID mithilfe der [Registerkarten-SSO-Authentifizierung](../tabs/how-to/authentication/auth-aad-sso.md)abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="dd456-113">Additionally, reliable information for user ID and tenant ID can be retrieved using [Tab SSO authentication](../tabs/how-to/authentication/auth-aad-sso.md).</span></span>

1. <span data-ttu-id="dd456-114">Einige Besprechungs-APIs, wie zum Beispiel, `GetParticipant` erfordern eine [bot-Registrierung und eine bot-APP-ID](../bots/how-to/create-a-bot-for-teams.md#with-an-azure-subscription) zum Generieren von auth-Token.</span><span class="sxs-lookup"><span data-stu-id="dd456-114">Some meeting APIs, such as `GetParticipant` will require a [bot registration and bot app ID](../bots/how-to/create-a-bot-for-teams.md#with-an-azure-subscription) to generate auth tokens.</span></span>

1. <span data-ttu-id="dd456-115">Entwickler müssen sich an die allgemeinen [Entwurfsrichtlinien für Teams-Registerkarten](../tabs/design/tabs.md) für Pre-und Post-Meeting-Szenarien sowie die [in-Meeting-Dialogfeld Richtlinien](design/designing-in-meeting-dialog.md) für das in-Meeting-Dialogfeld halten, das während einer Teambesprechung ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="dd456-115">Developers must adhere to general [Teams tab design guidelines](../tabs/design/tabs.md) for pre- and post-meeting scenarios as well as the [in-meeting dialog guidelines](design/designing-in-meeting-dialog.md) for in-meeting dialog triggered during a Teams meeting.</span></span>

## <a name="meeting-apps-api-reference"></a><span data-ttu-id="dd456-116">Besprechungs-apps-API-Referenz</span><span class="sxs-lookup"><span data-stu-id="dd456-116">Meeting apps API reference</span></span>

|<span data-ttu-id="dd456-117">API</span><span class="sxs-lookup"><span data-stu-id="dd456-117">API</span></span>|<span data-ttu-id="dd456-118">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="dd456-118">Description</span></span>|<span data-ttu-id="dd456-119">Anforderung</span><span class="sxs-lookup"><span data-stu-id="dd456-119">Request</span></span>|<span data-ttu-id="dd456-120">Source</span><span class="sxs-lookup"><span data-stu-id="dd456-120">Source</span></span>|
|---|---|----|---|
|<span data-ttu-id="dd456-121">**Getusercontext**</span><span class="sxs-lookup"><span data-stu-id="dd456-121">**GetUserContext**</span></span>| <span data-ttu-id="dd456-122">Abrufen von Kontextinformationen zum Anzeigen relevanter Inhalte auf einer Registerkarte Teams.</span><span class="sxs-lookup"><span data-stu-id="dd456-122">Get contextual information to display relevant content in a Teams tab.</span></span> |<span data-ttu-id="dd456-123">_**verläuft. GetContext (() => {/*...\* / } )*\*_</span><span class="sxs-lookup"><span data-stu-id="dd456-123">_**microsoftTeams.getContext( ( ) => {  /*...*/ } )**_</span></span>|<span data-ttu-id="dd456-124">Microsoft Teams-Client-SDK</span><span class="sxs-lookup"><span data-stu-id="dd456-124">Microsoft Teams client SDK</span></span>|
|<span data-ttu-id="dd456-125">**Getparticipant**</span><span class="sxs-lookup"><span data-stu-id="dd456-125">**GetParticipant**</span></span>|<span data-ttu-id="dd456-126">Mit dieser API kann ein bot eine Teilnehmer Information nach Besprechungs-ID und Teilnehmer-ID abrufen.</span><span class="sxs-lookup"><span data-stu-id="dd456-126">This API allows a bot to fetch a participant information by meeting id and participant id.</span></span>|<span data-ttu-id="dd456-127">**GET** _ **/V1/Meetings/{meetingId}/participants/{participantId} abrufen? Mandanten-Nr = {Mandanten** -Nr}_</span><span class="sxs-lookup"><span data-stu-id="dd456-127">**GET** _**/v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}**_</span></span> |<span data-ttu-id="dd456-128">Microsoft bot Framework SDK</span><span class="sxs-lookup"><span data-stu-id="dd456-128">Microsoft Bot Framework SDK</span></span>|
|<span data-ttu-id="dd456-129">**NotificationSignal**</span><span class="sxs-lookup"><span data-stu-id="dd456-129">**NotificationSignal**</span></span> |<span data-ttu-id="dd456-130">Besprechungs Signale werden über die folgende vorhandene Benachrichtigungs-API für Unterhaltungen (für Benutzer-bot-Chat) übermittelt.</span><span class="sxs-lookup"><span data-stu-id="dd456-130">Meeting signals will be delivered using the following existing conversation notification API (for user-bot chat).</span></span> <span data-ttu-id="dd456-131">Mit dieser API können Entwickler basierend auf der Endbenutzer Aktion signalisieren, dass eine Dialog Blase in einer Besprechung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="dd456-131">This API allows developers to signal based on end-user action to show-case an in-meeting dialog bubble.</span></span>|<span data-ttu-id="dd456-132">**Post** _ **/V3/Conversations/{conversationId}/Activities**_</span><span class="sxs-lookup"><span data-stu-id="dd456-132">**POST** _**/v3/conversations/{conversationId}/activities**_</span></span>|<span data-ttu-id="dd456-133">Microsoft bot Framework SDK</span><span class="sxs-lookup"><span data-stu-id="dd456-133">Microsoft Bot Framework SDK</span></span>|

### <a name="getusercontext"></a><span data-ttu-id="dd456-134">Getusercontext</span><span class="sxs-lookup"><span data-stu-id="dd456-134">GetUserContext</span></span>

<span data-ttu-id="dd456-135">Eine Anleitung zum Identifizieren und Abrufen von Kontextinformationen für die Registerkarteninhalte finden Sie in der Dokumentation zu [Get Context for your Teams](../tabs/how-to/access-teams-context.md#getting-context-by-using-the-microsoft-teams-javascript-library) .</span><span class="sxs-lookup"><span data-stu-id="dd456-135">Please refer to our [Get context for your Teams tab](../tabs/how-to/access-teams-context.md#getting-context-by-using-the-microsoft-teams-javascript-library) documentation for guidance on identifying and  retrieving contextual information for your tab content.</span></span> <span data-ttu-id="dd456-136">Im Rahmen der Erweiterbarkeit von Besprechungen wurde für die Antwort Nutzlast ein neuer Wert hinzugefügt:</span><span class="sxs-lookup"><span data-stu-id="dd456-136">As part of meetings extensibility, a new value has been added for the response payload:</span></span>

<span data-ttu-id="dd456-137">✔- **Besprechungs**-Nr: wird von einer Registerkarte bei der Ausführung im Besprechungs Kontext verwendet.</span><span class="sxs-lookup"><span data-stu-id="dd456-137">✔ **meetingId**: used by a tab when running in the meeting context.</span></span>

### <a name="getparticipant-api"></a><span data-ttu-id="dd456-138">Getparticipant-API</span><span class="sxs-lookup"><span data-stu-id="dd456-138">GetParticipant API</span></span>

> [!NOTE]
>
> * <span data-ttu-id="dd456-139">Sie sollten keine Teilnehmerrollen Zwischenspeichern, da der Besprechungsorganisator zu einem beliebigen Zeitpunkt eine Rolle ändern kann.</span><span class="sxs-lookup"><span data-stu-id="dd456-139">Do not cache participant roles since the meeting organizer can change a role at any point in time.</span></span>
>
> * <span data-ttu-id="dd456-140">Microsoft Teams unterstützt derzeit keine großen Verteilerlisten oder Dienstplan Größen von mehr als 350 Teilnehmern für die `GetParticipant` API.</span><span class="sxs-lookup"><span data-stu-id="dd456-140">Teams does not currently support large distribution lists or roster sizes of more than 350 participants for the `GetParticipant` API.</span></span>
>
> * <span data-ttu-id="dd456-141">Die Unterstützung für das bot Framework SDK wird in Kürze verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="dd456-141">Support for the Bot Framework SDK is coming soon.</span></span>

#### <a name="request"></a><span data-ttu-id="dd456-142">Anforderung</span><span class="sxs-lookup"><span data-stu-id="dd456-142">Request</span></span>

```http
GET /v3/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}
```

<span data-ttu-id="dd456-143">*Siehe* [bot Framework-API-Referenz](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="dd456-143">*See* the [Bot Framework API reference](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0&preserve-view=true).</span></span>

<!-- markdownlint-disable MD025 -->

<span data-ttu-id="dd456-144">**C#-Beispiel**</span><span class="sxs-lookup"><span data-stu-id="dd456-144">**C# Example**</span></span>

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
}
```

* * *
<!-- markdownlint-disable MD001 -->

#### <a name="query-parameters"></a><span data-ttu-id="dd456-145">Abfrageparameter</span><span class="sxs-lookup"><span data-stu-id="dd456-145">Query parameters</span></span>

<span data-ttu-id="dd456-146">**Besprechungs**-Nr.</span><span class="sxs-lookup"><span data-stu-id="dd456-146">**meetingId**.</span></span> <span data-ttu-id="dd456-147">Die Besprechungs-ID ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="dd456-147">The meeting identifier is required.</span></span>  
<span data-ttu-id="dd456-148">**Teilnehmer**-Nr.</span><span class="sxs-lookup"><span data-stu-id="dd456-148">**participantId**.</span></span> <span data-ttu-id="dd456-149">Die Teilnehmer-ID ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="dd456-149">The participant identifier is required.</span></span>  
<span data-ttu-id="dd456-150">**Mandanten**-Nr.</span><span class="sxs-lookup"><span data-stu-id="dd456-150">**tenantId**.</span></span> <span data-ttu-id="dd456-151">[Mandanten-ID](/onedrive/find-your-office-365-tenant-id) des Teilnehmers.</span><span class="sxs-lookup"><span data-stu-id="dd456-151">[Tenant id](/onedrive/find-your-office-365-tenant-id) of the participant.</span></span> <span data-ttu-id="dd456-152">Für Mandanten Benutzer erforderlich.</span><span class="sxs-lookup"><span data-stu-id="dd456-152">Required for tenant user.</span></span>

#### <a name="response-payload"></a><span data-ttu-id="dd456-153">Antwort Nutzlast</span><span class="sxs-lookup"><span data-stu-id="dd456-153">Response Payload</span></span>
<!-- markdownlint-disable MD036 -->

<span data-ttu-id="dd456-154">**meetingRole** kann *Organisator*, *Referent*oder *Teilnehmer*sein.</span><span class="sxs-lookup"><span data-stu-id="dd456-154">**meetingRole** can be *Organizer*, *Presenter*, or *Attendee*.</span></span>

<span data-ttu-id="dd456-155">**Beispiel 1**</span><span class="sxs-lookup"><span data-stu-id="dd456-155">**Example 1**</span></span>

```json
{
  "user":
  {
      "id": "29:1JKiJGPAX9TTxtGxhVo0wLx_zwzo-gG8Z-X03306vBwi9p-xMTEbDXsT6KH7-0kkTS8cD-2zkrsoV6f5WJ6_aYw",
      "aadObjectId": "6aebbad0-e5a5-424a-834a-20fb051f3c1a",
      "name": "Allan Deyoung",
      "givenName": "Allan",
      "surname": "Deyoung",
      "email": "Allan.Deyoung@microsoft.com",
      "userPrincipalName": "Allan.Deyoung@microsoft.com",
      "tenantId": "72f988bf-86f1-41af-91ab-2d7cd011db47",
  },
  "meeting":
  {
      "role ": "Presenter",
      "inMeeting":true
  },
  "conversation":
  {
      "id": "<conversation id>"
  }
}
```
#### <a name="response-codes"></a><span data-ttu-id="dd456-156">Antwort Codes</span><span class="sxs-lookup"><span data-stu-id="dd456-156">Response Codes</span></span>

<span data-ttu-id="dd456-157">**403**: die APP darf keine Teilnehmer Informationen erhalten.</span><span class="sxs-lookup"><span data-stu-id="dd456-157">**403**: the app is not allowed to get participant information.</span></span> <span data-ttu-id="dd456-158">Dies ist die häufigste Fehlerantwort und wird ausgelöst, wenn die APP nicht in der Besprechung installiert wird, beispielsweise wenn die APP vom mandantenadministrator deaktiviert oder während der Live-Website Minderung blockiert wird.</span><span class="sxs-lookup"><span data-stu-id="dd456-158">This will be the most common error response and is triggered when the app is not installed in the meeting such as when the app is disabled by tenant admin or blocked during live site mitigation.</span></span>  
<span data-ttu-id="dd456-159">**200**: Teilnehmer Informationen erfolgreich abgerufen</span><span class="sxs-lookup"><span data-stu-id="dd456-159">**200**: participant information successfully retrieved</span></span>  
<span data-ttu-id="dd456-160">**401**: Ungültiges Token</span><span class="sxs-lookup"><span data-stu-id="dd456-160">**401**: invalid token</span></span>  
<span data-ttu-id="dd456-161">**404**: die Besprechung ist nicht vorhanden, oder der Teilnehmer kann nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="dd456-161">**404**: the meeting doesn't exist or participant can’t be found.</span></span>

<!-- markdownlint-disable MD024 -->
### <a name="notificationsignal-api"></a><span data-ttu-id="dd456-162">NotificationSignal-API</span><span class="sxs-lookup"><span data-stu-id="dd456-162">NotificationSignal API</span></span>

> [!NOTE]
> <span data-ttu-id="dd456-163">Wenn ein in-Meeting-Dialogfeld aufgerufen wird, wird derselbe Inhalt auch als Chatnachricht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="dd456-163">When an in-meeting dialog is invoked, the same content will also be presented as a chat message.</span></span>

#### <a name="request"></a><span data-ttu-id="dd456-164">Anforderung</span><span class="sxs-lookup"><span data-stu-id="dd456-164">Request</span></span>

```http
POST /v3/conversations/{conversationId}/activities
```

#### <a name="query-parameters"></a><span data-ttu-id="dd456-165">Abfrageparameter</span><span class="sxs-lookup"><span data-stu-id="dd456-165">Query parameters</span></span>

<span data-ttu-id="dd456-166">**Conversation**-ID: der Konversationsbezeichner.</span><span class="sxs-lookup"><span data-stu-id="dd456-166">**conversationId**: The conversation identifier.</span></span> <span data-ttu-id="dd456-167">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="dd456-167">Required</span></span>

<span data-ttu-id="dd456-168">**completionBotId**: Dies ist die bot-ID.</span><span class="sxs-lookup"><span data-stu-id="dd456-168">**completionBotId**: This is the Bot ID.</span></span> <span data-ttu-id="dd456-169">Optional</span><span class="sxs-lookup"><span data-stu-id="dd456-169">Optional</span></span>

#### <a name="request-payload"></a><span data-ttu-id="dd456-170">Anforderungsnutzlast</span><span class="sxs-lookup"><span data-stu-id="dd456-170">Request Payload</span></span>

# <a name="json"></a>[<span data-ttu-id="dd456-171">Json</span><span class="sxs-lookup"><span data-stu-id="dd456-171">JSON</span></span>](#tab/json)

```json
{
    "type": "message",
    "text": "John Phillips assigned you a weekly todo",
    "summary": "Don't forget to meet with Marketing next week",
    "channelData": {
        "notification": {
            "alertInMeeting": true,
            "externalResourceUrl": "https://teams.microsoft.com/l/bubble/APP_ID?url=<TaskInfo.url>&height=<TaskInfo.height>&width=<TaskInfo.width>&title=<TaskInfo.title>&completionBotId=BOT_APP_ID"
        }
    },
    "replyToId": "1493070356924"
}
```

# <a name="cnet"></a>[<span data-ttu-id="dd456-172">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="dd456-172">C#/.NET</span></span>](#tab/dotnet)

```csharp
Activity activity = MessageFactory.Text("This is a meeting signal test");
MeetingNotification notification = new MeetingNotification
  {
    AlertInMeeting = true,
    ExternalResourceUrl = "https://teams.microsoft.com/l/bubble/APP_ID?url=<TaskInfo.url>&height=<TaskInfo.height>&width=<TaskInfo.width>&title=<TaskInfo.title>&completionBotId=BOT_APP_ID"
  };
activity.ChannelData = new TeamsChannelData
  {
    Notification = notification
  };
await turnContext.SendActivityAsync(activity).ConfigureAwait(false);
```

# <a name="javascript"></a>[<span data-ttu-id="dd456-173">JavaScript</span><span class="sxs-lookup"><span data-stu-id="dd456-173">JavaScript</span></span>](#tab/javascript)

```javascript

const replyActivity = MessageFactory.text('Hi'); // this could be an adaptive card instead
        replyActivity.channelData = {
            notification: {
                alertInMeeting: true,
                externalResourceUrl: 'https://teams.microsoft.com/l/bubble/APP_ID?url=<TaskInfo.url>&height=<TaskInfo.height>&width=<TaskInfo.width>&title=<TaskInfo.title>&completionBotId=BOT_APP_ID’
            }
        };
await context.sendActivity(replyActivity);
```

* * *

> [!IMPORTANT]
> <span data-ttu-id="dd456-174">Die URL in der Inhalts Blase (taskInfo-URL) muss in der Liste [gültiger Domänen](../resources/schema/manifest-schema.md#validdomains) enthalten sein, die im App-Manifest für Teams enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="dd456-174">The URL in the content bubble (taskInfo URL) must be included in the [valid domains](../resources/schema/manifest-schema.md#validdomains) list included in the Teams app manifest.</span></span>

#### <a name="response-codes"></a><span data-ttu-id="dd456-175">Antwort Codes</span><span class="sxs-lookup"><span data-stu-id="dd456-175">Response Codes</span></span>

<span data-ttu-id="dd456-176">**201**: Aktivität mit Signal wurde erfolgreich gesendet</span><span class="sxs-lookup"><span data-stu-id="dd456-176">**201**: activity with signal is successfully sent</span></span>  
<span data-ttu-id="dd456-177">**401**: Ungültiges Token</span><span class="sxs-lookup"><span data-stu-id="dd456-177">**401**: invalid token</span></span>  
<span data-ttu-id="dd456-178">**403**: die APP darf das Signal nicht senden.</span><span class="sxs-lookup"><span data-stu-id="dd456-178">**403**: the app is not allowed to send the signal.</span></span> <span data-ttu-id="dd456-179">In diesem Fall sollte die Nutzlast eine ausführlichere Fehlermeldung enthalten.</span><span class="sxs-lookup"><span data-stu-id="dd456-179">In this case, the payload should contain more detail error message.</span></span> <span data-ttu-id="dd456-180">Es kann viele Gründe geben: app, die vom mandantenadministrator deaktiviert, während einer Live-Standort Minderung blockiert wird, usw.</span><span class="sxs-lookup"><span data-stu-id="dd456-180">There can be many reasons: app disabled by tenant admin, blocked during live site mitigation, etc.</span></span>  
<span data-ttu-id="dd456-181">**404**: Besprechungs Chat nicht vorhanden</span><span class="sxs-lookup"><span data-stu-id="dd456-181">**404**: meeting chat doesn't exist</span></span>  

## <a name="enable-your-app-for-teams-meetings"></a><span data-ttu-id="dd456-182">Aktivieren Ihrer APP für Microsoft Teams-Besprechungen</span><span class="sxs-lookup"><span data-stu-id="dd456-182">Enable your app for Teams meetings</span></span>

### <a name="update-your-app-manifest"></a><span data-ttu-id="dd456-183">Aktualisieren des App-Manifests</span><span class="sxs-lookup"><span data-stu-id="dd456-183">Update your app manifest</span></span>

<span data-ttu-id="dd456-184">Die APP-Funktionen für Besprechungen werden in Ihrem App-Manifest über die **configurableTabs**  ->  -**Bereiche** und **Kontext** Arrays deklariert.</span><span class="sxs-lookup"><span data-stu-id="dd456-184">The meetings app capabilities are declared in your app manifest via the **configurableTabs** -> **scopes** and **context** arrays.</span></span> <span data-ttu-id="dd456-185">*Scope* definiert, an wen und in welchem *Kontext* definiert wird, wo Ihre app verfügbar sein wird.</span><span class="sxs-lookup"><span data-stu-id="dd456-185">*Scope* defines to whom and *context* defines where your app will be available.</span></span>

> [!NOTE]
> * <span data-ttu-id="dd456-186">Verwenden Sie das [Manifest-Schema für Entwicklervorschau](../resources/schema/manifest-schema-dev-preview.md) , um dieses in Ihrem App-Manifest zu testen.</span><span class="sxs-lookup"><span data-stu-id="dd456-186">Please use [Developer Preview manifest schema](../resources/schema/manifest-schema-dev-preview.md) to try this in your app manifest.</span></span>
> * <span data-ttu-id="dd456-187">Mobile Plattform unterstützt derzeit nur Manifest-Schema 1,6</span><span class="sxs-lookup"><span data-stu-id="dd456-187">Mobile Platform currently only support Manifest Schema 1.6</span></span>
> * <span data-ttu-id="dd456-188">Mobile Plattform unterstützt nur Registerkarten in vor-und nach Besprechungs Oberflächen.</span><span class="sxs-lookup"><span data-stu-id="dd456-188">Mobile Platform supports Tabs only in Pre and Post Meeting Surfaces.</span></span> <span data-ttu-id="dd456-189">Die in-Meeting-Erlebnisse (in-Meeting-Dialog und Tab) auf mobilen Geräten werden in Kürze verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="dd456-189">The In-meeting experiences (in-meeting dialog and tab) on mobile will be available soon</span></span>

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

### <a name="context-property"></a><span data-ttu-id="dd456-190">Context-Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="dd456-190">Context property</span></span>

<span data-ttu-id="dd456-191">Die Registerkarte `context` und die `scopes` Eigenschaften funktionieren in Harmonie, damit Sie bestimmen können, wo Ihre APP angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="dd456-191">The tab `context` and `scopes` properties work in harmony to allow you to determine where you want your app to appear.</span></span> <span data-ttu-id="dd456-192">Registerkarten im `team` `groupchat` Bereich oder können mehr als einen Kontext aufweisen.</span><span class="sxs-lookup"><span data-stu-id="dd456-192">Tabs in the `team` or `groupchat` scope can have more than one context.</span></span> <span data-ttu-id="dd456-193">Die möglichen Werte für die Context-Eigenschaft lauten wie folgt:</span><span class="sxs-lookup"><span data-stu-id="dd456-193">The possible values for the context property are as follows:</span></span>

* <span data-ttu-id="dd456-194">**channelTab**: eine Registerkarte in der Kopfzeile eines Team Kanals.</span><span class="sxs-lookup"><span data-stu-id="dd456-194">**channelTab**: a tab in the header of a team channel.</span></span>
* <span data-ttu-id="dd456-195">**privateChatTab**: eine Registerkarte in der Kopfzeile eines Gruppenchats zwischen einer Gruppe von Benutzern, die sich nicht im Kontext eines Teams oder einer Besprechung befinden.</span><span class="sxs-lookup"><span data-stu-id="dd456-195">**privateChatTab**: a tab in the header of a group chat between a set of users not in the context of a team or meeting.</span></span>
* <span data-ttu-id="dd456-196">**meetingChatTab**: eine Registerkarte in der Kopfzeile eines Gruppenchats zwischen einer Gruppe von Benutzern im Kontext einer geplanten Besprechung.</span><span class="sxs-lookup"><span data-stu-id="dd456-196">**meetingChatTab**: a tab in the header of a group chat between a set of users in the context of a scheduled meeting.</span></span>
* <span data-ttu-id="dd456-197">**meetingDetailsTab**: eine Registerkarte in der Kopfzeile der Ansicht "Besprechungsdetails" des Kalenders.</span><span class="sxs-lookup"><span data-stu-id="dd456-197">**meetingDetailsTab**: a tab in the header of the meeting details view of the calendar.</span></span>
* <span data-ttu-id="dd456-198">**meetingSidePanel**: ein in-Meeting-Bereich, der über den einheitlichen Balken geöffnet wird (u-Leiste).</span><span class="sxs-lookup"><span data-stu-id="dd456-198">**meetingSidePanel**: an in-meeting panel opened via the unified bar (u-bar).</span></span>

## <a name="configure-your-app-for-meeting-scenarios"></a><span data-ttu-id="dd456-199">Konfigurieren Ihrer APP für Besprechungs Szenarien</span><span class="sxs-lookup"><span data-stu-id="dd456-199">Configure your app for meeting scenarios</span></span>

> [!NOTE]
> <span data-ttu-id="dd456-200">Damit Ihre APP im Registerkarten Katalog sichtbar ist, muss Sie **konfigurierbare Registerkarten** und den **Gruppenchat Bereich**unterstützen.</span><span class="sxs-lookup"><span data-stu-id="dd456-200">For your app to be visible in the tab gallery it needs to **support configurable tabs** and the **group chat scope**.</span></span>

### <a name="pre-meeting"></a><span data-ttu-id="dd456-201">Pre-Meeting</span><span class="sxs-lookup"><span data-stu-id="dd456-201">Pre-meeting</span></span>

<span data-ttu-id="dd456-202">Benutzer mit Organizer-und/oder Presenter-Rollen fügen mithilfe der Schaltfläche Plus ➕ auf der Seite Besprechungs- **Chat** und Besprechungs **Details** Registerkarten zu einer Besprechung hinzu.</span><span class="sxs-lookup"><span data-stu-id="dd456-202">Users with organizer and/or presenter roles add tabs to a meeting using the plus ➕ button in the meeting **Chat** and meeting **details** pages.</span></span> <span data-ttu-id="dd456-203">Messaging Erweiterungen werden über das Menü Ellipsen/Überlauf hinzugefügt, &#x25CF;&#x25CF;&#x25CF; unterhalb des Bereichs zum Verfassen von Nachrichten im Chat angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="dd456-203">Messaging extensions are added to via the ellipses/overflow menu &#x25CF;&#x25CF;&#x25CF; located beneath the compose message area in the chat.</span></span> <span data-ttu-id="dd456-204">Bots werden mit der Taste "" zu einem Besprechungs Chat hinzugefügt **@** und die Option **Bots abrufen**ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="dd456-204">Bots are added to a meeting chat using the "**@**" key and selecting **Get bots**.</span></span>

<span data-ttu-id="dd456-205">✔ Die Benutzeridentität *muss* über die [Registerkarten SSO](../tabs/how-to/authentication/auth-aad-sso.md)bestätigt werden.</span><span class="sxs-lookup"><span data-stu-id="dd456-205">✔ The user identity *must* be confirmed via [Tabs SSO](../tabs/how-to/authentication/auth-aad-sso.md).</span></span> <span data-ttu-id="dd456-206">Nach dieser Authentifizierung kann die APP die Benutzerrolle über die getteilnehmer-API abrufen.</span><span class="sxs-lookup"><span data-stu-id="dd456-206">Following this authentication, the app can retrieve the user role via the GetParticipant API.</span></span>

 <span data-ttu-id="dd456-207">✔ Basierend auf der Benutzerrolle kann die App nun rollenspezifische Erlebnisse vorlegen.</span><span class="sxs-lookup"><span data-stu-id="dd456-207">✔ Based on the user role, the app will now have the capability to present role specific experiences.</span></span> <span data-ttu-id="dd456-208">Beispielsweise kann eine Polling-app nur Organisatoren und Referenten das Erstellen einer neuen Umfrage gestatten.</span><span class="sxs-lookup"><span data-stu-id="dd456-208">For example, a polling app can allow only organizers and presenters to create a new poll.</span></span>

> <span data-ttu-id="dd456-209">**Hinweis**: Rollenzuweisungen können geändert werden, während eine Besprechung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="dd456-209">**NOTE**: Role assignments can be changed while a meeting is in progress.</span></span>  <span data-ttu-id="dd456-210">*Siehe* [roles in a Teams Meeting](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).</span><span class="sxs-lookup"><span data-stu-id="dd456-210">*See* [Roles in a Teams meeting](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).</span></span> 

### <a name="in-meeting"></a><span data-ttu-id="dd456-211">In-Meeting</span><span class="sxs-lookup"><span data-stu-id="dd456-211">In-meeting</span></span>

#### <a name="sidepanel"></a><span data-ttu-id="dd456-212">**sidePanel**</span><span class="sxs-lookup"><span data-stu-id="dd456-212">**sidePanel**</span></span>

<span data-ttu-id="dd456-213">✔ In Ihrem App-Manifest fügen Sie **sidePanel** dem **Kontext** Array hinzu, wie oben beschrieben.</span><span class="sxs-lookup"><span data-stu-id="dd456-213">✔ In your app manifest add **sidePanel** to the **context** array as described above.</span></span>

<span data-ttu-id="dd456-214">✔ In der Besprechung als auch in allen Szenarien wird die app in einer in-Meeting-Registerkarte gerendert, die 320 Pixel groß in der Breite ist.</span><span class="sxs-lookup"><span data-stu-id="dd456-214">✔ In the meeting as well as in all scenarios, the app will be rendered in an in-meeting tab that is 320px in width.</span></span> <span data-ttu-id="dd456-215">Die Registerkarte muss dafür optimiert werden.</span><span class="sxs-lookup"><span data-stu-id="dd456-215">Your tab must be optimized for this.</span></span> <span data-ttu-id="dd456-216">*Siehe*, [framecontext-Schnittstelle](/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="dd456-216">*See*, [FrameContext interface](/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest&preserve-view=true)</span></span>

<span data-ttu-id="dd456-217">✔ Sie im Microsoft [Teams-SDK](../tabs/how-to/access-teams-context.md#user-context) nach, um die **benutzercontext** -API zu verwenden, um Anforderungen entsprechend weiterzuleiten.</span><span class="sxs-lookup"><span data-stu-id="dd456-217">✔Refer to the [Teams SDK](../tabs/how-to/access-teams-context.md#user-context) to use the **userContext** API to route requests accordingly.</span></span>

<span data-ttu-id="dd456-218">✔ Bezieht sich auf den Microsoft [Teams-Authentifizierungs Fluss für Registerkarten](../tabs/how-to/authentication/auth-flow-tab.md).</span><span class="sxs-lookup"><span data-stu-id="dd456-218">✔ Refer to the [Teams authentication flow for tabs](../tabs/how-to/authentication/auth-flow-tab.md).</span></span> <span data-ttu-id="dd456-219">Der Authentifizierungs Fluss für Registerkarten ähnelt dem auth-Fluss für Websites.</span><span class="sxs-lookup"><span data-stu-id="dd456-219">Authentication flow for tabs is very similar to the auth flow for websites.</span></span> <span data-ttu-id="dd456-220">Daher können Registerkarten OAuth 2,0 direkt verwenden.</span><span class="sxs-lookup"><span data-stu-id="dd456-220">Thus, tabs can use OAuth 2.0 directly.</span></span> <span data-ttu-id="dd456-221">*Siehe auch*, [Microsoft Identity Platform und OAuth 2,0-Autorisierungscode Fluss](/azure/active-directory/develop/v2-oauth2-auth-code-flow).</span><span class="sxs-lookup"><span data-stu-id="dd456-221">*See also*, [Microsoft identity platform and OAuth 2.0 authorization code flow](/azure/active-directory/develop/v2-oauth2-auth-code-flow).</span></span>

#### <a name="in-meeting-dialog"></a><span data-ttu-id="dd456-222">**in-Meeting-Dialog**</span><span class="sxs-lookup"><span data-stu-id="dd456-222">**in-meeting dialog**</span></span>

<span data-ttu-id="dd456-223">✔ Sie die Entwurfsrichtlinien für das [in-Meeting-Dialogfeld](design/designing-in-meeting-dialog.md)einhalten.</span><span class="sxs-lookup"><span data-stu-id="dd456-223">✔ You must adhere to the [in-meeting dialog design guidelines](design/designing-in-meeting-dialog.md).</span></span>

<span data-ttu-id="dd456-224">✔ Bezieht sich auf den Microsoft [Teams-Authentifizierungs Fluss für Registerkarten](../tabs/how-to/authentication/auth-flow-tab.md).</span><span class="sxs-lookup"><span data-stu-id="dd456-224">✔ Refer to the [Teams authentication flow for tabs](../tabs/how-to/authentication/auth-flow-tab.md).</span></span>

<span data-ttu-id="dd456-225">✔ Verwenden Sie die [Benachrichtigungs](/graph/api/resources/notifications-api-overview?view=graph-rest-beta&preserve-view=true) -API, um zu signalisieren, dass eine Blasen Benachrichtigung ausgelöst werden muss.</span><span class="sxs-lookup"><span data-stu-id="dd456-225">✔ Use the [notification](/graph/api/resources/notifications-api-overview?view=graph-rest-beta&preserve-view=true) API to signal that a bubble notification needs to be triggered.</span></span>

<span data-ttu-id="dd456-226">✔ Als Teil der Nutzlast der Benachrichtigungsanforderung enthalten die URL, in der der zu präsentierende Inhalt gehostet wird.</span><span class="sxs-lookup"><span data-stu-id="dd456-226">✔ As part of the notification request payload, include the URL where the content to be showcased is hosted.</span></span>

> [!NOTE]
>
> * <span data-ttu-id="dd456-227">Diese Benachrichtigungen sind in der Natur persistent.</span><span class="sxs-lookup"><span data-stu-id="dd456-227">These notifications are persistent in nature.</span></span> <span data-ttu-id="dd456-228">Sie müssen die [**submitTask ()**](../task-modules-and-cards/task-modules/task-modules-bots.md#submitting-the-result-of-a-task-module) -Funktion aufrufen, um automatisch zu entlassen, nachdem ein Benutzer eine Aktion in der-Webansicht durchführt.</span><span class="sxs-lookup"><span data-stu-id="dd456-228">You must invoke the [**submitTask()**](../task-modules-and-cards/task-modules/task-modules-bots.md#submitting-the-result-of-a-task-module) function to auto-dismiss after a user takes an action in the web-view.</span></span> <span data-ttu-id="dd456-229">Dies ist eine Voraussetzung für die APP-Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="dd456-229">This is a requirement for app submission.</span></span> <span data-ttu-id="dd456-230">*Siehe auch*Microsoft [Teams SDK: Aufgabenmodul](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="dd456-230">*See also*, [Teams SDK: task module](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true).</span></span>
>
> * <span data-ttu-id="dd456-231">Wenn Ihre APP anonyme Benutzer unterstützen soll, muss ihre anfängliche Anforderungsnutzlast auf die `from.id`  (ID der Benutzer)-Anforderungs Metadaten im `from` Objekt und nicht auf die `from.aadObjectId` Anforderungs Metadaten (Azure Active Directory ID des Benutzers) zurückgreifen.</span><span class="sxs-lookup"><span data-stu-id="dd456-231">If you want your app to support anonymous users, your initial invoke request payload must rely on the `from.id`  (ID of the user) request metadata in the `from` object, not the `from.aadObjectId` (Azure Active Directory ID of the user) request metadata.</span></span> <span data-ttu-id="dd456-232">*Weitere Informationen finden Sie unter* [Verwenden von Aufgaben Modulen in Registerkarten](../task-modules-and-cards/task-modules/task-modules-tabs.md) und [Erstellen und Senden des Aufgabenmoduls](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request).</span><span class="sxs-lookup"><span data-stu-id="dd456-232">*See* [Using task modules in tabs](../task-modules-and-cards/task-modules/task-modules-tabs.md) and [Create and send the task module](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request).</span></span>

### <a name="post-meeting"></a><span data-ttu-id="dd456-233">Nachbesprechung</span><span class="sxs-lookup"><span data-stu-id="dd456-233">Post-meeting</span></span>

<span data-ttu-id="dd456-234">Die Konfigurationen nach der Besprechung und vor der Besprechung sind äquivalent.</span><span class="sxs-lookup"><span data-stu-id="dd456-234">The post-meeting and pre-meeting configurations are equivalent.</span></span>

## <a name="meeting-app-sample"></a><span data-ttu-id="dd456-235">Beispiel für eine Besprechungs-App</span><span class="sxs-lookup"><span data-stu-id="dd456-235">Meeting app sample</span></span>

 > [!div class="nextstepaction"]
> [<span data-ttu-id="dd456-236">App für die Besprechungs Token-Generator</span><span class="sxs-lookup"><span data-stu-id="dd456-236">Meeting token generator app</span></span>](https://github.com/OfficeDev/microsoft-teams-sample-meetings-token)
