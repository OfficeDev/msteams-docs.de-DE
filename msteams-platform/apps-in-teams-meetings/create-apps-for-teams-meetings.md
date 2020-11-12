---
title: Apps für Teams-Besprechungen erstellen
author: laujan
description: Erstellen von Apps für Microsoft Teams-Besprechungen
ms.topic: conceptual
ms.author: lajanuar
keywords: Teams-apps-Besprechungen Benutzer Teilnehmer-Rollen-API
ms.openlocfilehash: d7dc812f715b6a7edbcc706946b8d80dd692daee
ms.sourcegitcommit: 0aeb60027f423d8ceff3b377db8c3efbb6da4d17
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/11/2020
ms.locfileid: "48997972"
---
# <a name="create-apps-for-teams-meetings-developer-preview"></a><span data-ttu-id="a76fa-104">Erstellen von Apps für Microsoft Teams-Besprechungen (Entwicklervorschau)</span><span class="sxs-lookup"><span data-stu-id="a76fa-104">Create apps for Teams meetings (Developer Preview)</span></span>

>[!IMPORTANT]
> <span data-ttu-id="a76fa-105">In der Entwicklervorschau von Microsoft Teams enthaltene Features werden nur für frühere Zugriffs-, Test-und Feedback Zwecke bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="a76fa-105">Features included in Microsoft Teams Developer Preview are provided for early-access, testing, and feedback purposes only.</span></span> <span data-ttu-id="a76fa-106">Sie werden möglicherweise geändert, bevor Sie in der öffentlichen Version verfügbar werden und sollten nicht in Produktionsanwendungen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="a76fa-106">They may undergo changes before becoming available in the public release and should not be used in production applications.</span></span>

## <a name="prerequisites-and-considerations"></a><span data-ttu-id="a76fa-107">Voraussetzungen und Überlegungen</span><span class="sxs-lookup"><span data-stu-id="a76fa-107">Prerequisites and considerations</span></span>

1. <span data-ttu-id="a76fa-108">Apps in Besprechungen erfordern grundlegende Kenntnisse der [Teams-App-Entwicklung](../overview.md).</span><span class="sxs-lookup"><span data-stu-id="a76fa-108">Apps in meetings require some basic knowledge of [Teams app development](../overview.md).</span></span> <span data-ttu-id="a76fa-109">Eine app in einer Besprechung kann aus [Registerkarten](../tabs/what-are-tabs.md), [Bots](../bots/what-are-bots.md)und [Messaging Erweiterungs](../messaging-extensions/what-are-messaging-extensions.md) Features bestehen und erfordert Aktualisierungen des Teams-APP- [Manifests](#update-your-app-manifest) , um anzugeben, dass die APP für Besprechungen zur Verfügung steht.</span><span class="sxs-lookup"><span data-stu-id="a76fa-109">An app in a meeting can comprise of [tabs](../tabs/what-are-tabs.md), [bots](../bots/what-are-bots.md), and [messaging extensions](../messaging-extensions/what-are-messaging-extensions.md) features and will require updates to the Teams [app manifest](#update-your-app-manifest) to indicate that the app is available for meetings</span></span>

1. <span data-ttu-id="a76fa-110">Damit Ihre APP im Besprechungs Lebenszyklus als Registerkarte funktioniert, muss Sie konfigurierbare Registerkarten im [Groupchat-Bereich](../resources/schema/manifest-schema.md#configurabletabs)unterstützen.</span><span class="sxs-lookup"><span data-stu-id="a76fa-110">For your app to function in the meeting lifecycle as a tab, it must support configurable tabs in the [groupchat scope](../resources/schema/manifest-schema.md#configurabletabs).</span></span> <span data-ttu-id="a76fa-111">*Weitere Informationen finden Sie unter* [Erweitern Ihrer Teams-App mit einer benutzerdefinierten Registerkarte](../tabs/how-to/add-tab.md). Durch die Unterstützung des `groupchat` Bereichs wird Ihre APP in [Besprechungen vor](teams-apps-in-meetings.md#pre-meeting-app-experience) und [nach](teams-apps-in-meetings.md#post-meeting-app-experience) dem Chatten aktiviert.</span><span class="sxs-lookup"><span data-stu-id="a76fa-111">*See* [Extend your Teams app with a custom tab](../tabs/how-to/add-tab.md). Supporting the `groupchat` scope will enable your app in [pre-meeting](teams-apps-in-meetings.md#pre-meeting-app-experience) and [post-meeting](teams-apps-in-meetings.md#post-meeting-app-experience) chats.</span></span>

1. <span data-ttu-id="a76fa-112">Die URL-Parameter der Besprechungs-API erfordern möglicherweise, `meetingId` `userId` und die [Mandanten](/onedrive/find-your-office-365-tenant-id) -Nr sind im Rahmen des Teams-Client-SDK und der Bot-Aktivität verfügbar.</span><span class="sxs-lookup"><span data-stu-id="a76fa-112">Meeting API URL parameters may require `meetingId`, `userId`, and the [tenantId](/onedrive/find-your-office-365-tenant-id) These are available as part of the Teams Client SDK and bot activity.</span></span> <span data-ttu-id="a76fa-113">Außerdem können zuverlässige Informationen für Benutzer-ID und Mandanten-ID mithilfe der [Registerkarten-SSO-Authentifizierung](../tabs/how-to/authentication/auth-aad-sso.md)abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="a76fa-113">Additionally, reliable information for user ID and tenant ID can be retrieved using [Tab SSO authentication](../tabs/how-to/authentication/auth-aad-sso.md).</span></span>

1. <span data-ttu-id="a76fa-114">Einige Besprechungs-APIs, wie zum Beispiel, `GetParticipant` erfordern eine [bot-Registrierung und eine bot-APP-ID](../bots/how-to/create-a-bot-for-teams.md#with-an-azure-subscription) zum Generieren von auth-Token.</span><span class="sxs-lookup"><span data-stu-id="a76fa-114">Some meeting APIs, such as `GetParticipant` will require a [bot registration and bot app ID](../bots/how-to/create-a-bot-for-teams.md#with-an-azure-subscription) to generate auth tokens.</span></span>

1. <span data-ttu-id="a76fa-115">Als Entwickler müssen Sie sich an die allgemeinen [Entwurfsrichtlinien für Teams-Registerkarten](../tabs/design/tabs.md) für vor-und nach Besprechungen sowie an die [in-Meeting-Dialogfeld Richtlinien](design/designing-in-meeting-dialog.md) für das in-Meeting-Dialogfeld halten, das während einer Teams-Besprechung ausgelöst wurde.</span><span class="sxs-lookup"><span data-stu-id="a76fa-115">As a developer, you must adhere to general [Teams tab design guidelines](../tabs/design/tabs.md) for pre- and post-meeting scenarios as well as the [in-meeting dialog guidelines](design/designing-in-meeting-dialog.md) for in-meeting dialog triggered during a Teams meeting.</span></span>

1. <span data-ttu-id="a76fa-116">Beachten Sie, dass die app in der Regel auf dem neuesten Stand sein muss, damit Ihre APP in Echtzeit aktualisiert werden kann, wenn Sie auf den Ereignis Aktivitäten in der Besprechung basiert.</span><span class="sxs-lookup"><span data-stu-id="a76fa-116">Please note that in order for your app to be updated in real-time, it must be up-to-date based on event activities in the meeting.</span></span> <span data-ttu-id="a76fa-117">Diese Ereignisse können sich innerhalb des in-Meeting-Dialogs befinden (siehe completion- `bot Id` Parameter in `Notification Signal API` ) und andere Oberflächen im gesamten Besprechungs Lebenszyklus.</span><span class="sxs-lookup"><span data-stu-id="a76fa-117">These events can be within the in-meeting dialog (refer to completion `bot Id` parameter in `Notification Signal API`) and other surfaces across the meeting lifecycle</span></span>

## <a name="meeting-apps-api-reference"></a><span data-ttu-id="a76fa-118">Besprechungs-apps-API-Referenz</span><span class="sxs-lookup"><span data-stu-id="a76fa-118">Meeting apps API reference</span></span>

|<span data-ttu-id="a76fa-119">API</span><span class="sxs-lookup"><span data-stu-id="a76fa-119">API</span></span>|<span data-ttu-id="a76fa-120">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a76fa-120">Description</span></span>|<span data-ttu-id="a76fa-121">Anforderung</span><span class="sxs-lookup"><span data-stu-id="a76fa-121">Request</span></span>|<span data-ttu-id="a76fa-122">Quelle</span><span class="sxs-lookup"><span data-stu-id="a76fa-122">Source</span></span>|
|---|---|----|---|
|<span data-ttu-id="a76fa-123">**Getusercontext**</span><span class="sxs-lookup"><span data-stu-id="a76fa-123">**GetUserContext**</span></span>| <span data-ttu-id="a76fa-124">Abrufen von Kontextinformationen zum Anzeigen relevanter Inhalte auf einer Registerkarte Teams.</span><span class="sxs-lookup"><span data-stu-id="a76fa-124">Get contextual information to display relevant content in a Teams tab.</span></span> |<span data-ttu-id="a76fa-125">_**verläuft. GetContext (() => {/ *...* / } )**_</span><span class="sxs-lookup"><span data-stu-id="a76fa-125">_**microsoftTeams.getContext( ( ) => {  / *...* / } )**_</span></span>|<span data-ttu-id="a76fa-126">Microsoft Teams-Client-SDK</span><span class="sxs-lookup"><span data-stu-id="a76fa-126">Microsoft Teams client SDK</span></span>|
|<span data-ttu-id="a76fa-127">**Getparticipant**</span><span class="sxs-lookup"><span data-stu-id="a76fa-127">**GetParticipant**</span></span>|<span data-ttu-id="a76fa-128">Mit dieser API kann ein bot eine Teilnehmer Information nach Besprechungs-ID und Teilnehmer-ID abrufen.</span><span class="sxs-lookup"><span data-stu-id="a76fa-128">This API allows a bot to fetch a participant information by meeting id and participant id.</span></span>|<span data-ttu-id="a76fa-129">**GET** _**/V1/Meetings/{meetingId}/participants/{participantId} abrufen? Mandanten-Nr = {Mandanten** -Nr}_</span><span class="sxs-lookup"><span data-stu-id="a76fa-129">**GET** _**/v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}**_</span></span> |<span data-ttu-id="a76fa-130">Microsoft bot Framework SDK</span><span class="sxs-lookup"><span data-stu-id="a76fa-130">Microsoft Bot Framework SDK</span></span>|
|<span data-ttu-id="a76fa-131">**NotificationSignal**</span><span class="sxs-lookup"><span data-stu-id="a76fa-131">**NotificationSignal**</span></span> |<span data-ttu-id="a76fa-132">Besprechungs Signale werden über die folgende vorhandene Benachrichtigungs-API für Unterhaltungen (für Benutzer-bot-Chat) übermittelt.</span><span class="sxs-lookup"><span data-stu-id="a76fa-132">Meeting signals will be delivered using the following existing conversation notification API (for user-bot chat).</span></span> <span data-ttu-id="a76fa-133">Mit dieser API können Entwickler basierend auf der Endbenutzer Aktion signalisieren, dass eine Dialog Blase in einer Besprechung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="a76fa-133">This API allows developers to signal based on end-user action to show-case an in-meeting dialog bubble.</span></span>|<span data-ttu-id="a76fa-134">**Post** _**/V3/Conversations/{conversationId}/Activities**_</span><span class="sxs-lookup"><span data-stu-id="a76fa-134">**POST** _**/v3/conversations/{conversationId}/activities**_</span></span>|<span data-ttu-id="a76fa-135">Microsoft bot Framework SDK</span><span class="sxs-lookup"><span data-stu-id="a76fa-135">Microsoft Bot Framework SDK</span></span>|

### <a name="getusercontext"></a><span data-ttu-id="a76fa-136">Getusercontext</span><span class="sxs-lookup"><span data-stu-id="a76fa-136">GetUserContext</span></span>

<span data-ttu-id="a76fa-137">Eine Anleitung zum Identifizieren und Abrufen von Kontextinformationen für die Registerkarteninhalte finden Sie in der Dokumentation zu [Get Context for your Teams](../tabs/how-to/access-teams-context.md#getting-context-by-using-the-microsoft-teams-javascript-library) .</span><span class="sxs-lookup"><span data-stu-id="a76fa-137">Please refer to our [Get context for your Teams tab](../tabs/how-to/access-teams-context.md#getting-context-by-using-the-microsoft-teams-javascript-library) documentation for guidance on identifying and  retrieving contextual information for your tab content.</span></span> <span data-ttu-id="a76fa-138">Im Rahmen der Erweiterbarkeit von Besprechungen wurde für die Antwort Nutzlast ein neuer Wert hinzugefügt:</span><span class="sxs-lookup"><span data-stu-id="a76fa-138">As part of meetings extensibility, a new value has been added for the response payload:</span></span>

<span data-ttu-id="a76fa-139">✔- **Besprechungs** -Nr: wird von einer Registerkarte bei der Ausführung im Besprechungs Kontext verwendet.</span><span class="sxs-lookup"><span data-stu-id="a76fa-139">✔ **meetingId** : used by a tab when running in the meeting context.</span></span>

### <a name="getparticipant-api"></a><span data-ttu-id="a76fa-140">Getparticipant-API</span><span class="sxs-lookup"><span data-stu-id="a76fa-140">GetParticipant API</span></span>

> [!NOTE]
>
> * <span data-ttu-id="a76fa-141">Sie sollten keine Teilnehmerrollen Zwischenspeichern, da der Besprechungsorganisator zu einem beliebigen Zeitpunkt eine Rolle ändern kann.</span><span class="sxs-lookup"><span data-stu-id="a76fa-141">Do not cache participant roles since the meeting organizer can change a role at any point in time.</span></span>
>
> * <span data-ttu-id="a76fa-142">Microsoft Teams unterstützt derzeit keine großen Verteilerlisten oder Dienstplan Größen von mehr als 350 Teilnehmern für die `GetParticipant` API.</span><span class="sxs-lookup"><span data-stu-id="a76fa-142">Teams does not currently support large distribution lists or roster sizes of more than 350 participants for the `GetParticipant` API.</span></span>
>
> * <span data-ttu-id="a76fa-143">Die Unterstützung für das bot Framework SDK wird in Kürze verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="a76fa-143">Support for the Bot Framework SDK is coming soon.</span></span>


#### <a name="request"></a><span data-ttu-id="a76fa-144">Anforderung</span><span class="sxs-lookup"><span data-stu-id="a76fa-144">Request</span></span>

```http
GET /v3/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}
```

<span data-ttu-id="a76fa-145">*Siehe* [bot Framework-API-Referenz](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="a76fa-145">*See* the [Bot Framework API reference](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0&preserve-view=true).</span></span>

<!-- markdownlint-disable MD025 -->

<span data-ttu-id="a76fa-146">**C#-Beispiel**</span><span class="sxs-lookup"><span data-stu-id="a76fa-146">**C# Example**</span></span>

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

#### <a name="query-parameters"></a><span data-ttu-id="a76fa-147">Abfrageparameter</span><span class="sxs-lookup"><span data-stu-id="a76fa-147">Query parameters</span></span>

|<span data-ttu-id="a76fa-148">Wert</span><span class="sxs-lookup"><span data-stu-id="a76fa-148">Value</span></span>|<span data-ttu-id="a76fa-149">Typ</span><span class="sxs-lookup"><span data-stu-id="a76fa-149">Type</span></span>|<span data-ttu-id="a76fa-150">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="a76fa-150">Required</span></span>|<span data-ttu-id="a76fa-151">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a76fa-151">Description</span></span>|
|---|---|----|---|
|<span data-ttu-id="a76fa-152">**meetingId**</span><span class="sxs-lookup"><span data-stu-id="a76fa-152">**meetingId**</span></span>| <span data-ttu-id="a76fa-153">string</span><span class="sxs-lookup"><span data-stu-id="a76fa-153">string</span></span> | <span data-ttu-id="a76fa-154">Ja</span><span class="sxs-lookup"><span data-stu-id="a76fa-154">Yes</span></span> | <span data-ttu-id="a76fa-155">Die Besprechungs-ID ist über bot Invoke und Microsoft Teams Client SDK verfügbar.</span><span class="sxs-lookup"><span data-stu-id="a76fa-155">The meeting identifier is available via Bot Invoke and Teams Client SDK.</span></span>|
|<span data-ttu-id="a76fa-156">**Teilnehmer-Nr**</span><span class="sxs-lookup"><span data-stu-id="a76fa-156">**participantId**</span></span>| <span data-ttu-id="a76fa-157">string</span><span class="sxs-lookup"><span data-stu-id="a76fa-157">string</span></span> | <span data-ttu-id="a76fa-158">Ja</span><span class="sxs-lookup"><span data-stu-id="a76fa-158">Yes</span></span> | <span data-ttu-id="a76fa-159">Dieses Feld ist die Benutzer-ID und steht in der Registerkarte "SSO", im bot-Invoke und im Microsoft Teams-Client-SDK zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="a76fa-159">This field is the User ID and it is available in Tab SSO, Bot Invoke, and Teams Client SDK.</span></span> <span data-ttu-id="a76fa-160">Die Registerkarte SSO wird dringend empfohlen.</span><span class="sxs-lookup"><span data-stu-id="a76fa-160">Tab SSO is highly recommended</span></span>|
|<span data-ttu-id="a76fa-161">**tenantId**</span><span class="sxs-lookup"><span data-stu-id="a76fa-161">**tenantId**</span></span>| <span data-ttu-id="a76fa-162">string</span><span class="sxs-lookup"><span data-stu-id="a76fa-162">string</span></span> | <span data-ttu-id="a76fa-163">Ja</span><span class="sxs-lookup"><span data-stu-id="a76fa-163">Yes</span></span> | <span data-ttu-id="a76fa-164">Dies ist für Mandanten Benutzer erforderlich.</span><span class="sxs-lookup"><span data-stu-id="a76fa-164">This required for tenant users.</span></span> <span data-ttu-id="a76fa-165">Sie ist in Tab SSO, bot Invoke und Microsoft Teams Client SDK verfügbar.</span><span class="sxs-lookup"><span data-stu-id="a76fa-165">It is available in Tab SSO, Bot Invoke, and Teams Client SDK.</span></span> <span data-ttu-id="a76fa-166">Die Registerkarte SSO wird dringend empfohlen.</span><span class="sxs-lookup"><span data-stu-id="a76fa-166">Tab SSO is highly recommended</span></span>|

#### <a name="response-payload"></a><span data-ttu-id="a76fa-167">Antwort Nutzlast</span><span class="sxs-lookup"><span data-stu-id="a76fa-167">Response Payload</span></span>
<!-- markdownlint-disable MD036 -->

<span data-ttu-id="a76fa-168">**Rolle** unter "Besprechung" kann *Organisator* , *Referent* oder *Teilnehmer* sein.</span><span class="sxs-lookup"><span data-stu-id="a76fa-168">**role** under "meeting" can be *Organizer* , *Presenter* , or *Attendee*.</span></span>

<span data-ttu-id="a76fa-169">**Beispiel 1**</span><span class="sxs-lookup"><span data-stu-id="a76fa-169">**Example 1**</span></span>

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
      "userRole": "user"
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
#### <a name="response-codes"></a><span data-ttu-id="a76fa-170">Antwort Codes</span><span class="sxs-lookup"><span data-stu-id="a76fa-170">Response Codes</span></span>

<span data-ttu-id="a76fa-171">**403** : die APP darf keine Teilnehmer Informationen erhalten.</span><span class="sxs-lookup"><span data-stu-id="a76fa-171">**403** : The app is not allowed to get participant information.</span></span> <span data-ttu-id="a76fa-172">Dies ist die häufigste Fehlerantwort und wird ausgelöst, wenn die APP nicht in der Besprechung installiert ist, beispielsweise wenn Sie vom mandantenadministrator deaktiviert oder während einer Live-Websitemigration blockiert wird.</span><span class="sxs-lookup"><span data-stu-id="a76fa-172">This will be the most common error response and is triggered when the app is not installed in the meeting such as when it is disabled by tenant admin or blocked during live site migration.</span></span>  
<span data-ttu-id="a76fa-173">**200** : Teilnehmer Informationen erfolgreich abgerufen.</span><span class="sxs-lookup"><span data-stu-id="a76fa-173">**200** : Participant information successfully retrieved.</span></span>  
<span data-ttu-id="a76fa-174">**401** : Ungültiges Token.</span><span class="sxs-lookup"><span data-stu-id="a76fa-174">**401** : Invalid token.</span></span>  
<span data-ttu-id="a76fa-175">**404** : Teilnehmer kann nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="a76fa-175">**404** : Participant cannot be found.</span></span> 
<span data-ttu-id="a76fa-176">**500** : die Besprechung ist entweder abgelaufen (mehr als 60 Tage seit der Beendigung der Besprechung) oder der Teilnehmer verfügt nicht über die Berechtigungen basierend auf seiner Rolle.</span><span class="sxs-lookup"><span data-stu-id="a76fa-176">**500** : The meeting is either expired (more than 60 days since the meeting ended) or the participant does not have permissions based on their role.</span></span>

<span data-ttu-id="a76fa-177">**Bald verfügbar**</span><span class="sxs-lookup"><span data-stu-id="a76fa-177">**Coming Soon**</span></span>

<span data-ttu-id="a76fa-178">**404** : die Besprechung ist entweder abgelaufen oder der Teilnehmer kann nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="a76fa-178">**404** : the meeting has either expired or participant cannot be found.</span></span> 

<!-- markdownlint-disable MD024 -->
### <a name="notificationsignal-api"></a><span data-ttu-id="a76fa-179">NotificationSignal-API</span><span class="sxs-lookup"><span data-stu-id="a76fa-179">NotificationSignal API</span></span>

> [!NOTE]
> <span data-ttu-id="a76fa-180">Wenn ein in-Meeting-Dialogfeld aufgerufen wird, wird derselbe Inhalt auch als Chatnachricht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a76fa-180">When an in-meeting dialog is invoked, the same content will also be presented as a chat message.</span></span>

#### <a name="request"></a><span data-ttu-id="a76fa-181">Anforderung</span><span class="sxs-lookup"><span data-stu-id="a76fa-181">Request</span></span>

```http
POST /v3/conversations/{conversationId}/activities
```

#### <a name="query-parameters"></a><span data-ttu-id="a76fa-182">Abfrageparameter</span><span class="sxs-lookup"><span data-stu-id="a76fa-182">Query parameters</span></span>

|<span data-ttu-id="a76fa-183">Wert</span><span class="sxs-lookup"><span data-stu-id="a76fa-183">Value</span></span>|<span data-ttu-id="a76fa-184">Typ</span><span class="sxs-lookup"><span data-stu-id="a76fa-184">Type</span></span>|<span data-ttu-id="a76fa-185">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="a76fa-185">Required</span></span>|<span data-ttu-id="a76fa-186">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a76fa-186">Description</span></span>|
|---|---|----|---|
|<span data-ttu-id="a76fa-187">**conversationId**</span><span class="sxs-lookup"><span data-stu-id="a76fa-187">**conversationId**</span></span>| <span data-ttu-id="a76fa-188">string</span><span class="sxs-lookup"><span data-stu-id="a76fa-188">string</span></span> | <span data-ttu-id="a76fa-189">Ja</span><span class="sxs-lookup"><span data-stu-id="a76fa-189">Yes</span></span> | <span data-ttu-id="a76fa-190">Die Konversations-ID ist im Rahmen von bot Invoke verfügbar</span><span class="sxs-lookup"><span data-stu-id="a76fa-190">The conversation identifier is available as part of bot invoke</span></span> |

#### <a name="request-payload"></a><span data-ttu-id="a76fa-191">Anforderungsnutzlast</span><span class="sxs-lookup"><span data-stu-id="a76fa-191">Request Payload</span></span>

> [!NOTE]
>
> *  <span data-ttu-id="a76fa-192">In der angeforderten Nutzlast unten `completionBotId` ist der Parameter des-Parameters `externalResourceUrl` ein optional.</span><span class="sxs-lookup"><span data-stu-id="a76fa-192">In the requested payload below, the `completionBotId` parameter of the `externalResourceUrl`is an optional.</span></span> <span data-ttu-id="a76fa-193">Es ist das `Bot ID` , das im Manifest deklariert wird.</span><span class="sxs-lookup"><span data-stu-id="a76fa-193">It is the `Bot ID` that is declared in the manifest.</span></span> <span data-ttu-id="a76fa-194">Der bot erhält ein Result-Objekt.</span><span class="sxs-lookup"><span data-stu-id="a76fa-194">The bot will receive a result object.</span></span>
> * <span data-ttu-id="a76fa-195">Die externalResourceUrl-Parameter width und Height müssen in Pixel angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="a76fa-195">The externalResourceUrl width and height parameters must be in pixels.</span></span> <span data-ttu-id="a76fa-196">Lesen Sie die [Entwurfsrichtlinien](design/designing-in-meeting-dialog.md) , um sicherzustellen, dass sich die Dimensionen innerhalb der zulässigen Grenzen befinden.</span><span class="sxs-lookup"><span data-stu-id="a76fa-196">Refer to the [design guidelines](design/designing-in-meeting-dialog.md) to ensure the dimensions are within the allowed limits.</span></span>
> * <span data-ttu-id="a76fa-197">Die URL ist die Seite, die als `<iframe>` innerhalb des in-Meeting-Dialogs geladen wird.</span><span class="sxs-lookup"><span data-stu-id="a76fa-197">The URL is the page loaded as an `<iframe>` inside the in-meeting dialog.</span></span> <span data-ttu-id="a76fa-198">Die Domäne der URL muss sich in Ihrem App-Manifest im APP- `validDomains` Array befinden.</span><span class="sxs-lookup"><span data-stu-id="a76fa-198">The URL's domain must be in the app's `validDomains` array in your app manifest.</span></span>


# <a name="json"></a>[<span data-ttu-id="a76fa-199">Json</span><span class="sxs-lookup"><span data-stu-id="a76fa-199">JSON</span></span>](#tab/json)

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

# <a name="cnet"></a>[<span data-ttu-id="a76fa-200">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="a76fa-200">C#/.NET</span></span>](#tab/dotnet)

```csharp
Activity activity = MessageFactory.Text("This is a meeting signal test");
MeetingNotification notification = new MeetingNotification
  {
    AlertInMeeting = true,
    ExternalResourceUrl = "https://teams.microsoft.com/l/bubble/APP_ID?url=<url>&height=<height>&width=<width>&title=<title>&completionBotId=BOT_APP_ID"
  };
activity.ChannelData = new TeamsChannelData
  {
    Notification = notification
  };
await turnContext.SendActivityAsync(activity).ConfigureAwait(false);
```

# <a name="javascript"></a>[<span data-ttu-id="a76fa-201">JavaScript</span><span class="sxs-lookup"><span data-stu-id="a76fa-201">JavaScript</span></span>](#tab/javascript)

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
> <span data-ttu-id="a76fa-202">Die URL in der Inhalts Blase (taskInfo-URL) muss in der Liste [gültiger Domänen](../resources/schema/manifest-schema.md#validdomains) enthalten sein, die im App-Manifest für Teams enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="a76fa-202">The URL in the content bubble (taskInfo URL) must be included in the [valid domains](../resources/schema/manifest-schema.md#validdomains) list included in the Teams app manifest.</span></span>

#### <a name="response-codes"></a><span data-ttu-id="a76fa-203">Antwort Codes</span><span class="sxs-lookup"><span data-stu-id="a76fa-203">Response Codes</span></span>

<span data-ttu-id="a76fa-204">**201** : Aktivität mit Signal wurde erfolgreich gesendet</span><span class="sxs-lookup"><span data-stu-id="a76fa-204">**201** : activity with signal is successfully sent</span></span>  
<span data-ttu-id="a76fa-205">**401** : Ungültiges Token</span><span class="sxs-lookup"><span data-stu-id="a76fa-205">**401** : invalid token</span></span>  
<span data-ttu-id="a76fa-206">**403** : die APP darf das Signal nicht senden.</span><span class="sxs-lookup"><span data-stu-id="a76fa-206">**403** : the app is not allowed to send the signal.</span></span> <span data-ttu-id="a76fa-207">In diesem Fall sollte die Nutzlast eine ausführlichere Fehlermeldung enthalten.</span><span class="sxs-lookup"><span data-stu-id="a76fa-207">In this case, the payload should contain more detail error message.</span></span> <span data-ttu-id="a76fa-208">Es kann viele Gründe geben: app, die vom mandantenadministrator deaktiviert, während einer Live-Standort Minderung blockiert wird, usw.</span><span class="sxs-lookup"><span data-stu-id="a76fa-208">There can be many reasons: app disabled by tenant admin, blocked during live site mitigation, etc.</span></span>  
<span data-ttu-id="a76fa-209">**404** : Besprechungs Chat nicht vorhanden</span><span class="sxs-lookup"><span data-stu-id="a76fa-209">**404** : meeting chat doesn't exist</span></span>  

## <a name="enable-your-app-for-teams-meetings"></a><span data-ttu-id="a76fa-210">Aktivieren Ihrer APP für Microsoft Teams-Besprechungen</span><span class="sxs-lookup"><span data-stu-id="a76fa-210">Enable your app for Teams meetings</span></span>

### <a name="update-your-app-manifest"></a><span data-ttu-id="a76fa-211">Aktualisieren des App-Manifests</span><span class="sxs-lookup"><span data-stu-id="a76fa-211">Update your app manifest</span></span>

<span data-ttu-id="a76fa-212">Die APP-Funktionen für Besprechungen werden in Ihrem App-Manifest über die **configurableTabs**  ->  - **Bereiche** und **Kontext** Arrays deklariert.</span><span class="sxs-lookup"><span data-stu-id="a76fa-212">The meetings app capabilities are declared in your app manifest via the **configurableTabs** -> **scopes** and **context** arrays.</span></span> <span data-ttu-id="a76fa-213">*Scope* definiert, an wen und in welchem *Kontext* definiert wird, wo Ihre app verfügbar sein wird.</span><span class="sxs-lookup"><span data-stu-id="a76fa-213">*Scope* defines to whom and *context* defines where your app will be available.</span></span>

> [!NOTE]
> * <span data-ttu-id="a76fa-214">Verwenden Sie das [Manifest-Schema für Entwicklervorschau](../resources/schema/manifest-schema-dev-preview.md) , um dieses in Ihrem App-Manifest zu testen.</span><span class="sxs-lookup"><span data-stu-id="a76fa-214">Please use [Developer Preview manifest schema](../resources/schema/manifest-schema-dev-preview.md) to try this in your app manifest.</span></span>

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

### <a name="context-property"></a><span data-ttu-id="a76fa-215">Context-Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="a76fa-215">Context property</span></span>

<span data-ttu-id="a76fa-216">Die Registerkarte `context` und die `scopes` Eigenschaften funktionieren in Harmonie, damit Sie bestimmen können, wo Ihre APP angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="a76fa-216">The tab `context` and `scopes` properties work in harmony to allow you to determine where you want your app to appear.</span></span> <span data-ttu-id="a76fa-217">Registerkarten im `team` `groupchat` Bereich oder können mehr als einen Kontext aufweisen.</span><span class="sxs-lookup"><span data-stu-id="a76fa-217">Tabs in the `team` or `groupchat` scope can have more than one context.</span></span> <span data-ttu-id="a76fa-218">Die möglichen Werte für die Context-Eigenschaft lauten wie folgt:</span><span class="sxs-lookup"><span data-stu-id="a76fa-218">The possible values for the context property are as follows:</span></span>

* <span data-ttu-id="a76fa-219">**channelTab** : eine Registerkarte in der Kopfzeile eines Team Kanals.</span><span class="sxs-lookup"><span data-stu-id="a76fa-219">**channelTab** : a tab in the header of a team channel.</span></span>
* <span data-ttu-id="a76fa-220">**privateChatTab** : eine Registerkarte in der Kopfzeile eines Gruppenchats zwischen einer Gruppe von Benutzern, die sich nicht im Kontext eines Teams oder einer Besprechung befinden.</span><span class="sxs-lookup"><span data-stu-id="a76fa-220">**privateChatTab** : a tab in the header of a group chat between a set of users not in the context of a team or meeting.</span></span>
* <span data-ttu-id="a76fa-221">**meetingChatTab** : eine Registerkarte in der Kopfzeile eines Gruppenchats zwischen einer Gruppe von Benutzern im Kontext einer geplanten Besprechung.</span><span class="sxs-lookup"><span data-stu-id="a76fa-221">**meetingChatTab** : a tab in the header of a group chat between a set of users in the context of a scheduled meeting.</span></span>
* <span data-ttu-id="a76fa-222">**meetingDetailsTab** : eine Registerkarte in der Kopfzeile der Ansicht "Besprechungsdetails" des Kalenders.</span><span class="sxs-lookup"><span data-stu-id="a76fa-222">**meetingDetailsTab** : a tab in the header of the meeting details view of the calendar.</span></span>
* <span data-ttu-id="a76fa-223">**meetingSidePanel** : ein in-Meeting-Bereich, der über den einheitlichen Balken geöffnet wird (u-Leiste).</span><span class="sxs-lookup"><span data-stu-id="a76fa-223">**meetingSidePanel** : an in-meeting panel opened via the unified bar (u-bar).</span></span>

> [!NOTE]
> <span data-ttu-id="a76fa-224">Die Eigenschaft "Context" wird derzeit nicht unterstützt und wird daher auf mobilen Clients ignoriert.</span><span class="sxs-lookup"><span data-stu-id="a76fa-224">"Context" property is currently not supported and thus will be ignored on mobile clients</span></span>

## <a name="configure-your-app-for-meeting-scenarios"></a><span data-ttu-id="a76fa-225">Konfigurieren Ihrer APP für Besprechungs Szenarien</span><span class="sxs-lookup"><span data-stu-id="a76fa-225">Configure your app for meeting scenarios</span></span>

> [!NOTE]
> * <span data-ttu-id="a76fa-226">Damit Ihre APP im Registerkarten Katalog sichtbar ist, muss Sie **konfigurierbare Registerkarten** und den **Gruppenchat Bereich** unterstützen.</span><span class="sxs-lookup"><span data-stu-id="a76fa-226">For your app to be visible in the tab gallery it needs to **support configurable tabs** and the **group chat scope**.</span></span>
>
> * <span data-ttu-id="a76fa-227">Mobile Clients unterstützen Registerkarten nur in Pre-und Post-Besprechungs Oberflächen.</span><span class="sxs-lookup"><span data-stu-id="a76fa-227">Mobile clients support Tabs only in Pre and Post Meeting Surfaces.</span></span> <span data-ttu-id="a76fa-228">Die in-Meeting-Erlebnisse (in-Meeting-Dialog und-Panel) auf mobilen Geräten werden in Kürze verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="a76fa-228">The In-meeting experiences (in-meeting dialog and panel) on mobile will be available soon.</span></span> <span data-ttu-id="a76fa-229">Befolgten Sie die [Anleitungen für Registerkarten auf mobilen Geräten](../tabs/design/tabs-mobile.md) beim Erstellen Ihrer Registerkarten für mobile Geräte.</span><span class="sxs-lookup"><span data-stu-id="a76fa-229">Follow the [guidance for tabs on mobile](../tabs/design/tabs-mobile.md) when creating your tabs for mobile.</span></span> 

### <a name="pre-meeting"></a><span data-ttu-id="a76fa-230">Pre-Meeting</span><span class="sxs-lookup"><span data-stu-id="a76fa-230">Pre-meeting</span></span>

<span data-ttu-id="a76fa-231">Benutzer mit Organizer-und/oder Presenter-Rollen fügen mithilfe der Schaltfläche Plus ➕ auf der Seite Besprechungs- **Chat** und Besprechungs **Details** Registerkarten zu einer Besprechung hinzu.</span><span class="sxs-lookup"><span data-stu-id="a76fa-231">Users with organizer and/or presenter roles add tabs to a meeting using the plus ➕ button in the meeting **Chat** and meeting **details** pages.</span></span> <span data-ttu-id="a76fa-232">Messaging Erweiterungen werden über das Menü Ellipsen/Überlauf hinzugefügt, &#x25CF;&#x25CF;&#x25CF; unterhalb des Bereichs zum Verfassen von Nachrichten im Chat angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="a76fa-232">Messaging extensions are added to via the ellipses/overflow menu &#x25CF;&#x25CF;&#x25CF; located beneath the compose message area in the chat.</span></span> <span data-ttu-id="a76fa-233">Bots werden mit der Taste "" zu einem Besprechungs Chat hinzugefügt **@** und die Option **Bots abrufen** ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="a76fa-233">Bots are added to a meeting chat using the " **@** " key and selecting **Get bots**.</span></span>

<span data-ttu-id="a76fa-234">✔ Die Benutzeridentität *muss* über die [Registerkarten SSO](../tabs/how-to/authentication/auth-aad-sso.md)bestätigt werden.</span><span class="sxs-lookup"><span data-stu-id="a76fa-234">✔ The user identity *must* be confirmed via [Tabs SSO](../tabs/how-to/authentication/auth-aad-sso.md).</span></span> <span data-ttu-id="a76fa-235">Nach dieser Authentifizierung kann die APP die Benutzerrolle über die getteilnehmer-API abrufen.</span><span class="sxs-lookup"><span data-stu-id="a76fa-235">Following this authentication, the app can retrieve the user role via the GetParticipant API.</span></span>

 <span data-ttu-id="a76fa-236">✔ Basierend auf der Benutzerrolle kann die App nun rollenspezifische Erlebnisse vorlegen.</span><span class="sxs-lookup"><span data-stu-id="a76fa-236">✔ Based on the user role, the app will now have the capability to present role specific experiences.</span></span> <span data-ttu-id="a76fa-237">Beispielsweise kann eine Polling-app nur Organisatoren und Referenten das Erstellen einer neuen Umfrage gestatten.</span><span class="sxs-lookup"><span data-stu-id="a76fa-237">For example, a polling app can allow only organizers and presenters to create a new poll.</span></span>

> <span data-ttu-id="a76fa-238">**Hinweis** : Rollenzuweisungen können geändert werden, während eine Besprechung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="a76fa-238">**NOTE** : Role assignments can be changed while a meeting is in progress.</span></span>  <span data-ttu-id="a76fa-239">*Siehe* [roles in a Teams Meeting](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).</span><span class="sxs-lookup"><span data-stu-id="a76fa-239">*See* [Roles in a Teams meeting](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).</span></span> 

### <a name="in-meeting"></a><span data-ttu-id="a76fa-240">In-Meeting</span><span class="sxs-lookup"><span data-stu-id="a76fa-240">In-meeting</span></span>

#### <a name="sidepanel"></a><span data-ttu-id="a76fa-241">**sidePanel**</span><span class="sxs-lookup"><span data-stu-id="a76fa-241">**sidePanel**</span></span>

<span data-ttu-id="a76fa-242">✔ In Ihrem App-Manifest fügen Sie **sidePanel** dem **Kontext** Array hinzu, wie oben beschrieben.</span><span class="sxs-lookup"><span data-stu-id="a76fa-242">✔ In your app manifest add **sidePanel** to the **context** array as described above.</span></span>

<span data-ttu-id="a76fa-243">✔ In der Besprechung als auch in allen Szenarien wird die app in einer in-Meeting-Registerkarte gerendert, die 320 Pixel groß in der Breite ist.</span><span class="sxs-lookup"><span data-stu-id="a76fa-243">✔ In the meeting as well as in all scenarios, the app will be rendered in an in-meeting tab that is 320px in width.</span></span> <span data-ttu-id="a76fa-244">Die Registerkarte muss dafür optimiert werden.</span><span class="sxs-lookup"><span data-stu-id="a76fa-244">Your tab must be optimized for this.</span></span> <span data-ttu-id="a76fa-245">*Siehe* , [framecontext-Schnittstelle](/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="a76fa-245">*See* , [FrameContext interface](/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest&preserve-view=true)</span></span>

<span data-ttu-id="a76fa-246">✔ Sie im Microsoft [Teams-SDK](../tabs/how-to/access-teams-context.md#user-context) nach, um die **benutzercontext** -API zu verwenden, um Anforderungen entsprechend weiterzuleiten.</span><span class="sxs-lookup"><span data-stu-id="a76fa-246">✔Refer to the [Teams SDK](../tabs/how-to/access-teams-context.md#user-context) to use the **userContext** API to route requests accordingly.</span></span>

<span data-ttu-id="a76fa-247">✔ Bezieht sich auf den Microsoft [Teams-Authentifizierungs Fluss für Registerkarten](../tabs/how-to/authentication/auth-flow-tab.md).</span><span class="sxs-lookup"><span data-stu-id="a76fa-247">✔ Refer to the [Teams authentication flow for tabs](../tabs/how-to/authentication/auth-flow-tab.md).</span></span> <span data-ttu-id="a76fa-248">Der Authentifizierungs Fluss für Registerkarten ähnelt dem auth-Fluss für Websites.</span><span class="sxs-lookup"><span data-stu-id="a76fa-248">Authentication flow for tabs is very similar to the auth flow for websites.</span></span> <span data-ttu-id="a76fa-249">Daher können Registerkarten OAuth 2,0 direkt verwenden.</span><span class="sxs-lookup"><span data-stu-id="a76fa-249">Thus, tabs can use OAuth 2.0 directly.</span></span> <span data-ttu-id="a76fa-250">*Siehe auch* , [Microsoft Identity Platform und OAuth 2,0-Autorisierungscode Fluss](/azure/active-directory/develop/v2-oauth2-auth-code-flow).</span><span class="sxs-lookup"><span data-stu-id="a76fa-250">*See also* , [Microsoft identity platform and OAuth 2.0 authorization code flow](/azure/active-directory/develop/v2-oauth2-auth-code-flow).</span></span>

#### <a name="in-meeting-dialog"></a><span data-ttu-id="a76fa-251">**in-Meeting-Dialog**</span><span class="sxs-lookup"><span data-stu-id="a76fa-251">**in-meeting dialog**</span></span>

<span data-ttu-id="a76fa-252">✔ Sie die Entwurfsrichtlinien für das [in-Meeting-Dialogfeld](design/designing-in-meeting-dialog.md)einhalten.</span><span class="sxs-lookup"><span data-stu-id="a76fa-252">✔ You must adhere to the [in-meeting dialog design guidelines](design/designing-in-meeting-dialog.md).</span></span>

<span data-ttu-id="a76fa-253">✔ Bezieht sich auf den Microsoft [Teams-Authentifizierungs Fluss für Registerkarten](../tabs/how-to/authentication/auth-flow-tab.md).</span><span class="sxs-lookup"><span data-stu-id="a76fa-253">✔ Refer to the [Teams authentication flow for tabs](../tabs/how-to/authentication/auth-flow-tab.md).</span></span>

<span data-ttu-id="a76fa-254">✔ Verwenden Sie die [Benachrichtigungs](/graph/api/resources/notifications-api-overview?view=graph-rest-beta&preserve-view=true) -API, um zu signalisieren, dass eine Blasen Benachrichtigung ausgelöst werden muss.</span><span class="sxs-lookup"><span data-stu-id="a76fa-254">✔ Use the [notification](/graph/api/resources/notifications-api-overview?view=graph-rest-beta&preserve-view=true) API to signal that a bubble notification needs to be triggered.</span></span>

<span data-ttu-id="a76fa-255">✔ Als Teil der Nutzlast der Benachrichtigungsanforderung enthalten die URL, in der der zu präsentierende Inhalt gehostet wird.</span><span class="sxs-lookup"><span data-stu-id="a76fa-255">✔ As part of the notification request payload, include the URL where the content to be showcased is hosted.</span></span>

> [!NOTE]
>
> * <span data-ttu-id="a76fa-256">Diese Benachrichtigungen sind in der Natur persistent.</span><span class="sxs-lookup"><span data-stu-id="a76fa-256">These notifications are persistent in nature.</span></span> <span data-ttu-id="a76fa-257">Sie müssen die [**submitTask ()**](../task-modules-and-cards/task-modules/task-modules-bots.md#submitting-the-result-of-a-task-module) -Funktion aufrufen, um automatisch zu entlassen, nachdem ein Benutzer eine Aktion in der-Webansicht durchführt.</span><span class="sxs-lookup"><span data-stu-id="a76fa-257">You must invoke the [**submitTask()**](../task-modules-and-cards/task-modules/task-modules-bots.md#submitting-the-result-of-a-task-module) function to auto-dismiss after a user takes an action in the web-view.</span></span> <span data-ttu-id="a76fa-258">Dies ist eine Voraussetzung für die APP-Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="a76fa-258">This is a requirement for app submission.</span></span> <span data-ttu-id="a76fa-259">*Siehe auch* Microsoft [Teams SDK: Aufgabenmodul](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="a76fa-259">*See also* , [Teams SDK: task module](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true).</span></span>
>
> * <span data-ttu-id="a76fa-260">Wenn Ihre APP anonyme Benutzer unterstützen soll, muss ihre anfängliche Anforderungsnutzlast auf die `from.id`  (ID der Benutzer)-Anforderungs Metadaten im `from` Objekt und nicht auf die `from.aadObjectId` Anforderungs Metadaten (Azure Active Directory ID des Benutzers) zurückgreifen.</span><span class="sxs-lookup"><span data-stu-id="a76fa-260">If you want your app to support anonymous users, your initial invoke request payload must rely on the `from.id`  (ID of the user) request metadata in the `from` object, not the `from.aadObjectId` (Azure Active Directory ID of the user) request metadata.</span></span> <span data-ttu-id="a76fa-261">*Weitere Informationen finden Sie unter* [Verwenden von Aufgaben Modulen in Registerkarten](../task-modules-and-cards/task-modules/task-modules-tabs.md) und [Erstellen und Senden des Aufgabenmoduls](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request).</span><span class="sxs-lookup"><span data-stu-id="a76fa-261">*See* [Using task modules in tabs](../task-modules-and-cards/task-modules/task-modules-tabs.md) and [Create and send the task module](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request).</span></span>

### <a name="post-meeting"></a><span data-ttu-id="a76fa-262">Nachbesprechung</span><span class="sxs-lookup"><span data-stu-id="a76fa-262">Post-meeting</span></span>

<span data-ttu-id="a76fa-263">Die Konfigurationen nach der Besprechung und vor der Besprechung sind äquivalent.</span><span class="sxs-lookup"><span data-stu-id="a76fa-263">The post-meeting and pre-meeting configurations are equivalent.</span></span>

## <a name="meeting-app-sample"></a><span data-ttu-id="a76fa-264">Beispiel für eine Besprechungs-App</span><span class="sxs-lookup"><span data-stu-id="a76fa-264">Meeting app sample</span></span>

 > [!div class="nextstepaction"]
> [<span data-ttu-id="a76fa-265">App für die Besprechungs Token-Generator</span><span class="sxs-lookup"><span data-stu-id="a76fa-265">Meeting token generator app</span></span>](https://github.com/OfficeDev/microsoft-teams-sample-meetings-token)
