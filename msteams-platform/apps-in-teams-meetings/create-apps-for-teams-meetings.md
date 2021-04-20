---
title: Apps für Teams-Besprechungen erstellen
author: laujan
description: Erstellen von Apps für Teams-Besprechungen
ms.topic: conceptual
ms.author: lajanuar
keywords: Rollen-API für Teams-Apps-Besprechungen für Benutzerteilnehmer
ms.openlocfilehash: c9410e142c6831fa0aa1b1f5307d92d67739be0e
ms.sourcegitcommit: ee8c4800da3b3569d80c6f3661a2f20aa1f2c5e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2021
ms.locfileid: "51885073"
---
# <a name="create-apps-for-teams-meetings"></a><span data-ttu-id="f4b4e-104">Apps für Teams-Besprechungen erstellen</span><span class="sxs-lookup"><span data-stu-id="f4b4e-104">Create apps for Teams meetings</span></span>

## <a name="prerequisites-and-considerations"></a><span data-ttu-id="f4b4e-105">Voraussetzungen und Überlegungen</span><span class="sxs-lookup"><span data-stu-id="f4b4e-105">Prerequisites and considerations</span></span>

<span data-ttu-id="f4b4e-106">Bevor Sie Apps für Teams-Besprechungen erstellen, müssen Sie folgendes wissen:</span><span class="sxs-lookup"><span data-stu-id="f4b4e-106">Before you create apps for Teams meetings, you must have an understanding of the following:</span></span>

* <span data-ttu-id="f4b4e-107">Sie müssen wissen, wie Sie Teams-Apps entwickeln.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-107">You must have knowledge of how to develop Teams apps.</span></span> <span data-ttu-id="f4b4e-108">Weitere Informationen finden Sie unter [Teams app development](../overview.md).</span><span class="sxs-lookup"><span data-stu-id="f4b4e-108">For more information, see [Teams app development](../overview.md).</span></span>

* <span data-ttu-id="f4b4e-109">Sie müssen das Teams-App-Manifest aktualisieren, um anzugeben, dass die App für Besprechungen verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-109">You must update the Teams app manifest to indicate that the app is available for meetings.</span></span> <span data-ttu-id="f4b4e-110">Weitere Informationen finden Sie unter [App-Manifest](#update-your-app-manifest).</span><span class="sxs-lookup"><span data-stu-id="f4b4e-110">For more information, see [app manifest](#update-your-app-manifest).</span></span>

* <span data-ttu-id="f4b4e-111">Damit Ihre App im Besprechungslebenszyklus als Registerkarte funktioniert, muss sie konfigurierbare Registerkarten im Gruppenchatbereich unterstützen.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-111">For your app to function in the meeting lifecycle as a tab, it must support configurable tabs in the groupchat scope.</span></span> <span data-ttu-id="f4b4e-112">Weitere Informationen finden Sie unter [groupchat scope](../resources/schema/manifest-schema.md#configurabletabs) und [build a group tab](../build-your-first-app/build-channel-tab.md).</span><span class="sxs-lookup"><span data-stu-id="f4b4e-112">For more information, see [groupchat scope](../resources/schema/manifest-schema.md#configurabletabs) and [build a group tab](../build-your-first-app/build-channel-tab.md).</span></span>

* <span data-ttu-id="f4b4e-113">Sie müssen die allgemeinen Richtlinien zum Entwerfen von Teams-Registerkarten für Szenarien vor und nach Besprechungen einhalten.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-113">You must adhere to general Teams tab design guidelines for pre- and post-meeting scenarios.</span></span> <span data-ttu-id="f4b4e-114">Informationen zu Erfahrungen während Besprechungen finden Sie in den Entwurfsrichtlinien für Besprechungsdialogfeldern und Besprechungsdialogfeldern.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-114">For experiences during meetings, refer to the in-meeting tab and in-meeting dialog design guidelines.</span></span> <span data-ttu-id="f4b4e-115">Weitere Informationen finden Sie unter [Richtlinien für das Entwerfen von Teams-Registerkarten,](../tabs/design/tabs.md)Richtlinien für den Entwurf von Registerkarten [in](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-tab) Besprechungen und Entwurfsrichtlinien für [Besprechungsdialogdialog.](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)</span><span class="sxs-lookup"><span data-stu-id="f4b4e-115">For more information, see [Teams tab design guidelines](../tabs/design/tabs.md), [in-meeting tab design guidelines](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-tab) and [in-meeting dialog design guidelines](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-dialog).</span></span>

* <span data-ttu-id="f4b4e-116">Sie müssen den Bereich `groupchat` unterstützen, um Ihre App in Chats vor und nach besprechungen zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-116">You must support the `groupchat` scope to enable your app in pre-meeting and post-meeting chats.</span></span> <span data-ttu-id="f4b4e-117">Mit der App vor der Besprechung können Sie Besprechungs-Apps finden und hinzufügen und Aufgaben vor besprechungen ausführen.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-117">With the pre-meeting app experience, you can find and add meeting apps and perform pre-meeting tasks.</span></span> <span data-ttu-id="f4b4e-118">Mit der App nach der Besprechung können Sie die Ergebnisse der Besprechung anzeigen, z. B. Umfrageergebnisse oder Feedback.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-118">With post-meeting app experience, you can view the results of the meeting, such as poll survey results or feedback.</span></span>

* <span data-ttu-id="f4b4e-119">Die Parameter für die Besprechungs-API-URL müssen `meetingId` über `userId` , und `tenantId` verfügen.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-119">Meeting API URL parameters must have `meetingId`, `userId`, and `tenantId`.</span></span> <span data-ttu-id="f4b4e-120">Diese sind im Rahmen der Teams-Client-SDK- und Botaktivität verfügbar.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-120">These are available as part of the Teams client SDK and bot activity.</span></span> <span data-ttu-id="f4b4e-121">Darüber hinaus können zuverlässige Informationen für Benutzer-ID und Mandanten-ID mithilfe der [Tab-SSO-Authentifizierung abgerufen werden.](../tabs/how-to/authentication/auth-aad-sso.md)</span><span class="sxs-lookup"><span data-stu-id="f4b4e-121">In addition, reliable information for user ID and tenant ID can be retrieved using [Tab SSO authentication](../tabs/how-to/authentication/auth-aad-sso.md).</span></span>

* <span data-ttu-id="f4b4e-122">Die `GetParticipant` API muss über eine Botregistrierung und -ID verfügen, um Authentifizierungstoken zu generieren.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-122">The `GetParticipant` API must have a bot registration and ID to generate auth tokens.</span></span> <span data-ttu-id="f4b4e-123">Weitere Informationen finden Sie unter [Botregistrierung und ID](../build-your-first-app/build-bot.md).</span><span class="sxs-lookup"><span data-stu-id="f4b4e-123">For more information, see [bot registration and ID](../build-your-first-app/build-bot.md).</span></span>

* <span data-ttu-id="f4b4e-124">Damit Ihre App in Echtzeit aktualisiert werden kann, muss sie basierend auf den Ereignisaktivitäten in der Besprechung auf dem neuesten Stand sein.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-124">For your app to update in real time, it must be up-to-date based on event activities in the meeting.</span></span> <span data-ttu-id="f4b4e-125">Diese Ereignisse können sich innerhalb des Dialogfelds in der Besprechung und in anderen Phasen des gesamten Besprechungslebenszyklus finden.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-125">These events can be within the in-meeting dialog box and other stages across the meeting lifecycle.</span></span> <span data-ttu-id="f4b4e-126">Das Dialogfeld in der Besprechung finden Sie unter `bot Id` Completion-Parameter in `Notification Signal API` .</span><span class="sxs-lookup"><span data-stu-id="f4b4e-126">For the in-meeting dialog box, see completion `bot Id` parameter in `Notification Signal API`.</span></span>

## <a name="meeting-apps-api-reference"></a><span data-ttu-id="f4b4e-127">Apireferenz für Besprechungs-Apps</span><span class="sxs-lookup"><span data-stu-id="f4b4e-127">Meeting apps API reference</span></span>

|<span data-ttu-id="f4b4e-128">API</span><span class="sxs-lookup"><span data-stu-id="f4b4e-128">API</span></span>|<span data-ttu-id="f4b4e-129">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f4b4e-129">Description</span></span>|<span data-ttu-id="f4b4e-130">Anforderung</span><span class="sxs-lookup"><span data-stu-id="f4b4e-130">Request</span></span>|<span data-ttu-id="f4b4e-131">Source</span><span class="sxs-lookup"><span data-stu-id="f4b4e-131">Source</span></span>|
|---|---|----|---|
|<span data-ttu-id="f4b4e-132">**GetUserContext**</span><span class="sxs-lookup"><span data-stu-id="f4b4e-132">**GetUserContext**</span></span>| <span data-ttu-id="f4b4e-133">Mit dieser API können Sie Kontextinformationen abrufen, um relevante Inhalte auf einer Registerkarte Teams anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-133">This API enables you to get contextual information to display relevant content in a Teams tab.</span></span> |<span data-ttu-id="f4b4e-134">_**microsoftTeams.getContext( ( ) => { /*...\* / } )*\*_</span><span class="sxs-lookup"><span data-stu-id="f4b4e-134">_**microsoftTeams.getContext( ( ) => {  /*...*/ } )**_</span></span>|<span data-ttu-id="f4b4e-135">Microsoft Teams client SDK</span><span class="sxs-lookup"><span data-stu-id="f4b4e-135">Microsoft Teams client SDK</span></span>|
|<span data-ttu-id="f4b4e-136">**GetParticipant**</span><span class="sxs-lookup"><span data-stu-id="f4b4e-136">**GetParticipant**</span></span>| <span data-ttu-id="f4b4e-137">Mit dieser API kann ein Bot Teilnehmerinformationen nach Besprechungs-ID und Teilnehmer-ID abrufen.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-137">This API allows a bot to fetch participant information by meeting ID and participant ID.</span></span> |<span data-ttu-id="f4b4e-138">**GET** _**/v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}**_</span><span class="sxs-lookup"><span data-stu-id="f4b4e-138">**GET** _**/v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}**_</span></span> |<span data-ttu-id="f4b4e-139">Microsoft Bot Framework SDK</span><span class="sxs-lookup"><span data-stu-id="f4b4e-139">Microsoft Bot Framework SDK</span></span>|
|<span data-ttu-id="f4b4e-140">**NotificationSignal**</span><span class="sxs-lookup"><span data-stu-id="f4b4e-140">**NotificationSignal**</span></span> | <span data-ttu-id="f4b4e-141">Mit dieser API können Sie Besprechungssignale bereitstellen, die mithilfe der vorhandenen Unterhaltungsbenachrichtigungs-API für den Benutzer-Bot-Chat übermittelt werden.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-141">This API enables you to provide meeting signals that are delivered using the existing conversation notification API for user-bot chat.</span></span> <span data-ttu-id="f4b4e-142">Damit können Sie basierend auf der Benutzeraktion, die ein Dialogfeld in der Besprechung zeigt, ein Signal senden.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-142">It allows you to signal based on user action that shows an in-meeting dialog box.</span></span> |<span data-ttu-id="f4b4e-143">**POST** _**/v3/conversations/{conversationId}/activities**_</span><span class="sxs-lookup"><span data-stu-id="f4b4e-143">**POST** _**/v3/conversations/{conversationId}/activities**_</span></span>|<span data-ttu-id="f4b4e-144">Microsoft Bot Framework SDK</span><span class="sxs-lookup"><span data-stu-id="f4b4e-144">Microsoft Bot Framework SDK</span></span>|

### <a name="getusercontext"></a><span data-ttu-id="f4b4e-145">GetUserContext</span><span class="sxs-lookup"><span data-stu-id="f4b4e-145">GetUserContext</span></span>

<span data-ttu-id="f4b4e-146">Informationen zum Identifizieren und Abrufen von Kontextinformationen für Ihre Registerkarteninhalte finden Sie unter [Abrufen des Kontexts für Ihre Registerkarte Teams](../tabs/how-to/access-teams-context.md#getting-context-by-using-the-microsoft-teams-javascript-library). `meetingId` wird von einer Registerkarte verwendet, wenn sie im Besprechungskontext ausgeführt wird, und wird für die Antwortnutzlast hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-146">To identify and retrieve contextual information for your tab content, see [get context for your Teams tab](../tabs/how-to/access-teams-context.md#getting-context-by-using-the-microsoft-teams-javascript-library). `meetingId` is used by a tab when running in the meeting context and is added for the response payload.</span></span>

### <a name="getparticipant-api"></a><span data-ttu-id="f4b4e-147">GetParticipant-API</span><span class="sxs-lookup"><span data-stu-id="f4b4e-147">GetParticipant API</span></span>

> [!NOTE]
> * <span data-ttu-id="f4b4e-148">Zwischenspeichern Sie keine Teilnehmerrollen, da der Besprechungsorganisator eine Rolle jederzeit ändern kann.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-148">Do not cache participant roles since the meeting organizer can change a role any time.</span></span>
> * <span data-ttu-id="f4b4e-149">Teams unterstützt derzeit keine großen Verteilerlisten oder Listengrößen von mehr als 350 Teilnehmern für die `GetParticipant` API.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-149">Teams does not currently support large distribution lists or roster sizes of more than 350 participants for the `GetParticipant` API.</span></span>

#### <a name="query-parameters"></a><span data-ttu-id="f4b4e-150">Abfrageparameter</span><span class="sxs-lookup"><span data-stu-id="f4b4e-150">Query parameters</span></span>

|<span data-ttu-id="f4b4e-151">Wert</span><span class="sxs-lookup"><span data-stu-id="f4b4e-151">Value</span></span>|<span data-ttu-id="f4b4e-152">Typ</span><span class="sxs-lookup"><span data-stu-id="f4b4e-152">Type</span></span>|<span data-ttu-id="f4b4e-153">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="f4b4e-153">Required</span></span>|<span data-ttu-id="f4b4e-154">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f4b4e-154">Description</span></span>|
|---|---|----|---|
|<span data-ttu-id="f4b4e-155">**meetingId**</span><span class="sxs-lookup"><span data-stu-id="f4b4e-155">**meetingId**</span></span>| <span data-ttu-id="f4b4e-156">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="f4b4e-156">string</span></span> | <span data-ttu-id="f4b4e-157">Ja</span><span class="sxs-lookup"><span data-stu-id="f4b4e-157">Yes</span></span> | <span data-ttu-id="f4b4e-158">Der Besprechungsbezeichner ist über Bot Invoke und Teams Client SDK verfügbar.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-158">The meeting identifier is available through Bot Invoke and Teams Client SDK.</span></span>|
|<span data-ttu-id="f4b4e-159">**participantId**</span><span class="sxs-lookup"><span data-stu-id="f4b4e-159">**participantId**</span></span>| <span data-ttu-id="f4b4e-160">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="f4b4e-160">string</span></span> | <span data-ttu-id="f4b4e-161">Ja</span><span class="sxs-lookup"><span data-stu-id="f4b4e-161">Yes</span></span> | <span data-ttu-id="f4b4e-162">Die Teilnehmer-ID ist die Benutzer-ID.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-162">The participant ID is the user ID.</span></span> <span data-ttu-id="f4b4e-163">Sie ist in Tab SSO, Bot Invoke und Teams Client SDK verfügbar.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-163">It is available in Tab SSO, Bot Invoke, and Teams Client SDK.</span></span> <span data-ttu-id="f4b4e-164">Es wird empfohlen, eine Teilnehmer-ID aus dem Tab-SSO zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-164">It is recommended to get a participant ID from the Tab SSO.</span></span> |
|<span data-ttu-id="f4b4e-165">**tenantId**</span><span class="sxs-lookup"><span data-stu-id="f4b4e-165">**tenantId**</span></span>| <span data-ttu-id="f4b4e-166">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="f4b4e-166">string</span></span> | <span data-ttu-id="f4b4e-167">Ja</span><span class="sxs-lookup"><span data-stu-id="f4b4e-167">Yes</span></span> | <span data-ttu-id="f4b4e-168">Die Mandanten-ID ist für die Mandantenbenutzer erforderlich.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-168">The tenant ID is required for the tenant users.</span></span> <span data-ttu-id="f4b4e-169">Sie ist in Tab SSO, Bot Invoke und Teams Client SDK verfügbar.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-169">It is available in Tab SSO, Bot Invoke, and Teams Client SDK.</span></span> <span data-ttu-id="f4b4e-170">Es wird empfohlen, eine Mandanten-ID aus dem Tab-SSO zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-170">It is recommended to get a tenant ID from the Tab SSO.</span></span> |

#### <a name="example"></a><span data-ttu-id="f4b4e-171">Beispiel</span><span class="sxs-lookup"><span data-stu-id="f4b4e-171">Example</span></span>

# <a name="c"></a>[<span data-ttu-id="f4b4e-172">C#</span><span class="sxs-lookup"><span data-stu-id="f4b4e-172">C#</span></span>](#tab/dotnet)

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

# <a name="javascript"></a>[<span data-ttu-id="f4b4e-173">JavaScript</span><span class="sxs-lookup"><span data-stu-id="f4b4e-173">JavaScript</span></span>](#tab/javascript)

```typescript

export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onMessage(async (context, next) => {
            TeamsMeetingParticipant participant = getMeetingParticipant(turnContext, "yourMeetingId", "yourParticipantId", "yourTenantId");
            let member = participant.user;
            let meetingInfo = participant.meeting;
            let conversation = participant.conversation;
            
            await context.sendActivity(`The participant role is: '${meetingInfo.role}'`);
            await next();
        });
    }
}

```

# <a name="json"></a>[<span data-ttu-id="f4b4e-174">Json</span><span class="sxs-lookup"><span data-stu-id="f4b4e-174">JSON</span></span>](#tab/json)

```http
GET /v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}
```

* * *

<span data-ttu-id="f4b4e-175">Der JSON-Antworttext für `GetParticipant` API ist:</span><span class="sxs-lookup"><span data-stu-id="f4b4e-175">The JSON response body for `GetParticipant` API is:</span></span>

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

#### <a name="response-codes"></a><span data-ttu-id="f4b4e-176">Antwortcodes</span><span class="sxs-lookup"><span data-stu-id="f4b4e-176">Response codes</span></span>

|<span data-ttu-id="f4b4e-177">Antwortcode</span><span class="sxs-lookup"><span data-stu-id="f4b4e-177">Response code</span></span>|<span data-ttu-id="f4b4e-178">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f4b4e-178">Description</span></span>|
|---|---|
| <span data-ttu-id="f4b4e-179">**403**</span><span class="sxs-lookup"><span data-stu-id="f4b4e-179">**403**</span></span> | <span data-ttu-id="f4b4e-180">Die App darf keine Teilnehmerinformationen erhalten.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-180">The app is not allowed to get participant information.</span></span> <span data-ttu-id="f4b4e-181">Dies ist die häufigste Fehlerantwort und wird ausgelöst, wenn die App nicht in der Besprechung installiert ist.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-181">This is the most common error response and is triggered if the app is not installed in the meeting.</span></span> <span data-ttu-id="f4b4e-182">Beispiel: Wenn die App vom Mandantenadministrator deaktiviert oder während der Livewebsitemigration blockiert wird.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-182">For example, if the app is disabled by tenant admin or blocked during live site migration.</span></span>|
| <span data-ttu-id="f4b4e-183">**200**</span><span class="sxs-lookup"><span data-stu-id="f4b4e-183">**200**</span></span> | <span data-ttu-id="f4b4e-184">Die Teilnehmerinformationen werden erfolgreich abgerufen.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-184">The participant information is successfully retrieved.</span></span>|
| <span data-ttu-id="f4b4e-185">**401**</span><span class="sxs-lookup"><span data-stu-id="f4b4e-185">**401**</span></span> | <span data-ttu-id="f4b4e-186">Die App antwortet mit einem ungültigen Token.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-186">The app responds with an invalid token.</span></span>|
| <span data-ttu-id="f4b4e-187">**404**</span><span class="sxs-lookup"><span data-stu-id="f4b4e-187">**404**</span></span> | <span data-ttu-id="f4b4e-188">Die Besprechung ist entweder abgelaufen, oder der Teilnehmer wurde nicht gefunden.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-188">The meeting has either expired or participant cannot be found.</span></span>|
| <span data-ttu-id="f4b4e-189">**500**</span><span class="sxs-lookup"><span data-stu-id="f4b4e-189">**500**</span></span> | <span data-ttu-id="f4b4e-190">Die Besprechung ist entweder länger als 60 Tage seit dem Ende der Besprechung abgelaufen, oder der Teilnehmer verfügt nicht über Berechtigungen basierend auf seiner Rolle.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-190">The meeting has either expired more than 60 days since the meeting ended or the participant does not have permissions based on their role.</span></span>|

### <a name="notificationsignal-api"></a><span data-ttu-id="f4b4e-191">NotificationSignal-API</span><span class="sxs-lookup"><span data-stu-id="f4b4e-191">NotificationSignal API</span></span>

<span data-ttu-id="f4b4e-192">Alle Benutzer in einer Besprechung erhalten die über die API gesendeten `NotificationSignal` Benachrichtigungen.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-192">All users in a meeting receive the notifications sent through the `NotificationSignal` API.</span></span>

> [!NOTE]
> * <span data-ttu-id="f4b4e-193">Wenn ein Dialogfeld in der Besprechung aufgerufen wird, wird der Inhalt als Chatnachricht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-193">When an in-meeting dialog box is invoked, the content is presented as a chat message.</span></span>
> * <span data-ttu-id="f4b4e-194">Derzeit wird das Senden gezielter Benachrichtigungen nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-194">Currently, sending targeted notifications is not supported.</span></span>

#### <a name="query-parameters"></a><span data-ttu-id="f4b4e-195">Abfrageparameter</span><span class="sxs-lookup"><span data-stu-id="f4b4e-195">Query parameters</span></span>

|<span data-ttu-id="f4b4e-196">Wert</span><span class="sxs-lookup"><span data-stu-id="f4b4e-196">Value</span></span>|<span data-ttu-id="f4b4e-197">Typ</span><span class="sxs-lookup"><span data-stu-id="f4b4e-197">Type</span></span>|<span data-ttu-id="f4b4e-198">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="f4b4e-198">Required</span></span>|<span data-ttu-id="f4b4e-199">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f4b4e-199">Description</span></span>|
|---|---|----|---|
|<span data-ttu-id="f4b4e-200">**conversationId**</span><span class="sxs-lookup"><span data-stu-id="f4b4e-200">**conversationId**</span></span>| <span data-ttu-id="f4b4e-201">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="f4b4e-201">string</span></span> | <span data-ttu-id="f4b4e-202">Ja</span><span class="sxs-lookup"><span data-stu-id="f4b4e-202">Yes</span></span> | <span data-ttu-id="f4b4e-203">Die Unterhaltungs-ID ist als Teil des Botaufrufs verfügbar.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-203">The conversation identifier is available as part of bot invoke</span></span> |

#### <a name="example"></a><span data-ttu-id="f4b4e-204">Beispiel</span><span class="sxs-lookup"><span data-stu-id="f4b4e-204">Example</span></span>

<span data-ttu-id="f4b4e-205">Der `Bot ID` wird im Manifest deklariert, und der Bot empfängt ein Ergebnisobjekt.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-205">The `Bot ID` is declared in the manifest and the bot receives a result object.</span></span>

> [!NOTE]
> * <span data-ttu-id="f4b4e-206">Der `completionBotId` Parameter von ist im `externalResourceUrl` angeforderten Nutzlastbeispiel optional.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-206">The `completionBotId` parameter of the `externalResourceUrl` is optional in the requested payload example.</span></span> <span data-ttu-id="f4b4e-207">`Bot ID` wird im Manifest deklariert, und der Bot empfängt ein Ergebnisobjekt.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-207">`Bot ID` is declared in the manifest and the bot receives a result object.</span></span>
> * <span data-ttu-id="f4b4e-208">Die `externalResourceUrl` Parameter für Breite und Höhe müssen in Pixel angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-208">The `externalResourceUrl` width and height parameters must be in pixels.</span></span> <span data-ttu-id="f4b4e-209">Um sicherzustellen, dass die Abmessungen innerhalb der zulässigen Grenzwerte liegen, finden Sie unter [Entwurfsrichtlinien](design/designing-apps-in-meetings.md).</span><span class="sxs-lookup"><span data-stu-id="f4b4e-209">To ensure the dimensions are within the allowed limits, see [design guidelines](design/designing-apps-in-meetings.md).</span></span>
> * <span data-ttu-id="f4b4e-210">Die URL ist die Im Besprechungsdialogfeld `<iframe>` geladene Seite.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-210">The URL is the page loaded as an `<iframe>` in the in-meeting dialog box.</span></span> <span data-ttu-id="f4b4e-211">Die Domäne muss sich im Array der App `validDomains` im App-Manifest befinden.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-211">The domain must be in the app's `validDomains` array in your app manifest.</span></span>

# <a name="c"></a>[<span data-ttu-id="f4b4e-212">C#</span><span class="sxs-lookup"><span data-stu-id="f4b4e-212">C#</span></span>](#tab/dotnet)

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

# <a name="javascript"></a>[<span data-ttu-id="f4b4e-213">JavaScript</span><span class="sxs-lookup"><span data-stu-id="f4b4e-213">JavaScript</span></span>](#tab/javascript)

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

# <a name="json"></a>[<span data-ttu-id="f4b4e-214">Json</span><span class="sxs-lookup"><span data-stu-id="f4b4e-214">JSON</span></span>](#tab/json)

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

#### <a name="response-codes"></a><span data-ttu-id="f4b4e-215">Antwortcodes</span><span class="sxs-lookup"><span data-stu-id="f4b4e-215">Response codes</span></span>

|<span data-ttu-id="f4b4e-216">Antwortcode</span><span class="sxs-lookup"><span data-stu-id="f4b4e-216">Response code</span></span>|<span data-ttu-id="f4b4e-217">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f4b4e-217">Description</span></span>|
|---|---|
| <span data-ttu-id="f4b4e-218">**201**</span><span class="sxs-lookup"><span data-stu-id="f4b4e-218">**201**</span></span> | <span data-ttu-id="f4b4e-219">Die Aktivität mit Signal wurde erfolgreich gesendet.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-219">The activity with signal is successfully sent</span></span> |
| <span data-ttu-id="f4b4e-220">**401**</span><span class="sxs-lookup"><span data-stu-id="f4b4e-220">**401**</span></span> | <span data-ttu-id="f4b4e-221">Die App antwortet mit einem ungültigen Token.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-221">The app responds with an invalid token.</span></span> |
| <span data-ttu-id="f4b4e-222">**403**</span><span class="sxs-lookup"><span data-stu-id="f4b4e-222">**403**</span></span> | <span data-ttu-id="f4b4e-223">Die App kann das Signal nicht senden.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-223">The app is unable to send the signal.</span></span> <span data-ttu-id="f4b4e-224">Dies kann aus verschiedenen Gründen geschehen, z. B. wenn der Mandantenadministrator die App deaktiviert, die App während der Livewebsitemigration blockiert wird und so weiter.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-224">This can happen due to various reasons such as the tenant admin disables the app, the app is blocked during live site migration, and so on.</span></span> <span data-ttu-id="f4b4e-225">In diesem Fall enthält die Nutzlast eine detaillierte Fehlermeldung.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-225">In this case, the payload contains a detailed error message.</span></span> |
| <span data-ttu-id="f4b4e-226">**404**</span><span class="sxs-lookup"><span data-stu-id="f4b4e-226">**404**</span></span> | <span data-ttu-id="f4b4e-227">Der Besprechungschat ist nicht vorhanden.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-227">The meeting chat does not exist.</span></span> |

## <a name="enable-your-app-for-teams-meetings"></a><span data-ttu-id="f4b4e-228">Aktivieren Ihrer App für Teams-Besprechungen</span><span class="sxs-lookup"><span data-stu-id="f4b4e-228">Enable your app for Teams meetings</span></span>

### <a name="update-your-app-manifest"></a><span data-ttu-id="f4b4e-229">Aktualisieren Des App-Manifests</span><span class="sxs-lookup"><span data-stu-id="f4b4e-229">Update your app manifest</span></span>

<span data-ttu-id="f4b4e-230">Die Funktionen der Besprechungs-App werden in Ihrem App-Manifest mit `configurableTabs` den Arrays , und `scopes` `context` deklariert.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-230">The meetings app capabilities are declared in your app manifest using the `configurableTabs`, `scopes`, and `context` arrays.</span></span> <span data-ttu-id="f4b4e-231">Scope definiert, für wen und der Kontext definiert, wo Ihre App verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-231">Scope defines to whom and context defines where your app is available.</span></span>

> [!NOTE]
> <span data-ttu-id="f4b4e-232">Versuchen Sie, Ihr App-Manifest mit dem [Manifestschema zu aktualisieren.](../resources/schema/manifest-schema-dev-preview.md)</span><span class="sxs-lookup"><span data-stu-id="f4b4e-232">Try updating your app manifest with the [manifest schema](../resources/schema/manifest-schema-dev-preview.md).</span></span>
> <span data-ttu-id="f4b4e-233">Apps in Besprechungen benötigen *Gruppenchatbereich.*</span><span class="sxs-lookup"><span data-stu-id="f4b4e-233">Apps in meetings need *groupchat* scope.</span></span> <span data-ttu-id="f4b4e-234">Der *Teambereich* funktioniert nur für Registerkarten in Kanälen.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-234">The *team* scope works for tabs in channels only.</span></span>

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
        "meetingSidePanel",
        "meetingStage"
     ]
    }
  ]
```
> [!NOTE]
> <span data-ttu-id="f4b4e-235">`meetingStage` ist derzeit nur in der Entwicklervorschau verfügbar.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-235">`meetingStage` is currently available in developer preview only.</span></span>

### <a name="context-property"></a><span data-ttu-id="f4b4e-236">Context-Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="f4b4e-236">Context property</span></span>

<span data-ttu-id="f4b4e-237">Mit der `context` Registerkarte und den Eigenschaften können Sie `scopes` bestimmen, wo Ihre App angezeigt werden muss.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-237">The tab `context` and `scopes` properties enable you to determine where your app must appear.</span></span> <span data-ttu-id="f4b4e-238">Registerkarten im `team` Bereich oder können mehrere `groupchat` Kontexte haben.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-238">Tabs in the `team` or `groupchat` scope can have more than one context.</span></span> <span data-ttu-id="f4b4e-239">Es folgen die Werte für die Eigenschaft, aus der Sie `context` alle oder einige der Werte verwenden können:</span><span class="sxs-lookup"><span data-stu-id="f4b4e-239">Following are the values for the `context` property from which you can use all or some of the values:</span></span>

|<span data-ttu-id="f4b4e-240">Wert</span><span class="sxs-lookup"><span data-stu-id="f4b4e-240">Value</span></span>|<span data-ttu-id="f4b4e-241">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f4b4e-241">Description</span></span>|
|---|---|
| <span data-ttu-id="f4b4e-242">**channelTab**</span><span class="sxs-lookup"><span data-stu-id="f4b4e-242">**channelTab**</span></span> | <span data-ttu-id="f4b4e-243">Eine Registerkarte in der Kopfzeile eines Teamkanals.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-243">A tab in the header of a team channel.</span></span> |
| <span data-ttu-id="f4b4e-244">**privateChatTab**</span><span class="sxs-lookup"><span data-stu-id="f4b4e-244">**privateChatTab**</span></span> | <span data-ttu-id="f4b4e-245">Eine Registerkarte in der Kopfzeile eines Gruppenchats zwischen einer Gruppe von Benutzern, die sich nicht im Kontext eines Teams oder einer Besprechung befindet.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-245">A tab in the header of a group chat between a set of users not in the context of a team or meeting.</span></span> |
| <span data-ttu-id="f4b4e-246">**meetingChatTab**</span><span class="sxs-lookup"><span data-stu-id="f4b4e-246">**meetingChatTab**</span></span> | <span data-ttu-id="f4b4e-247">Eine Registerkarte in der Kopfzeile eines Gruppenchats zwischen einer Gruppe von Benutzern im Kontext einer geplanten Besprechung.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-247">A tab in the header of a group chat between a set of users in the context of a scheduled meeting.</span></span> |
| <span data-ttu-id="f4b4e-248">**meetingDetailsTab**</span><span class="sxs-lookup"><span data-stu-id="f4b4e-248">**meetingDetailsTab**</span></span> | <span data-ttu-id="f4b4e-249">Eine Registerkarte in der Kopfzeile der Besprechungsdetailsansicht des Kalenders.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-249">A tab in the header of the meeting details view of the calendar.</span></span> |
| <span data-ttu-id="f4b4e-250">**meetingSidePanel**</span><span class="sxs-lookup"><span data-stu-id="f4b4e-250">**meetingSidePanel**</span></span> | <span data-ttu-id="f4b4e-251">Ein In-Meeting-Panel, das über die einheitliche Leiste (U-Leiste) geöffnet wird.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-251">An in-meeting panel opened via the unified bar (U-bar).</span></span> |
| <span data-ttu-id="f4b4e-252">**meetingStage**</span><span class="sxs-lookup"><span data-stu-id="f4b4e-252">**meetingStage**</span></span> | <span data-ttu-id="f4b4e-253">Eine App aus der Sidepanel kann für die Besprechungsphase freigegeben werden.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-253">An app from the sidepanel can be shared to the meeting stage.</span></span> |

> [!NOTE]
> <span data-ttu-id="f4b4e-254">`Context` wird derzeit auf mobilen Clients nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-254">`Context` property is currently not supported on mobile clients.</span></span>

## <a name="configure-your-app-for-meeting-scenarios"></a><span data-ttu-id="f4b4e-255">Konfigurieren Ihrer App für Besprechungsszenarien</span><span class="sxs-lookup"><span data-stu-id="f4b4e-255">Configure your app for meeting scenarios</span></span>

> [!NOTE]
> * <span data-ttu-id="f4b4e-256">Damit Ihre App im Registerkartenkatalog angezeigt wird, muss sie konfigurierbare Registerkarten und den Gruppenchatbereich unterstützen.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-256">For your app to be visible in the tab gallery it must support configurable tabs and the group chat scope.</span></span>
> * <span data-ttu-id="f4b4e-257">Mobile Clients unterstützen Registerkarten nur in Vor- und Nachbesprechungsphasen.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-257">Mobile clients support tabs only in pre and post meeting stages.</span></span>
> * <span data-ttu-id="f4b4e-258">Die Besprechungserfahrungen, die im Dialogfeld "Besprechung" und "Registerkarte" angezeigt werden, werden derzeit auf mobilen Clients nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-258">The in-meeting experiences that is in-meeting dialog box and tab is currently not supported on mobile clients.</span></span> <span data-ttu-id="f4b4e-259">Weitere Informationen finden Sie unter [Anleitungen für Registerkarten auf mobilen](../tabs/design/tabs-mobile.md) Geräten beim Erstellen Ihrer Registerkarten für Mobilgeräte.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-259">For more information, see [guidance for tabs on mobile](../tabs/design/tabs-mobile.md) when creating your tabs for mobile.</span></span>

### <a name="before-a-meeting"></a><span data-ttu-id="f4b4e-260">Vor einer Besprechung</span><span class="sxs-lookup"><span data-stu-id="f4b4e-260">Before a meeting</span></span>

<span data-ttu-id="f4b4e-261">Vor einer Besprechung können Benutzer Einer Besprechung Registerkarten, Bots und Messagingerweiterungen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-261">Before a meeting, users can add tabs, bots and messaging extensions to a meeting.</span></span> <span data-ttu-id="f4b4e-262">Benutzer mit Organisator- und Organisatorrollen können einer Besprechung Registerkarten hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-262">Users with organizer and presenter roles can add tabs to a meeting.</span></span>

<span data-ttu-id="f4b4e-263">**So fügen Sie einer Besprechung eine Registerkarte hinzu**</span><span class="sxs-lookup"><span data-stu-id="f4b4e-263">**To add a tab to a meeting**</span></span>

1. <span data-ttu-id="f4b4e-264">Wählen Sie in Ihrem Kalender eine Besprechung aus, der Sie eine Registerkarte hinzufügen möchten.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-264">In your calendar, select a meeting to which you want to add a tab.</span></span>
1. <span data-ttu-id="f4b4e-265">Wählen Sie die **Registerkarte Details** aus, und wählen Sie plus aus.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-265">Select the **Details** tab and select plus</span></span> <img src="~/assets/images/apps-in-meetings/plusbutton.png" alt="Plus button" width="30"/><span data-ttu-id="f4b4e-266">.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-266">.</span></span> <span data-ttu-id="f4b4e-267">Der Registerkartenkatalog wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-267">The tab gallery appears.</span></span>

    ![Pre-Meeting-Erfahrung](../assets/images/apps-in-meetings/PreMeeting.png)

1. <span data-ttu-id="f4b4e-269">Wählen Sie im Registerkartenkatalog die App aus, die Sie hinzufügen möchten, und führen Sie die erforderlichen Schritte aus.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-269">In the tab gallery, select the app that you want to add and follow the steps as required.</span></span> <span data-ttu-id="f4b4e-270">Die App wird als Registerkarte installiert.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-270">The app is installed as a tab.</span></span>
    > [!NOTE] 
    > <span data-ttu-id="f4b4e-271">Derzeit wird das Abrufen von Besprechungsdetails und Teilnehmerinformationen auf der Registerkarte Besprechungen nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-271">Currently, in meetings tab, getting meeting details and participant information is not supported.</span></span>

<span data-ttu-id="f4b4e-272">**So fügen Sie einer Besprechung eine Messagingerweiterung hinzu**</span><span class="sxs-lookup"><span data-stu-id="f4b4e-272">**To add a messaging extension to a meeting**</span></span>

1. <span data-ttu-id="f4b4e-273">Wählen Sie die Ellipsen oder das Überlaufmenü &#x25CF;&#x25CF;&#x25CF; sich im Bereich Verfassen von Nachrichten im Chat befindet.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-273">Select the ellipses or overflow menu &#x25CF;&#x25CF;&#x25CF; located in the compose message area in the chat.</span></span>
1. <span data-ttu-id="f4b4e-274">Wählen Sie die App aus, die Sie hinzufügen möchten, und führen Sie die Schritte nach Bedarf aus.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-274">Select the app that you want to add and follow the steps as required.</span></span> <span data-ttu-id="f4b4e-275">Die App wird als Messagingerweiterung installiert.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-275">The app is installed as a messaging extension.</span></span>

<span data-ttu-id="f4b4e-276">**So fügen Sie einer Besprechung einen Bot hinzu**</span><span class="sxs-lookup"><span data-stu-id="f4b4e-276">**To add a bot to a meeting**</span></span>

<span data-ttu-id="f4b4e-277">Geben Sie in einem Besprechungschat den **@** Schlüssel ein, und wählen **Sie Bots erhalten aus.**</span><span class="sxs-lookup"><span data-stu-id="f4b4e-277">In a meeting chat enter the **@** key and select **Get bots**.</span></span>

> [!NOTE]
> * <span data-ttu-id="f4b4e-278">Die Benutzeridentität muss mithilfe von [Tabs SSO bestätigt werden.](../tabs/how-to/authentication/auth-aad-sso.md)</span><span class="sxs-lookup"><span data-stu-id="f4b4e-278">The user identity must be confirmed using [Tabs SSO](../tabs/how-to/authentication/auth-aad-sso.md).</span></span> <span data-ttu-id="f4b4e-279">Nach der Authentifizierung kann die App die Benutzerrolle mithilfe der `GetParticipant` API abrufen.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-279">After authentication, the app can retrieve the user role using the `GetParticipant` API.</span></span>
> * <span data-ttu-id="f4b4e-280">Basierend auf der Benutzerrolle kann die App rollenspezifische Benutzeroberflächen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-280">Based on the user role, the app has the capability to provide role specific experiences.</span></span> <span data-ttu-id="f4b4e-281">Beispielsweise ermöglicht eine Abruf-App nur Organisatoren und Organisatoren, eine neue Umfrage zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-281">For example, a polling app allows only organizers and presenters to create a new poll.</span></span>
> * <span data-ttu-id="f4b4e-282">Rollenzuweisungen können geändert werden, während eine Besprechung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-282">Role assignments can be changed while a meeting is in progress.</span></span> <span data-ttu-id="f4b4e-283">Weitere Informationen finden Sie [unter Rollen in einer Teams-Besprechung](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).</span><span class="sxs-lookup"><span data-stu-id="f4b4e-283">For more information, see [roles in a Teams meeting](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).</span></span>

### <a name="during-a-meeting"></a><span data-ttu-id="f4b4e-284">Während einer Besprechung</span><span class="sxs-lookup"><span data-stu-id="f4b4e-284">During a meeting</span></span>

#### <a name="sidepanel"></a><span data-ttu-id="f4b4e-285">sidePanel</span><span class="sxs-lookup"><span data-stu-id="f4b4e-285">sidePanel</span></span>

<span data-ttu-id="f4b4e-286">Mit dem sidePanel können Sie die Erfahrungen in einer Besprechung anpassen, mit denen Organisatoren und Organisatoren unterschiedliche Ansichten und Aktionen ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-286">With the sidePanel, you can customize experiences in a meeting that enable organizers and presenters to have different set of views and actions.</span></span> <span data-ttu-id="f4b4e-287">In Ihrem App-Manifest müssen Sie dem Kontextarray sidePanel hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-287">In your app manifest, you must add sidePanel to the context array.</span></span> <span data-ttu-id="f4b4e-288">In der Besprechung und in allen Szenarien wird die App auf einer Registerkarte in der Besprechung gerendert, die 320 Pixel breit ist.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-288">In the meeting and in all scenarios, the app is rendered in an in-meeting tab that is 320 pixels in width.</span></span> <span data-ttu-id="f4b4e-289">Weitere Informationen finden Sie unter [FrameContext-Schnittstelle](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/framecontext?view=msteams-client-js-latest&preserve-view=true
).</span><span class="sxs-lookup"><span data-stu-id="f4b4e-289">For more information, see [FrameContext interface](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/framecontext?view=msteams-client-js-latest&preserve-view=true
).</span></span>

<span data-ttu-id="f4b4e-290">Informationen zur Verwendung der `userContext` API zum Entsprechend routen von Anforderungen finden Sie unter Teams [SDK](../tabs/how-to/access-teams-context.md#user-context).</span><span class="sxs-lookup"><span data-stu-id="f4b4e-290">To use the `userContext` API to route requests accordingly, see [Teams SDK](../tabs/how-to/access-teams-context.md#user-context).</span></span> <span data-ttu-id="f4b4e-291">Registerkarten finden Sie unter [Teams-Authentifizierungsfluss.](../tabs/how-to/authentication/auth-flow-tab.md)</span><span class="sxs-lookup"><span data-stu-id="f4b4e-291">See [Teams authentication flow for tabs](../tabs/how-to/authentication/auth-flow-tab.md).</span></span> <span data-ttu-id="f4b4e-292">Der Authentifizierungsfluss für Registerkarten ähnelt dem Authentifizierungsfluss für Websites.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-292">Authentication flow for tabs is very similar to the auth flow for websites.</span></span> <span data-ttu-id="f4b4e-293">Registerkarten können also OAuth 2.0 direkt verwenden.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-293">So tabs can use OAuth 2.0 directly.</span></span> <span data-ttu-id="f4b4e-294">Siehe Microsoft [Identity Platform und OAuth 2.0 Authorization Code Flow](/azure/active-directory/develop/v2-oauth2-auth-code-flow).</span><span class="sxs-lookup"><span data-stu-id="f4b4e-294">See, [Microsoft identity platform and OAuth 2.0 authorization code flow](/azure/active-directory/develop/v2-oauth2-auth-code-flow).</span></span>

<span data-ttu-id="f4b4e-295">Die Messagingerweiterung funktioniert wie erwartet, wenn sich ein Benutzer in einer Besprechungsansicht befindet und der Benutzer Nachrichtenerweiterungskarten verfassen kann.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-295">Messaging extension works as expected when a user is in an in-meeting view and the user can post compose message extension cards.</span></span> <span data-ttu-id="f4b4e-296">AppName in-meeting ist eine QuickInfo, in der der App-Name in der Besprechungs-U-Leiste steht.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-296">AppName in-meeting is a tooltip that states the app name in-meeting U-bar.</span></span>

> [!NOTE]
> <span data-ttu-id="f4b4e-297">Verwenden Sie Version 1.9.0 des [Teams SDK,](https://docs.microsoft.com/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) um seitenseitige Panel hochzuladen, da Versionen vor dem System keine Seitenleiste unterstützen.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-297">Use version 1.9.0 of [Teams SDK](https://docs.microsoft.com/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) to upload side panel, as versions prior to it do not support side panel.</span></span>

#### <a name="in-meeting-dialog"></a><span data-ttu-id="f4b4e-298">Dialogfeld "Besprechung"</span><span class="sxs-lookup"><span data-stu-id="f4b4e-298">In-meeting dialog</span></span>

<span data-ttu-id="f4b4e-299">Das Dialogfeld in der Besprechung kann verwendet werden, um Teilnehmer während der Besprechung zu engagieren und Während der Besprechung Informationen oder Feedback zu sammeln.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-299">The in-meeting dialog box can be used to engage participants during the meeting and collect information or feedback during the meeting.</span></span> <span data-ttu-id="f4b4e-300">Verwenden Sie die [`NotificationSignal`](/graph/api/resources/notifications-api-overview?view=graph-rest-beta&preserve-view=true) API, um zu signalisieren, dass eine Blasenbenachrichtigung ausgelöst werden muss.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-300">Use the [`NotificationSignal`](/graph/api/resources/notifications-api-overview?view=graph-rest-beta&preserve-view=true) API to signal that a bubble notification must be triggered.</span></span> <span data-ttu-id="f4b4e-301">Geben Sie im Rahmen der Nutzlast der Benachrichtigungsanforderung die URL an, in der der anzuzeigende Inhalt gehostet wird.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-301">As part of the notification request payload, include the URL where the content to be shown is hosted.</span></span>

<span data-ttu-id="f4b4e-302">Im Besprechungsdialogfeld darf kein Aufgabenmodul verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-302">In-meeting dialog must not use task module.</span></span> <span data-ttu-id="f4b4e-303">Das Aufgabenmodul wird in einem Besprechungschat nicht aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-303">Task module is not invoked in a meeting chat.</span></span> <span data-ttu-id="f4b4e-304">Eine externe Ressourcen-URL wird zum Anzeigen von Inhaltsblasen in einer Besprechung verwendet.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-304">An external resource URL is used to display content bubble in a meeting.</span></span> <span data-ttu-id="f4b4e-305">Sie können die Methode `submitTask` verwenden, um Daten in einem Besprechungschat zu übermitteln.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-305">You can use the `submitTask` method to submit data in a meeting chat.</span></span>

> [!NOTE]
> * <span data-ttu-id="f4b4e-306">Sie müssen die [submitTask()-Funktion](../task-modules-and-cards/task-modules/task-modules-bots.md#submitting-the-result-of-a-task-module) aufrufen, um automatisch zu schließen, nachdem ein Benutzer eine Aktion in der Webansicht ausgeführt hat.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-306">You must invoke the [submitTask()](../task-modules-and-cards/task-modules/task-modules-bots.md#submitting-the-result-of-a-task-module) function to dismiss automatically after a user takes an action in the web-view.</span></span> <span data-ttu-id="f4b4e-307">Dies ist eine Anforderung für die App-Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-307">This is a requirement for app submission.</span></span> <span data-ttu-id="f4b4e-308">Weitere Informationen finden Sie unter [Teams SDK task module](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="f4b4e-308">For more information, see [Teams SDK task module](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true).</span></span>
> * <span data-ttu-id="f4b4e-309">Wenn Sie möchten, dass Ihre App anonyme Benutzer unterstützt, muss die Nutzlast der ursprünglichen Aufrufanforderung auf den Anforderungsmetadaten im Objekt und nicht auf den `from.id` `from` `from.aadObjectId` Anforderungsmetadaten beruhen.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-309">If you want your app to support anonymous users, your initial invoke request payload must rely on the `from.id` request metadata in the `from` object, not the `from.aadObjectId` request metadata.</span></span> <span data-ttu-id="f4b4e-310">`from.id` ist die Benutzer-ID und `from.aadObjectId` die Azure Active Directory (AAD)-ID des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-310">`from.id` is the user ID and `from.aadObjectId` is the Azure Active Directory (AAD) ID of the user.</span></span> <span data-ttu-id="f4b4e-311">Weitere Informationen finden Sie unter [Verwenden von Aufgabenmodulen in Registerkarten](../task-modules-and-cards/task-modules/task-modules-tabs.md) und [Erstellen und Senden des Aufgabenmoduls.](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request)</span><span class="sxs-lookup"><span data-stu-id="f4b4e-311">For more information, see [using task modules in tabs](../task-modules-and-cards/task-modules/task-modules-tabs.md) and [create and send the task module](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request).</span></span>

#### <a name="share-to-stage"></a><span data-ttu-id="f4b4e-312">Freigeben in der Phase</span><span class="sxs-lookup"><span data-stu-id="f4b4e-312">Share to stage</span></span> 

> [!NOTE]
> * <span data-ttu-id="f4b4e-313">Diese Funktion ist derzeit nur in der Entwicklervorschau verfügbar.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-313">This capability is currently available in developer preview only.</span></span>
> * <span data-ttu-id="f4b4e-314">Um dieses Feature verwenden zu können, muss die App eine Besprechungs-Sidepanel unterstützen.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-314">To use this feature, the app must support an in-meeting sidepanel.</span></span>


<span data-ttu-id="f4b4e-315">Mit dieser Funktion können Entwickler eine App für die Besprechungsphase freigeben.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-315">This capability gives developers the ability to share an app to the meeting stage.</span></span> <span data-ttu-id="f4b4e-316">Durch aktivieren der Freigabe für die Besprechungsphase können Besprechungsteilnehmer in Echtzeit zusammenarbeiten.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-316">By enabling share to the meeting stage, meeting participants can collaborate in real-time.</span></span> 

<span data-ttu-id="f4b4e-317">Der erforderliche Kontext befindet `meetingStage` sich im App-Manifest.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-317">The required context is `meetingStage` in the app manifest.</span></span> <span data-ttu-id="f4b4e-318">Voraussetzung dafür ist der `meetingSidePanel` Kontext.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-318">A prerequisite for this is to have the `meetingSidePanel` context.</span></span> <span data-ttu-id="f4b4e-319">Dadurch wird die **Schaltfläche Freigeben** im Sidepanel wie in der folgenden Abbildung depeziiert aktiviert:</span><span class="sxs-lookup"><span data-stu-id="f4b4e-319">This enables the **Share** button in the sidepanel as depecited in the following image:</span></span>

  ![share_to_stage_during_meeting-Erfahrung](~/assets/images/apps-in-meetings/share_to_stage_during_meeting.png)

<span data-ttu-id="f4b4e-321">Die manifeste Änderung, die zum Aktivieren dieser Funktion erforderlich ist, lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="f4b4e-321">The manifest change that is needed to enable this capability is as follows:</span></span> 

```json

"configurableTabs": [
    {
      "configurationUrl": "https://contoso.com/teamstab/configure",
      "canUpdateConfiguration": true,
      "scopes": [
        "groupchat"
      ],
      "context":[
        
        "meetingSidePanel",
        "meetingStage"
     ]
    }
  ]
```



### <a name="after-a-meeting"></a><span data-ttu-id="f4b4e-322">Nach einer Besprechung</span><span class="sxs-lookup"><span data-stu-id="f4b4e-322">After a meeting</span></span>

<span data-ttu-id="f4b4e-323">Die Konfigurationen nach der Besprechung und vor der Besprechung sind äquivalent.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-323">The post-meeting and pre-meeting configurations are equivalent.</span></span>

## <a name="code-sample"></a><span data-ttu-id="f4b4e-324">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="f4b4e-324">Code sample</span></span>

|<span data-ttu-id="f4b4e-325">Beispielname</span><span class="sxs-lookup"><span data-stu-id="f4b4e-325">Sample name</span></span> | <span data-ttu-id="f4b4e-326">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f4b4e-326">Description</span></span> | <span data-ttu-id="f4b4e-327">.NET</span><span class="sxs-lookup"><span data-stu-id="f4b4e-327">.NET</span></span> | <span data-ttu-id="f4b4e-328">Node.js</span><span class="sxs-lookup"><span data-stu-id="f4b4e-328">Node.js</span></span> |
|----------------|-----------------|--------------|--------------|
| <span data-ttu-id="f4b4e-329">Erweiterbarkeit von Besprechungen</span><span class="sxs-lookup"><span data-stu-id="f4b4e-329">Meetings extensibility</span></span> | <span data-ttu-id="f4b4e-330">Beispiel für die Erweiterbarkeit von Microsoft Teams-Besprechungen zum Übergeben von Token.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-330">Microsoft Teams meeting extensibility sample for passing tokens.</span></span> | [<span data-ttu-id="f4b4e-331">View</span><span class="sxs-lookup"><span data-stu-id="f4b4e-331">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/csharp) | |
| <span data-ttu-id="f4b4e-332">Besprechungsinhaltsblasen-Bot</span><span class="sxs-lookup"><span data-stu-id="f4b4e-332">Meeting content bubble bot</span></span> | <span data-ttu-id="f4b4e-333">Beispiel für die Erweiterbarkeit von Microsoft Teams-Besprechungen für die Interaktion mit dem Inhaltsblasenbot in einer Besprechung.</span><span class="sxs-lookup"><span data-stu-id="f4b4e-333">Microsoft Teams meeting extensibility sample for interacting with content bubble bot in a meeting.</span></span> | [<span data-ttu-id="f4b4e-334">View</span><span class="sxs-lookup"><span data-stu-id="f4b4e-334">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/csharp) |  [<span data-ttu-id="f4b4e-335">View</span><span class="sxs-lookup"><span data-stu-id="f4b4e-335">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/nodejs)|

## <a name="see-also"></a><span data-ttu-id="f4b4e-336">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="f4b4e-336">See also</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f4b4e-337">Entwurfsrichtlinien für Besprechungsdialogdialog</span><span class="sxs-lookup"><span data-stu-id="f4b4e-337">In-meeting dialog design guidelines</span></span>](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)
> [!div class="nextstepaction"]
> [<span data-ttu-id="f4b4e-338">Teams-Authentifizierungsfluss für Registerkarten</span><span class="sxs-lookup"><span data-stu-id="f4b4e-338">Teams authentication flow for tabs</span></span>](../tabs/how-to/authentication/auth-flow-tab.md)
