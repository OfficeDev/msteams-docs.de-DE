---
title: Voraussetzungen und API-Verweise für Apps in Teams-Besprechungen
author: laujan
description: Arbeiten mit Apps für Teams Besprechungen
ms.topic: conceptual
ms.author: lajanuar
localization_priority: Normal
keywords: Teams-Apps – Benutzerteilnehmer-Rollen-API für Besprechungen
ms.openlocfilehash: f42e827801e21bbd039f52dbb685d4559ae5cf81
ms.sourcegitcommit: 37325179a532897fafbe827dcf9a7ca5fa5e7d0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2021
ms.locfileid: "52853508"
---
# <a name="prerequisites-and-api-references-for-apps-in-teams-meetings"></a><span data-ttu-id="57ae7-104">Voraussetzungen und API-Verweise für Apps in Teams-Besprechungen</span><span class="sxs-lookup"><span data-stu-id="57ae7-104">Prerequisites and API references for apps in Teams meetings</span></span>

<span data-ttu-id="57ae7-105">Um die Funktionen Ihrer Apps über den gesamten Besprechungslebenszyklus zu erweitern, können Sie mit Teams mit Apps für Teams Besprechungen arbeiten.</span><span class="sxs-lookup"><span data-stu-id="57ae7-105">To expand the capabilities of your apps across the meeting lifecycle, Teams enables you to work with apps for Teams meetings.</span></span> <span data-ttu-id="57ae7-106">Sie müssen die Voraussetzungen durchlaufen, und Sie können die Api-Verweise auf Besprechungs-Apps verwenden, um die Besprechungserfahrung zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="57ae7-106">You must  go through the prerequisites and you can use the meeting apps API references to enhance the meeting experience.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="57ae7-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="57ae7-107">Prerequisites</span></span>

<span data-ttu-id="57ae7-108">Bevor Sie mit Apps für Teams Besprechungen arbeiten, müssen Sie Folgendes verstehen:</span><span class="sxs-lookup"><span data-stu-id="57ae7-108">Before you work with apps for Teams meetings, you must have an understanding of the following:</span></span>

* <span data-ttu-id="57ae7-109">Sie müssen über Kenntnisse in der Entwicklung von Teams-Apps verfügen.</span><span class="sxs-lookup"><span data-stu-id="57ae7-109">You must have knowledge of how to develop Teams apps.</span></span> <span data-ttu-id="57ae7-110">Weitere Informationen finden Sie unter [Teams App-Entwicklung.](../overview.md)</span><span class="sxs-lookup"><span data-stu-id="57ae7-110">For more information, see [Teams app development](../overview.md).</span></span>

* <span data-ttu-id="57ae7-111">Sie müssen das Teams App-Manifest aktualisieren, um anzugeben, dass die App für Besprechungen verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="57ae7-111">You must update the Teams app manifest to indicate that the app is available for meetings.</span></span> <span data-ttu-id="57ae7-112">Weitere Informationen finden Sie unter [App-Manifest.](enable-and-configure-your-app-for-teams-meetings.md#update-your-app-manifest)</span><span class="sxs-lookup"><span data-stu-id="57ae7-112">For more information, see [app manifest](enable-and-configure-your-app-for-teams-meetings.md#update-your-app-manifest).</span></span>

* <span data-ttu-id="57ae7-113">Ihre App muss konfigurierbare Registerkarten im Gruppenchatbereich unterstützen, damit Ihre App im Besprechungslebenszyklus als Registerkarte funktioniert. Weitere Informationen finden Sie unter [Gruppenchatbereich](../resources/schema/manifest-schema.md#configurabletabs) und [Erstellen einer Gruppenregisterkarte.](../build-your-first-app/build-channel-tab.md)</span><span class="sxs-lookup"><span data-stu-id="57ae7-113">Your app must support configurable tabs in the groupchat scope, for your app to function in the meeting lifecycle as a tab. For more information, see [groupchat scope](../resources/schema/manifest-schema.md#configurabletabs) and [build a group tab](../build-your-first-app/build-channel-tab.md).</span></span>

* <span data-ttu-id="57ae7-114">Sie müssen allgemeine Teams Entwurfsrichtlinien für Registerkarten für Szenarien vor und nach der Besprechung einhalten.</span><span class="sxs-lookup"><span data-stu-id="57ae7-114">You must adhere to general Teams tab design guidelines for pre and post-meeting scenarios.</span></span> <span data-ttu-id="57ae7-115">Informationen zu Erfahrungen während Besprechungen finden Sie auf der Registerkarte "Besprechung" und in den Entwurfsrichtlinien des Dialogfelds "In-Meeting".</span><span class="sxs-lookup"><span data-stu-id="57ae7-115">For experiences during meetings, refer to the in-meeting tab and in-meeting dialog design guidelines.</span></span> <span data-ttu-id="57ae7-116">Weitere Informationen finden Sie unter [Teams Entwurfsrichtlinien für Registerkarten,](../tabs/design/tabs.md) [Entwurfsrichtlinien für Registerkarten in Besprechungen](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-tab)und Entwurfsrichtlinien für [Dialogfelder in Besprechungen.](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)</span><span class="sxs-lookup"><span data-stu-id="57ae7-116">For more information, see [Teams tab design guidelines](../tabs/design/tabs.md), [in-meeting tab design guidelines](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-tab), and [in-meeting dialog design guidelines](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-dialog).</span></span>

* <span data-ttu-id="57ae7-117">Sie müssen den `groupchat` Bereich unterstützen, um Ihre App in Chats vor und nach der Besprechung zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="57ae7-117">You must support the `groupchat` scope to enable your app in pre-meeting and post-meeting chats.</span></span> <span data-ttu-id="57ae7-118">Mit der App-Erfahrung vor der Besprechung können Sie Besprechungs-Apps suchen und hinzufügen und Aufgaben vor der Besprechung ausführen.</span><span class="sxs-lookup"><span data-stu-id="57ae7-118">With the pre-meeting app experience, you can find and add meeting apps and perform pre-meeting tasks.</span></span> <span data-ttu-id="57ae7-119">Mit der App-Erfahrung nach der Besprechung können Sie die Ergebnisse der Besprechung anzeigen, z. B. Umfrageergebnisse oder Feedback.</span><span class="sxs-lookup"><span data-stu-id="57ae7-119">With post-meeting app experience, you can view the results of the meeting, such as poll survey results or feedback.</span></span>

* <span data-ttu-id="57ae7-120">Die URL-Parameter der Besprechungs-API müssen `meetingId` über `userId` , und `tenantId` verfügen.</span><span class="sxs-lookup"><span data-stu-id="57ae7-120">Meeting API URL parameters must have `meetingId`, `userId`, and `tenantId`.</span></span> <span data-ttu-id="57ae7-121">Diese sind als Teil der Teams Client SDK- und Bot-Aktivität verfügbar.</span><span class="sxs-lookup"><span data-stu-id="57ae7-121">These are available as part of the Teams Client SDK and bot activity.</span></span> <span data-ttu-id="57ae7-122">Darüber hinaus können Sie mithilfe der [SSO-Authentifizierung](../tabs/how-to/authentication/auth-aad-sso.md)der Registerkarte zuverlässige Informationen zu Benutzer-ID und Mandanten-ID abrufen.</span><span class="sxs-lookup"><span data-stu-id="57ae7-122">In addition, you can retrieve reliable information for user ID and tenant ID using [tab SSO authentication](../tabs/how-to/authentication/auth-aad-sso.md).</span></span>

* <span data-ttu-id="57ae7-123">Die `GetParticipant` API muss über eine Bot-Registrierung und -ID verfügen, um Authentifizierungstoken zu generieren.</span><span class="sxs-lookup"><span data-stu-id="57ae7-123">The `GetParticipant` API must have a bot registration and ID to generate auth tokens.</span></span> <span data-ttu-id="57ae7-124">Weitere Informationen finden Sie unter [Bot-Registrierung und -ID.](../build-your-first-app/build-bot.md)</span><span class="sxs-lookup"><span data-stu-id="57ae7-124">For more information, see [bot registration and ID](../build-your-first-app/build-bot.md).</span></span>

* <span data-ttu-id="57ae7-125">Damit Ihre App in Echtzeit aktualisiert werden kann, muss sie basierend auf den Ereignisaktivitäten in der Besprechung auf dem neuesten Stand sein.</span><span class="sxs-lookup"><span data-stu-id="57ae7-125">For your app to update in real time, it must be up-to-date based on event activities in the meeting.</span></span> <span data-ttu-id="57ae7-126">Diese Ereignisse können sich innerhalb des Besprechungsdialogfelds und in anderen Phasen des Besprechungslebenszyklus befinden.</span><span class="sxs-lookup"><span data-stu-id="57ae7-126">These events can be within the in-meeting dialog box and other stages across the meeting lifecycle.</span></span> <span data-ttu-id="57ae7-127">Das Dialogfeld in besprechungsinternen Besprechungen finden Sie unter `bot Id` Abschlussparameter in `NotificationSignal` der API.</span><span class="sxs-lookup"><span data-stu-id="57ae7-127">For the in-meeting dialog box, see completion `bot Id` parameter in `NotificationSignal` API.</span></span>

<span data-ttu-id="57ae7-128">Nachdem Sie die Voraussetzungen erfüllt haben, können Sie die API-Referenzen für Besprechungs-Apps `GetUserContext` `GetParticipant` verwenden, mit `NotificationSignal` denen Sie mithilfe von Attributen auf Informationen zugreifen und relevante Inhalte anzeigen können.</span><span class="sxs-lookup"><span data-stu-id="57ae7-128">After you have gone through the prerequisites, you can use the meeting apps API references `GetUserContext`, `GetParticipant`, and `NotificationSignal` that enable you to access information using attributes and display relevant content.</span></span>

## <a name="meeting-apps-api-references"></a><span data-ttu-id="57ae7-129">API-Referenzen für Besprechungs-Apps</span><span class="sxs-lookup"><span data-stu-id="57ae7-129">Meeting apps API references</span></span>

<span data-ttu-id="57ae7-130">Die neuen Besprechungserweiterungen bieten Ihnen APIs, die die Besprechungsumgebung transformieren.</span><span class="sxs-lookup"><span data-stu-id="57ae7-130">The new meeting extensibilities provide you with APIs that transform the meeting experience.</span></span> <span data-ttu-id="57ae7-131">Mit dieser neuen Funktion können Sie Apps erstellen oder vorhandene Apps in den Besprechungslebenszyklus integrieren.</span><span class="sxs-lookup"><span data-stu-id="57ae7-131">With this new capability, you can build apps or integrate existing apps within the meeting lifecycle.</span></span> <span data-ttu-id="57ae7-132">Sie können die APIs verwenden, um Ihre App auf die Besprechung aufmerksam zu machen.</span><span class="sxs-lookup"><span data-stu-id="57ae7-132">You can use the APIs to make your app aware of the meeting.</span></span> <span data-ttu-id="57ae7-133">Sie können auswählen, welche APIs Sie verwenden möchten, um die Besprechungserfahrung zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="57ae7-133">You can choose which APIs you want to use to enhance the meeting experience.</span></span>

<span data-ttu-id="57ae7-134">Die folgende Tabelle enthält eine Liste dieser APIs:</span><span class="sxs-lookup"><span data-stu-id="57ae7-134">The following table provides a list of these APIs:</span></span>

|<span data-ttu-id="57ae7-135">API</span><span class="sxs-lookup"><span data-stu-id="57ae7-135">API</span></span>|<span data-ttu-id="57ae7-136">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="57ae7-136">Description</span></span>|<span data-ttu-id="57ae7-137">Anforderung</span><span class="sxs-lookup"><span data-stu-id="57ae7-137">Request</span></span>|<span data-ttu-id="57ae7-138">Quelle</span><span class="sxs-lookup"><span data-stu-id="57ae7-138">Source</span></span>|
|---|---|----|---|
|<span data-ttu-id="57ae7-139">**GetUserContext**</span><span class="sxs-lookup"><span data-stu-id="57ae7-139">**GetUserContext**</span></span>| <span data-ttu-id="57ae7-140">Mit dieser API können Sie Kontextinformationen abrufen, um relevante Inhalte auf einer Teams Registerkarte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="57ae7-140">This API enables you to get contextual information to display relevant content in a Teams tab.</span></span> |<span data-ttu-id="57ae7-141">_**microsoftTeams.getContext( ( ) => { /*...\* / } )*\*_</span><span class="sxs-lookup"><span data-stu-id="57ae7-141">_**microsoftTeams.getContext( ( ) => {  /*...*/ } )**_</span></span>|<span data-ttu-id="57ae7-142">Microsoft Teams Client SDK</span><span class="sxs-lookup"><span data-stu-id="57ae7-142">Microsoft Teams Client SDK</span></span>|
|<span data-ttu-id="57ae7-143">**GetParticipant**</span><span class="sxs-lookup"><span data-stu-id="57ae7-143">**GetParticipant**</span></span>| <span data-ttu-id="57ae7-144">Diese API ermöglicht es einem Bot, Teilnehmerinformationen nach Besprechungs-ID und Teilnehmer-ID abzurufen.</span><span class="sxs-lookup"><span data-stu-id="57ae7-144">This API allows a bot to fetch participant information by meeting ID and participant ID.</span></span> |<span data-ttu-id="57ae7-145">**GET** _**/v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}**_</span><span class="sxs-lookup"><span data-stu-id="57ae7-145">**GET** _**/v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}**_</span></span> |<span data-ttu-id="57ae7-146">Microsoft Bot Framework Sdk</span><span class="sxs-lookup"><span data-stu-id="57ae7-146">Microsoft Bot Framework SDK</span></span>|
|<span data-ttu-id="57ae7-147">**NotificationSignal**</span><span class="sxs-lookup"><span data-stu-id="57ae7-147">**NotificationSignal**</span></span> | <span data-ttu-id="57ae7-148">Mit dieser API können Sie Besprechungssignale bereitstellen, die mithilfe der vorhandenen Unterhaltungsbenachrichtigungs-API für den Benutzer-Bot-Chat übermittelt werden.</span><span class="sxs-lookup"><span data-stu-id="57ae7-148">This API enables you to provide meeting signals that are delivered using the existing conversation notification API for user-bot chat.</span></span> <span data-ttu-id="57ae7-149">Sie können ein Signal basierend auf einer Benutzeraktion senden, die ein Dialogfeld in der Besprechung anzeigt.</span><span class="sxs-lookup"><span data-stu-id="57ae7-149">It allows you to signal based on user action that shows an in-meeting dialog box.</span></span> |<span data-ttu-id="57ae7-150">**POST** _**/v3/conversations/{conversationId}/activities**_</span><span class="sxs-lookup"><span data-stu-id="57ae7-150">**POST** _**/v3/conversations/{conversationId}/activities**_</span></span>|<span data-ttu-id="57ae7-151">Microsoft Bot Framework Sdk</span><span class="sxs-lookup"><span data-stu-id="57ae7-151">Microsoft Bot Framework SDK</span></span>|

### <a name="getusercontext-api"></a><span data-ttu-id="57ae7-152">GetUserContext-API</span><span class="sxs-lookup"><span data-stu-id="57ae7-152">GetUserContext API</span></span>

<span data-ttu-id="57ae7-153">Informationen zum Identifizieren und Abrufen von Kontextinformationen für Ihre Registerkarteninhalte finden Sie unter Abrufen des [Kontexts für Ihre Teams Registerkarte.](../tabs/how-to/access-teams-context.md#getting-context-by-using-the-microsoft-teams-javascript-library) `meetingId`wird von einer Registerkarte verwendet, wenn sie im Besprechungskontext ausgeführt wird, und wird für die Antwortnutzlast hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="57ae7-153">To identify and retrieve contextual information for your tab content, see [get context for your Teams tab](../tabs/how-to/access-teams-context.md#getting-context-by-using-the-microsoft-teams-javascript-library). `meetingId` is used by a tab when running in the meeting context and is added for the response payload.</span></span>

### <a name="getparticipant-api"></a><span data-ttu-id="57ae7-154">GetParticipant-API</span><span class="sxs-lookup"><span data-stu-id="57ae7-154">GetParticipant API</span></span>

> [!NOTE]
> * <span data-ttu-id="57ae7-155">Teilnehmerrollen nicht zwischenspeichern, da der Besprechungsorganisator die Rollen jederzeit ändern kann.</span><span class="sxs-lookup"><span data-stu-id="57ae7-155">Do not cache participant roles since the meeting organizer can change the roles any time.</span></span>
> * <span data-ttu-id="57ae7-156">Teams unterstützt derzeit keine großen Verteilerlisten oder Listengrößen von mehr als 350 Teilnehmern für die `GetParticipant` API.</span><span class="sxs-lookup"><span data-stu-id="57ae7-156">Teams does not currently support large distribution lists or roster sizes of more than 350 participants for the `GetParticipant` API.</span></span>

<span data-ttu-id="57ae7-157">Die `GetParticipant` API ermöglicht es einem Bot, Teilnehmerinformationen nach Besprechungs-ID und Teilnehmer-ID abzurufen.</span><span class="sxs-lookup"><span data-stu-id="57ae7-157">The `GetParticipant` API allows a bot to fetch participant information by meeting ID and participant ID.</span></span> <span data-ttu-id="57ae7-158">Die API enthält Abfrageparameter, Beispiele und Antwortcodes.</span><span class="sxs-lookup"><span data-stu-id="57ae7-158">The API includes query parameters, examples, and response codes.</span></span>

#### <a name="query-parameters"></a><span data-ttu-id="57ae7-159">Abfrageparameter</span><span class="sxs-lookup"><span data-stu-id="57ae7-159">Query parameters</span></span>

<span data-ttu-id="57ae7-160">Die `GetParticipant` API enthält die folgenden Abfrageparameter:</span><span class="sxs-lookup"><span data-stu-id="57ae7-160">The `GetParticipant` API includes the following query parameters:</span></span>

|<span data-ttu-id="57ae7-161">Wert</span><span class="sxs-lookup"><span data-stu-id="57ae7-161">Value</span></span>|<span data-ttu-id="57ae7-162">Typ</span><span class="sxs-lookup"><span data-stu-id="57ae7-162">Type</span></span>|<span data-ttu-id="57ae7-163">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="57ae7-163">Required</span></span>|<span data-ttu-id="57ae7-164">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="57ae7-164">Description</span></span>|
|---|---|----|---|
|<span data-ttu-id="57ae7-165">**meetingId**</span><span class="sxs-lookup"><span data-stu-id="57ae7-165">**meetingId**</span></span>| <span data-ttu-id="57ae7-166">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="57ae7-166">String</span></span> | <span data-ttu-id="57ae7-167">Ja</span><span class="sxs-lookup"><span data-stu-id="57ae7-167">Yes</span></span> | <span data-ttu-id="57ae7-168">Der Besprechungsbezeichner ist über Bot Invoke und Teams Client SDK verfügbar.</span><span class="sxs-lookup"><span data-stu-id="57ae7-168">The meeting identifier is available through Bot Invoke and Teams Client SDK.</span></span>|
|<span data-ttu-id="57ae7-169">**participantId**</span><span class="sxs-lookup"><span data-stu-id="57ae7-169">**participantId**</span></span>| <span data-ttu-id="57ae7-170">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="57ae7-170">String</span></span> | <span data-ttu-id="57ae7-171">Ja</span><span class="sxs-lookup"><span data-stu-id="57ae7-171">Yes</span></span> | <span data-ttu-id="57ae7-172">Die Teilnehmer-ID ist die Benutzer-ID.</span><span class="sxs-lookup"><span data-stu-id="57ae7-172">The participant ID is the user ID.</span></span> <span data-ttu-id="57ae7-173">Es ist in Tab SSO, Bot Invoke und Teams Client SDK verfügbar.</span><span class="sxs-lookup"><span data-stu-id="57ae7-173">It is available in Tab SSO, Bot Invoke, and Teams Client SDK.</span></span> <span data-ttu-id="57ae7-174">Es wird empfohlen, eine Teilnehmer-ID vom Tab-SSO abzurufen.</span><span class="sxs-lookup"><span data-stu-id="57ae7-174">It is recommended to get a participant ID from the Tab SSO.</span></span> |
|<span data-ttu-id="57ae7-175">**tenantId**</span><span class="sxs-lookup"><span data-stu-id="57ae7-175">**tenantId**</span></span>| <span data-ttu-id="57ae7-176">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="57ae7-176">String</span></span> | <span data-ttu-id="57ae7-177">Ja</span><span class="sxs-lookup"><span data-stu-id="57ae7-177">Yes</span></span> | <span data-ttu-id="57ae7-178">Die Mandanten-ID ist für die Mandantenbenutzer erforderlich.</span><span class="sxs-lookup"><span data-stu-id="57ae7-178">The tenant ID is required for the tenant users.</span></span> <span data-ttu-id="57ae7-179">Es ist in Tab SSO, Bot Invoke und Teams Client SDK verfügbar.</span><span class="sxs-lookup"><span data-stu-id="57ae7-179">It is available in Tab SSO, Bot Invoke, and Teams Client SDK.</span></span> <span data-ttu-id="57ae7-180">Es wird empfohlen, eine Mandanten-ID aus dem Tab-SSO abzurufen.</span><span class="sxs-lookup"><span data-stu-id="57ae7-180">It is recommended to get a tenant ID from the Tab SSO.</span></span> |

#### <a name="example"></a><span data-ttu-id="57ae7-181">Beispiel</span><span class="sxs-lookup"><span data-stu-id="57ae7-181">Example</span></span>

<span data-ttu-id="57ae7-182">Die `GetParticipant` API enthält die folgenden Beispiele:</span><span class="sxs-lookup"><span data-stu-id="57ae7-182">The `GetParticipant` API includes the following examples:</span></span>

# <a name="c"></a>[<span data-ttu-id="57ae7-183">C#</span><span class="sxs-lookup"><span data-stu-id="57ae7-183">C#</span></span>](#tab/dotnet)

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

# <a name="javascript"></a>[<span data-ttu-id="57ae7-184">JavaScript</span><span class="sxs-lookup"><span data-stu-id="57ae7-184">JavaScript</span></span>](#tab/javascript)

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

# <a name="json"></a>[<span data-ttu-id="57ae7-185">Json</span><span class="sxs-lookup"><span data-stu-id="57ae7-185">JSON</span></span>](#tab/json)

```http
GET /v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}
```

* * *

<span data-ttu-id="57ae7-186">Der JSON-Antworttext für `GetParticipant` die API lautet:</span><span class="sxs-lookup"><span data-stu-id="57ae7-186">The JSON response body for `GetParticipant` API is:</span></span>

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

#### <a name="response-codes"></a><span data-ttu-id="57ae7-187">Antwortcodes</span><span class="sxs-lookup"><span data-stu-id="57ae7-187">Response codes</span></span>

<span data-ttu-id="57ae7-188">Die `GetParticipant` API enthält die folgenden Antwortcodes:</span><span class="sxs-lookup"><span data-stu-id="57ae7-188">The `GetParticipant` API includes the following response codes:</span></span>

|<span data-ttu-id="57ae7-189">Antwortcode</span><span class="sxs-lookup"><span data-stu-id="57ae7-189">Response code</span></span>|<span data-ttu-id="57ae7-190">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="57ae7-190">Description</span></span>|
|---|---|
| <span data-ttu-id="57ae7-191">**403**</span><span class="sxs-lookup"><span data-stu-id="57ae7-191">**403**</span></span> | <span data-ttu-id="57ae7-192">Die App darf keine Teilnehmerinformationen abrufen.</span><span class="sxs-lookup"><span data-stu-id="57ae7-192">The app is not allowed to get participant information.</span></span> <span data-ttu-id="57ae7-193">Dies ist die häufigste Fehlerantwort und wird ausgelöst, wenn die App nicht in der Besprechung installiert ist.</span><span class="sxs-lookup"><span data-stu-id="57ae7-193">This is the most common error response and is triggered if the app is not installed in the meeting.</span></span> <span data-ttu-id="57ae7-194">Wenn die App beispielsweise vom Mandantenadministrator deaktiviert oder während der Migration einer Livewebsite blockiert wird.</span><span class="sxs-lookup"><span data-stu-id="57ae7-194">For example, if the app is disabled by tenant admin or blocked during live site migration.</span></span>|
| <span data-ttu-id="57ae7-195">**200**</span><span class="sxs-lookup"><span data-stu-id="57ae7-195">**200**</span></span> | <span data-ttu-id="57ae7-196">Die Teilnehmerinformationen werden erfolgreich abgerufen.</span><span class="sxs-lookup"><span data-stu-id="57ae7-196">The participant information is successfully retrieved.</span></span>|
| <span data-ttu-id="57ae7-197">**401**</span><span class="sxs-lookup"><span data-stu-id="57ae7-197">**401**</span></span> | <span data-ttu-id="57ae7-198">Die App antwortet mit einem ungültigen Token.</span><span class="sxs-lookup"><span data-stu-id="57ae7-198">The app responds with an invalid token.</span></span>|
| <span data-ttu-id="57ae7-199">**404**</span><span class="sxs-lookup"><span data-stu-id="57ae7-199">**404**</span></span> | <span data-ttu-id="57ae7-200">Die Besprechung ist entweder abgelaufen, oder der Teilnehmer konnte nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="57ae7-200">The meeting has either expired or participant cannot be found.</span></span>|
| <span data-ttu-id="57ae7-201">**500**</span><span class="sxs-lookup"><span data-stu-id="57ae7-201">**500**</span></span> | <span data-ttu-id="57ae7-202">Die Besprechung ist entweder abgelaufen (mehr als 60 Tage), seit die Besprechung endete, oder die Teilnehmer verfügen nicht über Berechtigungen basierend auf ihrer Rolle.</span><span class="sxs-lookup"><span data-stu-id="57ae7-202">The meeting has either expired (more than 60 days) since the meeting ended or the participants do not have permissions based on their role.</span></span>|

### <a name="notificationsignal-api"></a><span data-ttu-id="57ae7-203">NotificationSignal-API</span><span class="sxs-lookup"><span data-stu-id="57ae7-203">NotificationSignal API</span></span>

<span data-ttu-id="57ae7-204">Alle Benutzer in einer Besprechung erhalten die Benachrichtigungen, die über die API gesendet `NotificationSignal` werden.</span><span class="sxs-lookup"><span data-stu-id="57ae7-204">All users in a meeting receive the notifications sent through the `NotificationSignal` API.</span></span>

> [!NOTE]
> * <span data-ttu-id="57ae7-205">Wenn ein Dialogfeld in einer Besprechung aufgerufen wird, wird der Inhalt als Chatnachricht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="57ae7-205">When an in-meeting dialog box is invoked, the content is presented as a chat message.</span></span>
> * <span data-ttu-id="57ae7-206">Derzeit wird das Senden von gezielten Benachrichtigungen nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="57ae7-206">Currently, sending targeted notifications is not supported.</span></span>

<span data-ttu-id="57ae7-207">`NotificationSignal` Mithilfe der API können Sie Besprechungssignale bereitstellen, die mithilfe der vorhandenen Unterhaltungsbenachrichtigungs-API für den Benutzer-Bot-Chat übermittelt werden.</span><span class="sxs-lookup"><span data-stu-id="57ae7-207">`NotificationSignal` API enables you to provide meeting signals that are delivered using the existing conversation notification API for user-bot chat.</span></span> <span data-ttu-id="57ae7-208">Diese API ermöglicht es Ihnen, basierend auf einer Benutzeraktion, die ein Dialogfeld in der Besprechung anzeigt, ein Signal zu senden.</span><span class="sxs-lookup"><span data-stu-id="57ae7-208">This API allows you to signal based on user action that shows an in-meeting dialog box.</span></span> <span data-ttu-id="57ae7-209">Die API enthält Abfrageparameter, Beispiele und Antwortcodes.</span><span class="sxs-lookup"><span data-stu-id="57ae7-209">The API includes query parameter, examples, and response codes.</span></span>

#### <a name="query-parameter"></a><span data-ttu-id="57ae7-210">Abfrageparameter</span><span class="sxs-lookup"><span data-stu-id="57ae7-210">Query parameter</span></span>

<span data-ttu-id="57ae7-211">Die `NotificationSignal` API enthält den folgenden Abfrageparameter:</span><span class="sxs-lookup"><span data-stu-id="57ae7-211">The `NotificationSignal` API includes the following query parameter:</span></span>

|<span data-ttu-id="57ae7-212">Wert</span><span class="sxs-lookup"><span data-stu-id="57ae7-212">Value</span></span>|<span data-ttu-id="57ae7-213">Typ</span><span class="sxs-lookup"><span data-stu-id="57ae7-213">Type</span></span>|<span data-ttu-id="57ae7-214">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="57ae7-214">Required</span></span>|<span data-ttu-id="57ae7-215">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="57ae7-215">Description</span></span>|
|---|---|----|---|
|<span data-ttu-id="57ae7-216">**conversationId**</span><span class="sxs-lookup"><span data-stu-id="57ae7-216">**conversationId**</span></span>| <span data-ttu-id="57ae7-217">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="57ae7-217">String</span></span> | <span data-ttu-id="57ae7-218">Ja</span><span class="sxs-lookup"><span data-stu-id="57ae7-218">Yes</span></span> | <span data-ttu-id="57ae7-219">Der Unterhaltungsbezeichner ist als Teil des Bot-Aufrufs verfügbar.</span><span class="sxs-lookup"><span data-stu-id="57ae7-219">The conversation identifier is available as part of Bot Invoke.</span></span> |

#### <a name="examples"></a><span data-ttu-id="57ae7-220">Beispiele</span><span class="sxs-lookup"><span data-stu-id="57ae7-220">Examples</span></span>

<span data-ttu-id="57ae7-221">Der `Bot ID` wird im Manifest deklariert, und der Bot erhält ein Ergebnisobjekt.</span><span class="sxs-lookup"><span data-stu-id="57ae7-221">The `Bot ID` is declared in the manifest and the bot receives a result object.</span></span>

> [!NOTE]
> * <span data-ttu-id="57ae7-222">Der `completionBotId` Parameter des Parameters ist im `externalResourceUrl` angeforderten Nutzlastbeispiel optional.</span><span class="sxs-lookup"><span data-stu-id="57ae7-222">The `completionBotId` parameter of the `externalResourceUrl` is optional in the requested payload example.</span></span> <span data-ttu-id="57ae7-223">`Bot ID` wird im Manifest deklariert, und der Bot erhält ein Ergebnisobjekt.</span><span class="sxs-lookup"><span data-stu-id="57ae7-223">`Bot ID` is declared in the manifest and the bot receives a result object.</span></span>
> * <span data-ttu-id="57ae7-224">Die `externalResourceUrl` Parameter für Breite und Höhe müssen in Pixeln angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="57ae7-224">The `externalResourceUrl` width and height parameters must be in pixels.</span></span> <span data-ttu-id="57ae7-225">Um sicherzustellen, dass die Abmessungen innerhalb der zulässigen Grenzwerte liegen, lesen Sie die [Entwurfsrichtlinien.](design/designing-apps-in-meetings.md)</span><span class="sxs-lookup"><span data-stu-id="57ae7-225">To ensure the dimensions are within the allowed limits, see [design guidelines](design/designing-apps-in-meetings.md).</span></span>
> * <span data-ttu-id="57ae7-226">Die URL ist die Seite, die als in das Dialogfeld in der Besprechung geladen `<iframe>` wird.</span><span class="sxs-lookup"><span data-stu-id="57ae7-226">The URL is the page loaded as an `<iframe>` in the in-meeting dialog box.</span></span> <span data-ttu-id="57ae7-227">Die Domäne muss sich im Array der App `validDomains` in Ihrem App-Manifest befinden.</span><span class="sxs-lookup"><span data-stu-id="57ae7-227">The domain must be in the app's `validDomains` array in your app manifest.</span></span>

<span data-ttu-id="57ae7-228">Die `NotificationSignal` API enthält die folgenden Beispiele:</span><span class="sxs-lookup"><span data-stu-id="57ae7-228">The `NotificationSignal` API includes the following examples:</span></span>

# <a name="c"></a>[<span data-ttu-id="57ae7-229">C#</span><span class="sxs-lookup"><span data-stu-id="57ae7-229">C#</span></span>](#tab/dotnet)

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

# <a name="javascript"></a>[<span data-ttu-id="57ae7-230">JavaScript</span><span class="sxs-lookup"><span data-stu-id="57ae7-230">JavaScript</span></span>](#tab/javascript)

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

# <a name="json"></a>[<span data-ttu-id="57ae7-231">Json</span><span class="sxs-lookup"><span data-stu-id="57ae7-231">JSON</span></span>](#tab/json)

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

---

#### <a name="response-codes"></a><span data-ttu-id="57ae7-232">Antwortcodes</span><span class="sxs-lookup"><span data-stu-id="57ae7-232">Response codes</span></span>

<span data-ttu-id="57ae7-233">Die `NotificationSignal` API enthält die folgenden Antwortcodes:</span><span class="sxs-lookup"><span data-stu-id="57ae7-233">The `NotificationSignal` API includes the following response codes:</span></span>

|<span data-ttu-id="57ae7-234">Antwortcode</span><span class="sxs-lookup"><span data-stu-id="57ae7-234">Response code</span></span>|<span data-ttu-id="57ae7-235">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="57ae7-235">Description</span></span>|
|---|---|
| <span data-ttu-id="57ae7-236">**201**</span><span class="sxs-lookup"><span data-stu-id="57ae7-236">**201**</span></span> | <span data-ttu-id="57ae7-237">Die Aktivität mit Signal wird erfolgreich gesendet.</span><span class="sxs-lookup"><span data-stu-id="57ae7-237">The activity with signal is successfully sent.</span></span> |
| <span data-ttu-id="57ae7-238">**401**</span><span class="sxs-lookup"><span data-stu-id="57ae7-238">**401**</span></span> | <span data-ttu-id="57ae7-239">Die App antwortet mit einem ungültigen Token.</span><span class="sxs-lookup"><span data-stu-id="57ae7-239">The app responds with an invalid token.</span></span> |
| <span data-ttu-id="57ae7-240">**403**</span><span class="sxs-lookup"><span data-stu-id="57ae7-240">**403**</span></span> | <span data-ttu-id="57ae7-241">Die App kann das Signal nicht senden.</span><span class="sxs-lookup"><span data-stu-id="57ae7-241">The app is unable to send the signal.</span></span> <span data-ttu-id="57ae7-242">Dies kann aus verschiedenen Gründen geschehen, z. B. wenn der Mandantenadministrator die App deaktiviert, die App während der Migration der Livewebsite blockiert wird usw.</span><span class="sxs-lookup"><span data-stu-id="57ae7-242">This can happen due to various reasons such as the tenant admin disables the app, the app is blocked during live site migration, and so on.</span></span> <span data-ttu-id="57ae7-243">In diesem Fall enthält die Nutzlast eine detaillierte Fehlermeldung.</span><span class="sxs-lookup"><span data-stu-id="57ae7-243">In this case, the payload contains a detailed error message.</span></span> |
| <span data-ttu-id="57ae7-244">**404**</span><span class="sxs-lookup"><span data-stu-id="57ae7-244">**404**</span></span> | <span data-ttu-id="57ae7-245">Der Besprechungschat ist nicht vorhanden.</span><span class="sxs-lookup"><span data-stu-id="57ae7-245">The meeting chat does not exist.</span></span> |

## <a name="code-sample"></a><span data-ttu-id="57ae7-246">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="57ae7-246">Code sample</span></span>

|<span data-ttu-id="57ae7-247">Beispielname</span><span class="sxs-lookup"><span data-stu-id="57ae7-247">Sample name</span></span> | <span data-ttu-id="57ae7-248">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="57ae7-248">Description</span></span> | <span data-ttu-id="57ae7-249">.NET</span><span class="sxs-lookup"><span data-stu-id="57ae7-249">.NET</span></span> | <span data-ttu-id="57ae7-250">Node.js</span><span class="sxs-lookup"><span data-stu-id="57ae7-250">Node.js</span></span> |
|----------------|-----------------|--------------|--------------|
| <span data-ttu-id="57ae7-251">Erweiterbarkeit von Besprechungen</span><span class="sxs-lookup"><span data-stu-id="57ae7-251">Meetings extensibility</span></span> | <span data-ttu-id="57ae7-252">Microsoft Teams Beispiel für die Erweiterbarkeit von Besprechungen zum Übergeben von Token.</span><span class="sxs-lookup"><span data-stu-id="57ae7-252">Microsoft Teams meeting extensibility sample for passing tokens.</span></span> | [<span data-ttu-id="57ae7-253">View</span><span class="sxs-lookup"><span data-stu-id="57ae7-253">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/csharp) | [<span data-ttu-id="57ae7-254">View</span><span class="sxs-lookup"><span data-stu-id="57ae7-254">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/nodejs) |
| <span data-ttu-id="57ae7-255">Besprechungsinhalts-Blasen-Bot</span><span class="sxs-lookup"><span data-stu-id="57ae7-255">Meeting content bubble bot</span></span> | <span data-ttu-id="57ae7-256">Microsoft Teams Besprechungserweiterungsbeispiel für die Interaktion mit einem Inhaltsblasen-Bot in einer Besprechung.</span><span class="sxs-lookup"><span data-stu-id="57ae7-256">Microsoft Teams meeting extensibility sample for interacting with content bubble bot in a meeting.</span></span> | [<span data-ttu-id="57ae7-257">View</span><span class="sxs-lookup"><span data-stu-id="57ae7-257">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/csharp) |  [<span data-ttu-id="57ae7-258">View</span><span class="sxs-lookup"><span data-stu-id="57ae7-258">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/nodejs)|
| <span data-ttu-id="57ae7-259">Meeting MeetingSidePanel</span><span class="sxs-lookup"><span data-stu-id="57ae7-259">Meeting meetingSidePanel</span></span> | <span data-ttu-id="57ae7-260">Microsoft Teams Besprechungserweiterungsbeispiel für die Interaktion mit dem Seitenbereich in besprechungsinternen Besprechungen.</span><span class="sxs-lookup"><span data-stu-id="57ae7-260">Microsoft Teams meeting extensibility sample for interacting with the side panel in-meeting.</span></span> | [<span data-ttu-id="57ae7-261">View</span><span class="sxs-lookup"><span data-stu-id="57ae7-261">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-sidepanel/csharp) | [<span data-ttu-id="57ae7-262">View</span><span class="sxs-lookup"><span data-stu-id="57ae7-262">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-sidepanel/nodejs)|

## <a name="see-also"></a><span data-ttu-id="57ae7-263">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="57ae7-263">See also</span></span>

* [<span data-ttu-id="57ae7-264">Entwurfsrichtlinien für Besprechungsdialoge</span><span class="sxs-lookup"><span data-stu-id="57ae7-264">In-meeting dialog design guidelines</span></span>](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)
* [<span data-ttu-id="57ae7-265">Teams Authentifizierungsfluss für Registerkarten</span><span class="sxs-lookup"><span data-stu-id="57ae7-265">Teams authentication flow for tabs</span></span>](../tabs/how-to/authentication/auth-flow-tab.md)
* [<span data-ttu-id="57ae7-266">Apps für Teams Besprechungen</span><span class="sxs-lookup"><span data-stu-id="57ae7-266">Apps for Teams meetings</span></span>](teams-apps-in-meetings.md)

## <a name="next-step"></a><span data-ttu-id="57ae7-267">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="57ae7-267">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="57ae7-268">Aktivieren und Konfigurieren Ihrer Apps für Teams Besprechungen</span><span class="sxs-lookup"><span data-stu-id="57ae7-268">Enable and configure your apps for Teams meetings</span></span>](enable-and-configure-your-app-for-teams-meetings.md)
