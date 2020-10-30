---
title: Apps für Teams-Besprechungen erstellen
author: laujan
description: Erstellen von Apps für Microsoft Teams-Besprechungen
ms.topic: conceptual
ms.author: lajanuar
keywords: Teams-apps-Besprechungen Benutzer Teilnehmer-Rollen-API
ms.openlocfilehash: cf42d660c9b4a82f8e28d4d4379194c1bcc681e1
ms.sourcegitcommit: 3fc7ad33e2693f07170c3cb1a0d396261fc5c619
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "48796169"
---
# <a name="create-apps-for-teams-meetings-developer-preview"></a><span data-ttu-id="0fbf5-104">Erstellen von Apps für Microsoft Teams-Besprechungen (Entwicklervorschau)</span><span class="sxs-lookup"><span data-stu-id="0fbf5-104">Create apps for Teams meetings (Developer Preview)</span></span>

>[!IMPORTANT]
> <span data-ttu-id="0fbf5-105">In der Entwicklervorschau von Microsoft Teams enthaltene Features werden nur für frühere Zugriffs-, Test-und Feedback Zwecke bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-105">Features included in Microsoft Teams Developer Preview are provided for early-access, testing, and feedback purposes only.</span></span> <span data-ttu-id="0fbf5-106">Sie werden möglicherweise geändert, bevor Sie in der öffentlichen Version verfügbar werden und sollten nicht in Produktionsanwendungen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-106">They may undergo changes before becoming available in the public release and should not be used in production applications.</span></span>

## <a name="prerequisites-and-considerations"></a><span data-ttu-id="0fbf5-107">Voraussetzungen und Überlegungen</span><span class="sxs-lookup"><span data-stu-id="0fbf5-107">Prerequisites and considerations</span></span>

1. <span data-ttu-id="0fbf5-108">Apps in Besprechungen erfordern grundlegende Kenntnisse der [Teams-App-Entwicklung](../overview.md).</span><span class="sxs-lookup"><span data-stu-id="0fbf5-108">Apps in meetings require some basic knowledge of [Teams app development](../overview.md).</span></span> <span data-ttu-id="0fbf5-109">Eine app in einer Besprechung kann aus [Registerkarten](../tabs/what-are-tabs.md), [Bots](../bots/what-are-bots.md)und [Messaging Erweiterungs](../messaging-extensions/what-are-messaging-extensions.md) Features bestehen und erfordert Aktualisierungen des Teams-APP- [Manifests](#update-your-app-manifest) , um anzugeben, dass die APP für Besprechungen zur Verfügung steht.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-109">An app in a meeting can comprise of [tabs](../tabs/what-are-tabs.md), [bots](../bots/what-are-bots.md), and [messaging extensions](../messaging-extensions/what-are-messaging-extensions.md) features and will require updates to the Teams [app manifest](#update-your-app-manifest) to indicate that the app is available for meetings</span></span>

1. <span data-ttu-id="0fbf5-110">Damit Ihre APP im Besprechungs Lebenszyklus als Registerkarte funktioniert, muss Sie konfigurierbare Registerkarten im [Groupchat-Bereich](../resources/schema/manifest-schema.md#configurabletabs)unterstützen.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-110">For your app to function in the meeting lifecycle as a tab, it must support configurable tabs in the [groupchat scope](../resources/schema/manifest-schema.md#configurabletabs).</span></span> <span data-ttu-id="0fbf5-111">*Weitere Informationen finden Sie unter* [Erweitern Ihrer Teams-App mit einer benutzerdefinierten Registerkarte](../tabs/how-to/add-tab.md). Durch die Unterstützung des `groupchat` Bereichs wird Ihre APP in [Besprechungen vor](teams-apps-in-meetings.md#pre-meeting-app-experience) und [nach](teams-apps-in-meetings.md#post-meeting-app-experience) dem Chatten aktiviert.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-111">*See* [Extend your Teams app with a custom tab](../tabs/how-to/add-tab.md). Supporting the `groupchat` scope will enable your app in [pre-meeting](teams-apps-in-meetings.md#pre-meeting-app-experience) and [post-meeting](teams-apps-in-meetings.md#post-meeting-app-experience) chats.</span></span>

1. <span data-ttu-id="0fbf5-112">Die URL-Parameter der Besprechungs-API erfordern möglicherweise, `meetingId` `userId` und die [Mandanten](/onedrive/find-your-office-365-tenant-id) -Nr sind im Rahmen des Teams-Client-SDK und der Bot-Aktivität verfügbar.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-112">Meeting API URL parameters may require `meetingId`, `userId`, and the [tenantId](/onedrive/find-your-office-365-tenant-id) These are available as part of the Teams Client SDK and bot activity.</span></span> <span data-ttu-id="0fbf5-113">Außerdem können zuverlässige Informationen für Benutzer-ID und Mandanten-ID mithilfe der [Registerkarten-SSO-Authentifizierung](../tabs/how-to/authentication/auth-aad-sso.md)abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-113">Additionally, reliable information for user ID and tenant ID can be retrieved using [Tab SSO authentication](../tabs/how-to/authentication/auth-aad-sso.md).</span></span>

1. <span data-ttu-id="0fbf5-114">Einige Besprechungs-APIs, wie zum Beispiel, `GetParticipant` erfordern eine [bot-Registrierung und eine bot-APP-ID](../bots/how-to/create-a-bot-for-teams.md#with-an-azure-subscription) zum Generieren von auth-Token.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-114">Some meeting APIs, such as `GetParticipant` will require a [bot registration and bot app ID](../bots/how-to/create-a-bot-for-teams.md#with-an-azure-subscription) to generate auth tokens.</span></span>

1. <span data-ttu-id="0fbf5-115">Entwickler müssen sich an die allgemeinen [Entwurfsrichtlinien für Teams-Registerkarten](../tabs/design/tabs.md) für Pre-und Post-Meeting-Szenarien sowie die [in-Meeting-Dialogfeld Richtlinien](design/designing-in-meeting-dialog.md) für das in-Meeting-Dialogfeld halten, das während einer Teambesprechung ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-115">Developers must adhere to general [Teams tab design guidelines](../tabs/design/tabs.md) for pre- and post-meeting scenarios as well as the [in-meeting dialog guidelines](design/designing-in-meeting-dialog.md) for in-meeting dialog triggered during a Teams meeting.</span></span>

## <a name="meeting-apps-api-reference"></a><span data-ttu-id="0fbf5-116">Besprechungs-apps-API-Referenz</span><span class="sxs-lookup"><span data-stu-id="0fbf5-116">Meeting apps API reference</span></span>

|<span data-ttu-id="0fbf5-117">API</span><span class="sxs-lookup"><span data-stu-id="0fbf5-117">API</span></span>|<span data-ttu-id="0fbf5-118">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0fbf5-118">Description</span></span>|<span data-ttu-id="0fbf5-119">Anforderung</span><span class="sxs-lookup"><span data-stu-id="0fbf5-119">Request</span></span>|<span data-ttu-id="0fbf5-120">Source</span><span class="sxs-lookup"><span data-stu-id="0fbf5-120">Source</span></span>|
|---|---|----|---|
|<span data-ttu-id="0fbf5-121">**Getusercontext**</span><span class="sxs-lookup"><span data-stu-id="0fbf5-121">**GetUserContext**</span></span>| <span data-ttu-id="0fbf5-122">Abrufen von Kontextinformationen zum Anzeigen relevanter Inhalte auf einer Registerkarte Teams.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-122">Get contextual information to display relevant content in a Teams tab.</span></span> |<span data-ttu-id="0fbf5-123">_**verläuft. GetContext (() => {/ *...* / } )**_</span><span class="sxs-lookup"><span data-stu-id="0fbf5-123">_**microsoftTeams.getContext( ( ) => {  / *...* / } )**_</span></span>|<span data-ttu-id="0fbf5-124">Microsoft Teams-Client-SDK</span><span class="sxs-lookup"><span data-stu-id="0fbf5-124">Microsoft Teams client SDK</span></span>|
|<span data-ttu-id="0fbf5-125">**Getparticipant**</span><span class="sxs-lookup"><span data-stu-id="0fbf5-125">**GetParticipant**</span></span>|<span data-ttu-id="0fbf5-126">Mit dieser API kann ein bot eine Teilnehmer Information nach Besprechungs-ID und Teilnehmer-ID abrufen.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-126">This API allows a bot to fetch a participant information by meeting id and participant id.</span></span>|<span data-ttu-id="0fbf5-127">**GET** _**/V1/Meetings/{meetingId}/participants/{participantId} abrufen? Mandanten-Nr = {Mandanten** -Nr}_</span><span class="sxs-lookup"><span data-stu-id="0fbf5-127">**GET** _**/v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}**_</span></span> |<span data-ttu-id="0fbf5-128">Microsoft bot Framework SDK</span><span class="sxs-lookup"><span data-stu-id="0fbf5-128">Microsoft Bot Framework SDK</span></span>|
|<span data-ttu-id="0fbf5-129">**NotificationSignal**</span><span class="sxs-lookup"><span data-stu-id="0fbf5-129">**NotificationSignal**</span></span> |<span data-ttu-id="0fbf5-130">Besprechungs Signale werden über die folgende vorhandene Benachrichtigungs-API für Unterhaltungen (für Benutzer-bot-Chat) übermittelt.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-130">Meeting signals will be delivered using the following existing conversation notification API (for user-bot chat).</span></span> <span data-ttu-id="0fbf5-131">Mit dieser API können Entwickler basierend auf der Endbenutzer Aktion signalisieren, dass eine Dialog Blase in einer Besprechung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-131">This API allows developers to signal based on end-user action to show-case an in-meeting dialog bubble.</span></span>|<span data-ttu-id="0fbf5-132">**Post** _**/V3/Conversations/{conversationId}/Activities**_</span><span class="sxs-lookup"><span data-stu-id="0fbf5-132">**POST** _**/v3/conversations/{conversationId}/activities**_</span></span>|<span data-ttu-id="0fbf5-133">Microsoft bot Framework SDK</span><span class="sxs-lookup"><span data-stu-id="0fbf5-133">Microsoft Bot Framework SDK</span></span>|

### <a name="getusercontext"></a><span data-ttu-id="0fbf5-134">Getusercontext</span><span class="sxs-lookup"><span data-stu-id="0fbf5-134">GetUserContext</span></span>

<span data-ttu-id="0fbf5-135">Eine Anleitung zum Identifizieren und Abrufen von Kontextinformationen für die Registerkarteninhalte finden Sie in der Dokumentation zu [Get Context for your Teams](../tabs/how-to/access-teams-context.md#getting-context-by-using-the-microsoft-teams-javascript-library) .</span><span class="sxs-lookup"><span data-stu-id="0fbf5-135">Please refer to our [Get context for your Teams tab](../tabs/how-to/access-teams-context.md#getting-context-by-using-the-microsoft-teams-javascript-library) documentation for guidance on identifying and  retrieving contextual information for your tab content.</span></span> <span data-ttu-id="0fbf5-136">Im Rahmen der Erweiterbarkeit von Besprechungen wurde für die Antwort Nutzlast ein neuer Wert hinzugefügt:</span><span class="sxs-lookup"><span data-stu-id="0fbf5-136">As part of meetings extensibility, a new value has been added for the response payload:</span></span>

<span data-ttu-id="0fbf5-137">✔- **Besprechungs** -Nr: wird von einer Registerkarte bei der Ausführung im Besprechungs Kontext verwendet.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-137">✔ **meetingId** : used by a tab when running in the meeting context.</span></span>

### <a name="getparticipant-api"></a><span data-ttu-id="0fbf5-138">Getparticipant-API</span><span class="sxs-lookup"><span data-stu-id="0fbf5-138">GetParticipant API</span></span>

> [!NOTE]
>
> * <span data-ttu-id="0fbf5-139">Sie sollten keine Teilnehmerrollen Zwischenspeichern, da der Besprechungsorganisator zu einem beliebigen Zeitpunkt eine Rolle ändern kann.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-139">Do not cache participant roles since the meeting organizer can change a role at any point in time.</span></span>
>
> * <span data-ttu-id="0fbf5-140">Microsoft Teams unterstützt derzeit keine großen Verteilerlisten oder Dienstplan Größen von mehr als 350 Teilnehmern für die `GetParticipant` API.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-140">Teams does not currently support large distribution lists or roster sizes of more than 350 participants for the `GetParticipant` API.</span></span>
>
> * <span data-ttu-id="0fbf5-141">Die Unterstützung für das bot Framework SDK wird in Kürze verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-141">Support for the Bot Framework SDK is coming soon.</span></span>

#### <a name="request"></a><span data-ttu-id="0fbf5-142">Anforderung</span><span class="sxs-lookup"><span data-stu-id="0fbf5-142">Request</span></span>

```http
GET /v3/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}
```

<span data-ttu-id="0fbf5-143">*Siehe* [bot Framework-API-Referenz](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="0fbf5-143">*See* the [Bot Framework API reference](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0&preserve-view=true).</span></span>

<!-- markdownlint-disable MD025 -->

<span data-ttu-id="0fbf5-144">**C#-Beispiel**</span><span class="sxs-lookup"><span data-stu-id="0fbf5-144">**C# Example**</span></span>

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

#### <a name="query-parameters"></a><span data-ttu-id="0fbf5-145">Abfrageparameter</span><span class="sxs-lookup"><span data-stu-id="0fbf5-145">Query parameters</span></span>

|<span data-ttu-id="0fbf5-146">Wert</span><span class="sxs-lookup"><span data-stu-id="0fbf5-146">Value</span></span>|<span data-ttu-id="0fbf5-147">Typ</span><span class="sxs-lookup"><span data-stu-id="0fbf5-147">Type</span></span>|<span data-ttu-id="0fbf5-148">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="0fbf5-148">Required</span></span>|<span data-ttu-id="0fbf5-149">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0fbf5-149">Description</span></span>|
|---|---|----|---|
|<span data-ttu-id="0fbf5-150">**meetingId**</span><span class="sxs-lookup"><span data-stu-id="0fbf5-150">**meetingId**</span></span>| <span data-ttu-id="0fbf5-151">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="0fbf5-151">string</span></span> | <span data-ttu-id="0fbf5-152">Ja</span><span class="sxs-lookup"><span data-stu-id="0fbf5-152">Yes</span></span> | <span data-ttu-id="0fbf5-153">Die Besprechungs-ID ist über bot Invoke und Microsoft Teams Client SDK verfügbar.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-153">The meeting identifier is available via Bot Invoke and Teams Client SDK.</span></span>|
|<span data-ttu-id="0fbf5-154">**Teilnehmer-Nr**</span><span class="sxs-lookup"><span data-stu-id="0fbf5-154">**participantId**</span></span>| <span data-ttu-id="0fbf5-155">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="0fbf5-155">string</span></span> | <span data-ttu-id="0fbf5-156">Ja</span><span class="sxs-lookup"><span data-stu-id="0fbf5-156">Yes</span></span> | <span data-ttu-id="0fbf5-157">Dieses Feld ist die Benutzer-ID und steht in der Registerkarte "SSO", im bot-Invoke und im Microsoft Teams-Client-SDK zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-157">This field is the User ID and it is available in Tab SSO, Bot Invoke, and Teams Client SDK.</span></span> <span data-ttu-id="0fbf5-158">Die Registerkarte SSO wird dringend empfohlen.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-158">Tab SSO is highly recommended</span></span>|
|<span data-ttu-id="0fbf5-159">**tenantId**</span><span class="sxs-lookup"><span data-stu-id="0fbf5-159">**tenantId**</span></span>| <span data-ttu-id="0fbf5-160">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="0fbf5-160">string</span></span> | <span data-ttu-id="0fbf5-161">Ja</span><span class="sxs-lookup"><span data-stu-id="0fbf5-161">Yes</span></span> | <span data-ttu-id="0fbf5-162">Dies ist für Mandanten Benutzer erforderlich.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-162">This required for tenant users.</span></span> <span data-ttu-id="0fbf5-163">Sie ist in Tab SSO, bot Invoke und Microsoft Teams Client SDK verfügbar.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-163">It is available in Tab SSO, Bot Invoke, and Teams Client SDK.</span></span> <span data-ttu-id="0fbf5-164">Die Registerkarte SSO wird dringend empfohlen.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-164">Tab SSO is highly recommended</span></span>|

#### <a name="response-payload"></a><span data-ttu-id="0fbf5-165">Antwort Nutzlast</span><span class="sxs-lookup"><span data-stu-id="0fbf5-165">Response Payload</span></span>
<!-- markdownlint-disable MD036 -->

<span data-ttu-id="0fbf5-166">**Rolle** unter "Besprechung" kann *Organisator* , *Referent* oder *Teilnehmer* sein.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-166">**role** under "meeting" can be *Organizer* , *Presenter* , or *Attendee* .</span></span>

<span data-ttu-id="0fbf5-167">**Beispiel 1**</span><span class="sxs-lookup"><span data-stu-id="0fbf5-167">**Example 1**</span></span>

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
#### <a name="response-codes"></a><span data-ttu-id="0fbf5-168">Antwort Codes</span><span class="sxs-lookup"><span data-stu-id="0fbf5-168">Response Codes</span></span>

<span data-ttu-id="0fbf5-169">**403** : die APP darf keine Teilnehmer Informationen erhalten.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-169">**403** : the app is not allowed to get participant information.</span></span> <span data-ttu-id="0fbf5-170">Dies ist die häufigste Fehlerantwort und wird ausgelöst, wenn die APP nicht in der Besprechung installiert wird, beispielsweise wenn die APP vom mandantenadministrator deaktiviert oder während der Live-Website Minderung blockiert wird.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-170">This will be the most common error response and is triggered when the app is not installed in the meeting such as when the app is disabled by tenant admin or blocked during live site mitigation.</span></span>  
<span data-ttu-id="0fbf5-171">**200** : Teilnehmer Informationen erfolgreich abgerufen</span><span class="sxs-lookup"><span data-stu-id="0fbf5-171">**200** : participant information successfully retrieved</span></span>  
<span data-ttu-id="0fbf5-172">**401** : Ungültiges Token</span><span class="sxs-lookup"><span data-stu-id="0fbf5-172">**401** : invalid token</span></span>  
<span data-ttu-id="0fbf5-173">**404** : die Besprechung ist nicht vorhanden, oder der Teilnehmer kann nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-173">**404** : the meeting doesn't exist or participant can’t be found.</span></span>

<!-- markdownlint-disable MD024 -->
### <a name="notificationsignal-api"></a><span data-ttu-id="0fbf5-174">NotificationSignal-API</span><span class="sxs-lookup"><span data-stu-id="0fbf5-174">NotificationSignal API</span></span>

> [!NOTE]
> <span data-ttu-id="0fbf5-175">Wenn ein in-Meeting-Dialogfeld aufgerufen wird, wird derselbe Inhalt auch als Chatnachricht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-175">When an in-meeting dialog is invoked, the same content will also be presented as a chat message.</span></span>

#### <a name="request"></a><span data-ttu-id="0fbf5-176">Anforderung</span><span class="sxs-lookup"><span data-stu-id="0fbf5-176">Request</span></span>

```http
POST /v3/conversations/{conversationId}/activities
```

#### <a name="query-parameters"></a><span data-ttu-id="0fbf5-177">Abfrageparameter</span><span class="sxs-lookup"><span data-stu-id="0fbf5-177">Query parameters</span></span>

|<span data-ttu-id="0fbf5-178">Wert</span><span class="sxs-lookup"><span data-stu-id="0fbf5-178">Value</span></span>|<span data-ttu-id="0fbf5-179">Typ</span><span class="sxs-lookup"><span data-stu-id="0fbf5-179">Type</span></span>|<span data-ttu-id="0fbf5-180">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="0fbf5-180">Required</span></span>|<span data-ttu-id="0fbf5-181">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0fbf5-181">Description</span></span>|
|---|---|----|---|
|<span data-ttu-id="0fbf5-182">**conversationId**</span><span class="sxs-lookup"><span data-stu-id="0fbf5-182">**conversationId**</span></span>| <span data-ttu-id="0fbf5-183">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="0fbf5-183">string</span></span> | <span data-ttu-id="0fbf5-184">Ja</span><span class="sxs-lookup"><span data-stu-id="0fbf5-184">Yes</span></span> | <span data-ttu-id="0fbf5-185">Die Konversations-ID ist im Rahmen von bot Invoke verfügbar</span><span class="sxs-lookup"><span data-stu-id="0fbf5-185">The conversation identifier is available as part of bot invoke</span></span> |

#### <a name="request-payload"></a><span data-ttu-id="0fbf5-186">Anforderungsnutzlast</span><span class="sxs-lookup"><span data-stu-id="0fbf5-186">Request Payload</span></span>

> [!NOTE]
>
> <span data-ttu-id="0fbf5-187">Das completionBotId in der externalResourceUrl in der folgenden Nutzlast ist ein optionaler Parameter.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-187">The completionBotId in the externalResourceUrl in the requeste payload below is an optional parameter.</span></span> <span data-ttu-id="0fbf5-188">Es ist die bot-ID, die im Manifest deklariert wird.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-188">It is the Bot ID that is declared in the manifest.</span></span> <span data-ttu-id="0fbf5-189">Der bot erhält ein Result-Objekt.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-189">The bot will receive a result object.</span></span>

# <a name="json"></a>[<span data-ttu-id="0fbf5-190">Json</span><span class="sxs-lookup"><span data-stu-id="0fbf5-190">JSON</span></span>](#tab/json)

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

# <a name="cnet"></a>[<span data-ttu-id="0fbf5-191">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="0fbf5-191">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="javascript"></a>[<span data-ttu-id="0fbf5-192">JavaScript</span><span class="sxs-lookup"><span data-stu-id="0fbf5-192">JavaScript</span></span>](#tab/javascript)

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
> <span data-ttu-id="0fbf5-193">Die URL in der Inhalts Blase (taskInfo-URL) muss in der Liste [gültiger Domänen](../resources/schema/manifest-schema.md#validdomains) enthalten sein, die im App-Manifest für Teams enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-193">The URL in the content bubble (taskInfo URL) must be included in the [valid domains](../resources/schema/manifest-schema.md#validdomains) list included in the Teams app manifest.</span></span>

#### <a name="response-codes"></a><span data-ttu-id="0fbf5-194">Antwort Codes</span><span class="sxs-lookup"><span data-stu-id="0fbf5-194">Response Codes</span></span>

<span data-ttu-id="0fbf5-195">**201** : Aktivität mit Signal wurde erfolgreich gesendet</span><span class="sxs-lookup"><span data-stu-id="0fbf5-195">**201** : activity with signal is successfully sent</span></span>  
<span data-ttu-id="0fbf5-196">**401** : Ungültiges Token</span><span class="sxs-lookup"><span data-stu-id="0fbf5-196">**401** : invalid token</span></span>  
<span data-ttu-id="0fbf5-197">**403** : die APP darf das Signal nicht senden.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-197">**403** : the app is not allowed to send the signal.</span></span> <span data-ttu-id="0fbf5-198">In diesem Fall sollte die Nutzlast eine ausführlichere Fehlermeldung enthalten.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-198">In this case, the payload should contain more detail error message.</span></span> <span data-ttu-id="0fbf5-199">Es kann viele Gründe geben: app, die vom mandantenadministrator deaktiviert, während einer Live-Standort Minderung blockiert wird, usw.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-199">There can be many reasons: app disabled by tenant admin, blocked during live site mitigation, etc.</span></span>  
<span data-ttu-id="0fbf5-200">**404** : Besprechungs Chat nicht vorhanden</span><span class="sxs-lookup"><span data-stu-id="0fbf5-200">**404** : meeting chat doesn't exist</span></span>  

## <a name="enable-your-app-for-teams-meetings"></a><span data-ttu-id="0fbf5-201">Aktivieren Ihrer APP für Microsoft Teams-Besprechungen</span><span class="sxs-lookup"><span data-stu-id="0fbf5-201">Enable your app for Teams meetings</span></span>

### <a name="update-your-app-manifest"></a><span data-ttu-id="0fbf5-202">Aktualisieren des App-Manifests</span><span class="sxs-lookup"><span data-stu-id="0fbf5-202">Update your app manifest</span></span>

<span data-ttu-id="0fbf5-203">Die APP-Funktionen für Besprechungen werden in Ihrem App-Manifest über die **configurableTabs**  ->  - **Bereiche** und **Kontext** Arrays deklariert.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-203">The meetings app capabilities are declared in your app manifest via the **configurableTabs** -> **scopes** and **context** arrays.</span></span> <span data-ttu-id="0fbf5-204">*Scope* definiert, an wen und in welchem *Kontext* definiert wird, wo Ihre app verfügbar sein wird.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-204">*Scope* defines to whom and *context* defines where your app will be available.</span></span>

> [!NOTE]
> * <span data-ttu-id="0fbf5-205">Verwenden Sie das [Manifest-Schema für Entwicklervorschau](../resources/schema/manifest-schema-dev-preview.md) , um dieses in Ihrem App-Manifest zu testen.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-205">Please use [Developer Preview manifest schema](../resources/schema/manifest-schema-dev-preview.md) to try this in your app manifest.</span></span>

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

### <a name="context-property"></a><span data-ttu-id="0fbf5-206">Context-Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="0fbf5-206">Context property</span></span>

<span data-ttu-id="0fbf5-207">Die Registerkarte `context` und die `scopes` Eigenschaften funktionieren in Harmonie, damit Sie bestimmen können, wo Ihre APP angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-207">The tab `context` and `scopes` properties work in harmony to allow you to determine where you want your app to appear.</span></span> <span data-ttu-id="0fbf5-208">Registerkarten im `team` `groupchat` Bereich oder können mehr als einen Kontext aufweisen.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-208">Tabs in the `team` or `groupchat` scope can have more than one context.</span></span> <span data-ttu-id="0fbf5-209">Die möglichen Werte für die Context-Eigenschaft lauten wie folgt:</span><span class="sxs-lookup"><span data-stu-id="0fbf5-209">The possible values for the context property are as follows:</span></span>

* <span data-ttu-id="0fbf5-210">**channelTab** : eine Registerkarte in der Kopfzeile eines Team Kanals.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-210">**channelTab** : a tab in the header of a team channel.</span></span>
* <span data-ttu-id="0fbf5-211">**privateChatTab** : eine Registerkarte in der Kopfzeile eines Gruppenchats zwischen einer Gruppe von Benutzern, die sich nicht im Kontext eines Teams oder einer Besprechung befinden.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-211">**privateChatTab** : a tab in the header of a group chat between a set of users not in the context of a team or meeting.</span></span>
* <span data-ttu-id="0fbf5-212">**meetingChatTab** : eine Registerkarte in der Kopfzeile eines Gruppenchats zwischen einer Gruppe von Benutzern im Kontext einer geplanten Besprechung.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-212">**meetingChatTab** : a tab in the header of a group chat between a set of users in the context of a scheduled meeting.</span></span>
* <span data-ttu-id="0fbf5-213">**meetingDetailsTab** : eine Registerkarte in der Kopfzeile der Ansicht "Besprechungsdetails" des Kalenders.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-213">**meetingDetailsTab** : a tab in the header of the meeting details view of the calendar.</span></span>
* <span data-ttu-id="0fbf5-214">**meetingSidePanel** : ein in-Meeting-Bereich, der über den einheitlichen Balken geöffnet wird (u-Leiste).</span><span class="sxs-lookup"><span data-stu-id="0fbf5-214">**meetingSidePanel** : an in-meeting panel opened via the unified bar (u-bar).</span></span>

> [!NOTE]
> <span data-ttu-id="0fbf5-215">Die Eigenschaft "Context" wird derzeit nicht unterstützt und wird daher auf mobilen Clients ignoriert.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-215">"Context" property is currently not supported and thus will be ignored on mobile clients</span></span>

## <a name="configure-your-app-for-meeting-scenarios"></a><span data-ttu-id="0fbf5-216">Konfigurieren Ihrer APP für Besprechungs Szenarien</span><span class="sxs-lookup"><span data-stu-id="0fbf5-216">Configure your app for meeting scenarios</span></span>

> [!NOTE]
> * <span data-ttu-id="0fbf5-217">Damit Ihre APP im Registerkarten Katalog sichtbar ist, muss Sie **konfigurierbare Registerkarten** und den **Gruppenchat Bereich** unterstützen.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-217">For your app to be visible in the tab gallery it needs to **support configurable tabs** and the **group chat scope** .</span></span>
>
> * <span data-ttu-id="0fbf5-218">Mobile Clients unterstützen Registerkarten nur in Pre-und Post-Besprechungs Oberflächen.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-218">Mobile clients support Tabs only in Pre and Post Meeting Surfaces.</span></span> <span data-ttu-id="0fbf5-219">Die in-Meeting-Erlebnisse (in-Meeting-Dialog und-Panel) auf mobilen Geräten werden in Kürze verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-219">The In-meeting experiences (in-meeting dialog and panel) on mobile will be available soon.</span></span> <span data-ttu-id="0fbf5-220">Befolgten Sie die [Anleitungen für Registerkarten auf mobilen Geräten](../tabs/design/tabs-mobile.md) beim Erstellen Ihrer Registerkarten für mobile Geräte.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-220">Follow the [guidance for tabs on mobile](../tabs/design/tabs-mobile.md) when creating your tabs for mobile.</span></span> 

### <a name="pre-meeting"></a><span data-ttu-id="0fbf5-221">Pre-Meeting</span><span class="sxs-lookup"><span data-stu-id="0fbf5-221">Pre-meeting</span></span>

<span data-ttu-id="0fbf5-222">Benutzer mit Organizer-und/oder Presenter-Rollen fügen mithilfe der Schaltfläche Plus ➕ auf der Seite Besprechungs- **Chat** und Besprechungs **Details** Registerkarten zu einer Besprechung hinzu.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-222">Users with organizer and/or presenter roles add tabs to a meeting using the plus ➕ button in the meeting **Chat** and meeting **details** pages.</span></span> <span data-ttu-id="0fbf5-223">Messaging Erweiterungen werden über das Menü Ellipsen/Überlauf hinzugefügt, &#x25CF;&#x25CF;&#x25CF; unterhalb des Bereichs zum Verfassen von Nachrichten im Chat angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-223">Messaging extensions are added to via the ellipses/overflow menu &#x25CF;&#x25CF;&#x25CF; located beneath the compose message area in the chat.</span></span> <span data-ttu-id="0fbf5-224">Bots werden mit der Taste "" zu einem Besprechungs Chat hinzugefügt **@** und die Option **Bots abrufen** ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-224">Bots are added to a meeting chat using the " **@** " key and selecting **Get bots** .</span></span>

<span data-ttu-id="0fbf5-225">✔ Die Benutzeridentität *muss* über die [Registerkarten SSO](../tabs/how-to/authentication/auth-aad-sso.md)bestätigt werden.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-225">✔ The user identity *must* be confirmed via [Tabs SSO](../tabs/how-to/authentication/auth-aad-sso.md).</span></span> <span data-ttu-id="0fbf5-226">Nach dieser Authentifizierung kann die APP die Benutzerrolle über die getteilnehmer-API abrufen.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-226">Following this authentication, the app can retrieve the user role via the GetParticipant API.</span></span>

 <span data-ttu-id="0fbf5-227">✔ Basierend auf der Benutzerrolle kann die App nun rollenspezifische Erlebnisse vorlegen.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-227">✔ Based on the user role, the app will now have the capability to present role specific experiences.</span></span> <span data-ttu-id="0fbf5-228">Beispielsweise kann eine Polling-app nur Organisatoren und Referenten das Erstellen einer neuen Umfrage gestatten.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-228">For example, a polling app can allow only organizers and presenters to create a new poll.</span></span>

> <span data-ttu-id="0fbf5-229">**Hinweis** : Rollenzuweisungen können geändert werden, während eine Besprechung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-229">**NOTE** : Role assignments can be changed while a meeting is in progress.</span></span>  <span data-ttu-id="0fbf5-230">*Siehe* [roles in a Teams Meeting](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).</span><span class="sxs-lookup"><span data-stu-id="0fbf5-230">*See* [Roles in a Teams meeting](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).</span></span> 

### <a name="in-meeting"></a><span data-ttu-id="0fbf5-231">In-Meeting</span><span class="sxs-lookup"><span data-stu-id="0fbf5-231">In-meeting</span></span>

#### <a name="sidepanel"></a><span data-ttu-id="0fbf5-232">**sidePanel**</span><span class="sxs-lookup"><span data-stu-id="0fbf5-232">**sidePanel**</span></span>

<span data-ttu-id="0fbf5-233">✔ In Ihrem App-Manifest fügen Sie **sidePanel** dem **Kontext** Array hinzu, wie oben beschrieben.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-233">✔ In your app manifest add **sidePanel** to the **context** array as described above.</span></span>

<span data-ttu-id="0fbf5-234">✔ In der Besprechung als auch in allen Szenarien wird die app in einer in-Meeting-Registerkarte gerendert, die 320 Pixel groß in der Breite ist.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-234">✔ In the meeting as well as in all scenarios, the app will be rendered in an in-meeting tab that is 320px in width.</span></span> <span data-ttu-id="0fbf5-235">Die Registerkarte muss dafür optimiert werden.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-235">Your tab must be optimized for this.</span></span> <span data-ttu-id="0fbf5-236">*Siehe* , [framecontext-Schnittstelle](/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="0fbf5-236">*See* , [FrameContext interface](/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest&preserve-view=true)</span></span>

<span data-ttu-id="0fbf5-237">✔ Sie im Microsoft [Teams-SDK](../tabs/how-to/access-teams-context.md#user-context) nach, um die **benutzercontext** -API zu verwenden, um Anforderungen entsprechend weiterzuleiten.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-237">✔Refer to the [Teams SDK](../tabs/how-to/access-teams-context.md#user-context) to use the **userContext** API to route requests accordingly.</span></span>

<span data-ttu-id="0fbf5-238">✔ Bezieht sich auf den Microsoft [Teams-Authentifizierungs Fluss für Registerkarten](../tabs/how-to/authentication/auth-flow-tab.md).</span><span class="sxs-lookup"><span data-stu-id="0fbf5-238">✔ Refer to the [Teams authentication flow for tabs](../tabs/how-to/authentication/auth-flow-tab.md).</span></span> <span data-ttu-id="0fbf5-239">Der Authentifizierungs Fluss für Registerkarten ähnelt dem auth-Fluss für Websites.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-239">Authentication flow for tabs is very similar to the auth flow for websites.</span></span> <span data-ttu-id="0fbf5-240">Daher können Registerkarten OAuth 2,0 direkt verwenden.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-240">Thus, tabs can use OAuth 2.0 directly.</span></span> <span data-ttu-id="0fbf5-241">*Siehe auch* , [Microsoft Identity Platform und OAuth 2,0-Autorisierungscode Fluss](/azure/active-directory/develop/v2-oauth2-auth-code-flow).</span><span class="sxs-lookup"><span data-stu-id="0fbf5-241">*See also* , [Microsoft identity platform and OAuth 2.0 authorization code flow](/azure/active-directory/develop/v2-oauth2-auth-code-flow).</span></span>

#### <a name="in-meeting-dialog"></a><span data-ttu-id="0fbf5-242">**in-Meeting-Dialog**</span><span class="sxs-lookup"><span data-stu-id="0fbf5-242">**in-meeting dialog**</span></span>

<span data-ttu-id="0fbf5-243">✔ Sie die Entwurfsrichtlinien für das [in-Meeting-Dialogfeld](design/designing-in-meeting-dialog.md)einhalten.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-243">✔ You must adhere to the [in-meeting dialog design guidelines](design/designing-in-meeting-dialog.md).</span></span>

<span data-ttu-id="0fbf5-244">✔ Bezieht sich auf den Microsoft [Teams-Authentifizierungs Fluss für Registerkarten](../tabs/how-to/authentication/auth-flow-tab.md).</span><span class="sxs-lookup"><span data-stu-id="0fbf5-244">✔ Refer to the [Teams authentication flow for tabs](../tabs/how-to/authentication/auth-flow-tab.md).</span></span>

<span data-ttu-id="0fbf5-245">✔ Verwenden Sie die [Benachrichtigungs](/graph/api/resources/notifications-api-overview?view=graph-rest-beta&preserve-view=true) -API, um zu signalisieren, dass eine Blasen Benachrichtigung ausgelöst werden muss.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-245">✔ Use the [notification](/graph/api/resources/notifications-api-overview?view=graph-rest-beta&preserve-view=true) API to signal that a bubble notification needs to be triggered.</span></span>

<span data-ttu-id="0fbf5-246">✔ Als Teil der Nutzlast der Benachrichtigungsanforderung enthalten die URL, in der der zu präsentierende Inhalt gehostet wird.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-246">✔ As part of the notification request payload, include the URL where the content to be showcased is hosted.</span></span>

> [!NOTE]
>
> * <span data-ttu-id="0fbf5-247">Diese Benachrichtigungen sind in der Natur persistent.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-247">These notifications are persistent in nature.</span></span> <span data-ttu-id="0fbf5-248">Sie müssen die [**submitTask ()**](../task-modules-and-cards/task-modules/task-modules-bots.md#submitting-the-result-of-a-task-module) -Funktion aufrufen, um automatisch zu entlassen, nachdem ein Benutzer eine Aktion in der-Webansicht durchführt.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-248">You must invoke the [**submitTask()**](../task-modules-and-cards/task-modules/task-modules-bots.md#submitting-the-result-of-a-task-module) function to auto-dismiss after a user takes an action in the web-view.</span></span> <span data-ttu-id="0fbf5-249">Dies ist eine Voraussetzung für die APP-Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-249">This is a requirement for app submission.</span></span> <span data-ttu-id="0fbf5-250">*Siehe auch* Microsoft [Teams SDK: Aufgabenmodul](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="0fbf5-250">*See also* , [Teams SDK: task module](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true).</span></span>
>
> * <span data-ttu-id="0fbf5-251">Wenn Ihre APP anonyme Benutzer unterstützen soll, muss ihre anfängliche Anforderungsnutzlast auf die `from.id`  (ID der Benutzer)-Anforderungs Metadaten im `from` Objekt und nicht auf die `from.aadObjectId` Anforderungs Metadaten (Azure Active Directory ID des Benutzers) zurückgreifen.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-251">If you want your app to support anonymous users, your initial invoke request payload must rely on the `from.id`  (ID of the user) request metadata in the `from` object, not the `from.aadObjectId` (Azure Active Directory ID of the user) request metadata.</span></span> <span data-ttu-id="0fbf5-252">*Weitere Informationen finden Sie unter* [Verwenden von Aufgaben Modulen in Registerkarten](../task-modules-and-cards/task-modules/task-modules-tabs.md) und [Erstellen und Senden des Aufgabenmoduls](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request).</span><span class="sxs-lookup"><span data-stu-id="0fbf5-252">*See* [Using task modules in tabs](../task-modules-and-cards/task-modules/task-modules-tabs.md) and [Create and send the task module](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request).</span></span>

### <a name="post-meeting"></a><span data-ttu-id="0fbf5-253">Nachbesprechung</span><span class="sxs-lookup"><span data-stu-id="0fbf5-253">Post-meeting</span></span>

<span data-ttu-id="0fbf5-254">Die Konfigurationen nach der Besprechung und vor der Besprechung sind äquivalent.</span><span class="sxs-lookup"><span data-stu-id="0fbf5-254">The post-meeting and pre-meeting configurations are equivalent.</span></span>

## <a name="meeting-app-sample"></a><span data-ttu-id="0fbf5-255">Beispiel für eine Besprechungs-App</span><span class="sxs-lookup"><span data-stu-id="0fbf5-255">Meeting app sample</span></span>

 > [!div class="nextstepaction"]
> [<span data-ttu-id="0fbf5-256">App für die Besprechungs Token-Generator</span><span class="sxs-lookup"><span data-stu-id="0fbf5-256">Meeting token generator app</span></span>](https://github.com/OfficeDev/microsoft-teams-sample-meetings-token)
