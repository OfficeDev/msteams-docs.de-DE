---
title: Voraussetzungen und API-Verweise für Apps in Teams-Besprechungen
author: laujan
description: Arbeiten mit Apps für Teams Besprechungen
ms.topic: conceptual
ms.author: lajanuar
localization_priority: Normal
keywords: Rollen-API für Teams-Apps-Besprechungen für Benutzerteilnehmer
ms.openlocfilehash: aeedd6ff4ee1e075d24020d872b5ebd216be4fb0
ms.sourcegitcommit: 2c8b35899dd845acd66f1f927e40d99523c29a91
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2021
ms.locfileid: "52684642"
---
# <a name="prerequisites-and-api-references-for-apps-in-teams-meetings"></a><span data-ttu-id="521b6-104">Voraussetzungen und API-Verweise für Apps in Teams-Besprechungen</span><span class="sxs-lookup"><span data-stu-id="521b6-104">Prerequisites and API references for apps in Teams meetings</span></span>

<span data-ttu-id="521b6-105">Um die Funktionen Ihrer Apps über den gesamten Besprechungslebenszyklus zu erweitern, Teams Sie mit Apps für Teams arbeiten.</span><span class="sxs-lookup"><span data-stu-id="521b6-105">To expand the capabilities of your apps across the meeting lifecycle, Teams enables you to work with apps for Teams meetings.</span></span> <span data-ttu-id="521b6-106">Sie müssen die Voraussetzungen durchgehen und die Besprechungs-Apps-API-Verweise verwenden, um die Besprechungserfahrung zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="521b6-106">You must  go through the prerequisites and you can use the meeting apps API references to enhance the meeting experience.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="521b6-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="521b6-107">Prerequisites</span></span>

<span data-ttu-id="521b6-108">Bevor Sie mit Apps für Teams arbeiten, müssen Sie folgendes wissen:</span><span class="sxs-lookup"><span data-stu-id="521b6-108">Before you work with apps for Teams meetings, you must have an understanding of the following:</span></span>

* <span data-ttu-id="521b6-109">Sie müssen wissen, wie Sie apps Teams entwickeln.</span><span class="sxs-lookup"><span data-stu-id="521b6-109">You must have knowledge of how to develop Teams apps.</span></span> <span data-ttu-id="521b6-110">Weitere Informationen finden Sie unter [Teams App Development](../overview.md).</span><span class="sxs-lookup"><span data-stu-id="521b6-110">For more information, see [Teams app development](../overview.md).</span></span>

* <span data-ttu-id="521b6-111">Sie müssen das Teams-App-Manifest aktualisieren, um anzugeben, dass die App für Besprechungen verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="521b6-111">You must update the Teams app manifest to indicate that the app is available for meetings.</span></span> <span data-ttu-id="521b6-112">Weitere Informationen finden Sie unter [App-Manifest](enable-and-configure-your-app-for-teams-meetings.md#update-your-app-manifest).</span><span class="sxs-lookup"><span data-stu-id="521b6-112">For more information, see [app manifest](enable-and-configure-your-app-for-teams-meetings.md#update-your-app-manifest).</span></span>

* <span data-ttu-id="521b6-113">Ihre App muss konfigurierbare Registerkarten im Gruppenchatbereich unterstützen, damit Ihre App im Besprechungslebenszyklus als Registerkarte funktioniert. Weitere Informationen finden Sie unter [groupchat scope](../resources/schema/manifest-schema.md#configurabletabs) und [build a group tab](../build-your-first-app/build-channel-tab.md).</span><span class="sxs-lookup"><span data-stu-id="521b6-113">Your app must support configurable tabs in the groupchat scope, for your app to function in the meeting lifecycle as a tab. For more information, see [groupchat scope](../resources/schema/manifest-schema.md#configurabletabs) and [build a group tab](../build-your-first-app/build-channel-tab.md).</span></span>

* <span data-ttu-id="521b6-114">Sie müssen die allgemeinen Richtlinien Teams Registerkartendesigns für Szenarien vor und nach Besprechungen einhalten.</span><span class="sxs-lookup"><span data-stu-id="521b6-114">You must adhere to general Teams tab design guidelines for pre and post-meeting scenarios.</span></span> <span data-ttu-id="521b6-115">Informationen zu Erfahrungen während Besprechungen finden Sie in den Entwurfsrichtlinien für Besprechungsdialogfeldern und Besprechungsdialogfeldern.</span><span class="sxs-lookup"><span data-stu-id="521b6-115">For experiences during meetings, refer to the in-meeting tab and in-meeting dialog design guidelines.</span></span> <span data-ttu-id="521b6-116">Weitere Informationen finden Sie unter [Teams Richtlinien](../tabs/design/tabs.md)für den Registerkartenentwurf, Richtlinien zum Entwerfen von Registerkarten [in](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-tab)Besprechungen und Entwurfsrichtlinien für [Besprechungsdialogdialog.](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)</span><span class="sxs-lookup"><span data-stu-id="521b6-116">For more information, see [Teams tab design guidelines](../tabs/design/tabs.md), [in-meeting tab design guidelines](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-tab), and [in-meeting dialog design guidelines](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-dialog).</span></span>

* <span data-ttu-id="521b6-117">Sie müssen den Bereich `groupchat` unterstützen, um Ihre App in Chats vor und nach besprechungen zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="521b6-117">You must support the `groupchat` scope to enable your app in pre-meeting and post-meeting chats.</span></span> <span data-ttu-id="521b6-118">Mit der App vor der Besprechung können Sie Besprechungs-Apps finden und hinzufügen und Aufgaben vor besprechungen ausführen.</span><span class="sxs-lookup"><span data-stu-id="521b6-118">With the pre-meeting app experience, you can find and add meeting apps and perform pre-meeting tasks.</span></span> <span data-ttu-id="521b6-119">Mit der App nach der Besprechung können Sie die Ergebnisse der Besprechung anzeigen, z. B. Umfrageergebnisse oder Feedback.</span><span class="sxs-lookup"><span data-stu-id="521b6-119">With post-meeting app experience, you can view the results of the meeting, such as poll survey results or feedback.</span></span>

* <span data-ttu-id="521b6-120">Die Parameter für die Besprechungs-API-URL müssen `meetingId` über `userId` , und `tenantId` verfügen.</span><span class="sxs-lookup"><span data-stu-id="521b6-120">Meeting API URL parameters must have `meetingId`, `userId`, and `tenantId`.</span></span> <span data-ttu-id="521b6-121">Diese sind im Rahmen der Teams Client SDK und Bot-Aktivität verfügbar.</span><span class="sxs-lookup"><span data-stu-id="521b6-121">These are available as part of the Teams Client SDK and bot activity.</span></span> <span data-ttu-id="521b6-122">Darüber hinaus können Sie zuverlässige Informationen für Benutzer-ID und Mandanten-ID mithilfe [der Registerkarte SSO-Authentifizierung abrufen.](../tabs/how-to/authentication/auth-aad-sso.md)</span><span class="sxs-lookup"><span data-stu-id="521b6-122">In addition, you can retrieve reliable information for user ID and tenant ID using [tab SSO authentication](../tabs/how-to/authentication/auth-aad-sso.md).</span></span>

* <span data-ttu-id="521b6-123">Die `GetParticipant` API muss über eine Botregistrierung und -ID verfügen, um Authentifizierungstoken zu generieren.</span><span class="sxs-lookup"><span data-stu-id="521b6-123">The `GetParticipant` API must have a bot registration and ID to generate auth tokens.</span></span> <span data-ttu-id="521b6-124">Weitere Informationen finden Sie unter [Botregistrierung und ID](../build-your-first-app/build-bot.md).</span><span class="sxs-lookup"><span data-stu-id="521b6-124">For more information, see [bot registration and ID](../build-your-first-app/build-bot.md).</span></span>

* <span data-ttu-id="521b6-125">Damit Ihre App in Echtzeit aktualisiert werden kann, muss sie basierend auf den Ereignisaktivitäten in der Besprechung auf dem neuesten Stand sein.</span><span class="sxs-lookup"><span data-stu-id="521b6-125">For your app to update in real time, it must be up-to-date based on event activities in the meeting.</span></span> <span data-ttu-id="521b6-126">Diese Ereignisse können sich innerhalb des Dialogfelds in der Besprechung und in anderen Phasen des gesamten Besprechungslebenszyklus finden.</span><span class="sxs-lookup"><span data-stu-id="521b6-126">These events can be within the in-meeting dialog box and other stages across the meeting lifecycle.</span></span> <span data-ttu-id="521b6-127">Das Dialogfeld In-Meeting finden Sie unter Completion `bot Id` parameter in `NotificationSignal` API.</span><span class="sxs-lookup"><span data-stu-id="521b6-127">For the in-meeting dialog box, see completion `bot Id` parameter in `NotificationSignal` API.</span></span>

* <span data-ttu-id="521b6-128">Die Besprechungsdetails-API muss über eine Botregistrierung und bot-ID verfügen.</span><span class="sxs-lookup"><span data-stu-id="521b6-128">Meeting Details API must have a bot registration and bot ID.</span></span> <span data-ttu-id="521b6-129">Es erfordert Bot SDK, um zu `TurnContext` erhalten.</span><span class="sxs-lookup"><span data-stu-id="521b6-129">It requires Bot SDK to get `TurnContext`.</span></span>

* <span data-ttu-id="521b6-130">Bei Besprechungsereignissen in Echtzeit müssen Sie mit dem über das Bot SDK verfügbaren `TurnContext` Objekt vertraut sein.</span><span class="sxs-lookup"><span data-stu-id="521b6-130">For real-time meeting events, you must be familiar with the `TurnContext` object available through the Bot SDK.</span></span> <span data-ttu-id="521b6-131">Das `Activity` Objekt in enthält die Nutzlast mit der `TurnContext` tatsächlichen Start- und Endzeit.</span><span class="sxs-lookup"><span data-stu-id="521b6-131">The `Activity` object in `TurnContext` contains the payload with the actual start and end time.</span></span> <span data-ttu-id="521b6-132">Für Echtzeit-Besprechungsereignisse ist eine registrierte Bot-ID von der Teams erforderlich.</span><span class="sxs-lookup"><span data-stu-id="521b6-132">Real-time meeting events require a registered bot ID from the Teams platform.</span></span>

<span data-ttu-id="521b6-133">Nachdem Sie die Voraussetzungen erfüllt haben, können Sie die API-Verweise auf die Besprechungs-Apps , , und die Besprechungsdetails-API verwenden, mit der Sie mithilfe von Attributen auf Informationen zugreifen und relevante `GetUserContext` `GetParticipant` Inhalte anzeigen `NotificationSignal` können.</span><span class="sxs-lookup"><span data-stu-id="521b6-133">After you have gone through the prerequisites, you can use the meeting apps API references `GetUserContext`, `GetParticipant`, `NotificationSignal`, and Meeting Details API that enable you to access information using attributes and display relevant content.</span></span>

## <a name="meeting-apps-api-references"></a><span data-ttu-id="521b6-134">Apireferenzen für Besprechungs-Apps</span><span class="sxs-lookup"><span data-stu-id="521b6-134">Meeting apps API references</span></span>

<span data-ttu-id="521b6-135">Die neuen Besprechungsergehnmöglichkeiten bieten Ihnen APIs, die die Besprechungserfahrung transformieren.</span><span class="sxs-lookup"><span data-stu-id="521b6-135">The new meeting extensibilities provide you with APIs that transform the meeting experience.</span></span> <span data-ttu-id="521b6-136">Mit dieser neuen Funktion können Sie Apps erstellen oder vorhandene Apps innerhalb des Besprechungslebenszyklus integrieren.</span><span class="sxs-lookup"><span data-stu-id="521b6-136">With this new capability, you can build apps or integrate existing apps within the meeting lifecycle.</span></span> <span data-ttu-id="521b6-137">Sie können die APIs verwenden, um Ihre App auf die Besprechung aufmerksam zu machen.</span><span class="sxs-lookup"><span data-stu-id="521b6-137">You can use the APIs to make your app aware of the meeting.</span></span> <span data-ttu-id="521b6-138">Sie können auswählen, welche APIs Sie verwenden möchten, um die Besprechungserfahrung zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="521b6-138">You can choose which APIs you want to use to enhance the meeting experience.</span></span>

<span data-ttu-id="521b6-139">Die folgende Tabelle enthält eine Liste dieser APIs:</span><span class="sxs-lookup"><span data-stu-id="521b6-139">The following table provides a list of these APIs:</span></span>

|<span data-ttu-id="521b6-140">API</span><span class="sxs-lookup"><span data-stu-id="521b6-140">API</span></span>|<span data-ttu-id="521b6-141">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="521b6-141">Description</span></span>|<span data-ttu-id="521b6-142">Anforderung</span><span class="sxs-lookup"><span data-stu-id="521b6-142">Request</span></span>|<span data-ttu-id="521b6-143">Quelle</span><span class="sxs-lookup"><span data-stu-id="521b6-143">Source</span></span>|
|---|---|----|---|
|<span data-ttu-id="521b6-144">**GetUserContext**</span><span class="sxs-lookup"><span data-stu-id="521b6-144">**GetUserContext**</span></span>| <span data-ttu-id="521b6-145">Mit dieser API können Sie Kontextinformationen abrufen, um relevante Inhalte auf einer Registerkarte Teams anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="521b6-145">This API enables you to get contextual information to display relevant content in a Teams tab.</span></span> |<span data-ttu-id="521b6-146">_**microsoftTeams.getContext( ( ) => { /*...\* / } )*\*_</span><span class="sxs-lookup"><span data-stu-id="521b6-146">_**microsoftTeams.getContext( ( ) => {  /*...*/ } )**_</span></span>|<span data-ttu-id="521b6-147">Microsoft Teams Client SDK</span><span class="sxs-lookup"><span data-stu-id="521b6-147">Microsoft Teams Client SDK</span></span>|
|<span data-ttu-id="521b6-148">**GetParticipant**</span><span class="sxs-lookup"><span data-stu-id="521b6-148">**GetParticipant**</span></span>| <span data-ttu-id="521b6-149">Mit dieser API kann ein Bot Teilnehmerinformationen nach Besprechungs-ID und Teilnehmer-ID abrufen.</span><span class="sxs-lookup"><span data-stu-id="521b6-149">This API allows a bot to fetch participant information by meeting ID and participant ID.</span></span> |<span data-ttu-id="521b6-150">**GET** _**/v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}**_</span><span class="sxs-lookup"><span data-stu-id="521b6-150">**GET** _**/v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}**_</span></span> |<span data-ttu-id="521b6-151">Microsoft Bot Framework SDK</span><span class="sxs-lookup"><span data-stu-id="521b6-151">Microsoft Bot Framework SDK</span></span>|
|<span data-ttu-id="521b6-152">**NotificationSignal**</span><span class="sxs-lookup"><span data-stu-id="521b6-152">**NotificationSignal**</span></span> | <span data-ttu-id="521b6-153">Mit dieser API können Sie Besprechungssignale bereitstellen, die mithilfe der vorhandenen Unterhaltungsbenachrichtigungs-API für den Benutzer-Bot-Chat übermittelt werden.</span><span class="sxs-lookup"><span data-stu-id="521b6-153">This API enables you to provide meeting signals that are delivered using the existing conversation notification API for user-bot chat.</span></span> <span data-ttu-id="521b6-154">Damit können Sie basierend auf der Benutzeraktion, die ein Dialogfeld in der Besprechung zeigt, ein Signal senden.</span><span class="sxs-lookup"><span data-stu-id="521b6-154">It allows you to signal based on user action that shows an in-meeting dialog box.</span></span> |<span data-ttu-id="521b6-155">**POST** _**/v3/conversations/{conversationId}/activities**_</span><span class="sxs-lookup"><span data-stu-id="521b6-155">**POST** _**/v3/conversations/{conversationId}/activities**_</span></span>|<span data-ttu-id="521b6-156">Microsoft Bot Framework SDK</span><span class="sxs-lookup"><span data-stu-id="521b6-156">Microsoft Bot Framework SDK</span></span>|
|<span data-ttu-id="521b6-157">**Besprechungsdetails**</span><span class="sxs-lookup"><span data-stu-id="521b6-157">**Meeting Details**</span></span> | <span data-ttu-id="521b6-158">Mit dieser API können Sie statische Besprechungsmetadaten abrufen.</span><span class="sxs-lookup"><span data-stu-id="521b6-158">This API enables you to get static meeting metadata.</span></span> |<span data-ttu-id="521b6-159">**GET** _**/v1/meetings/{meetingId}**_</span><span class="sxs-lookup"><span data-stu-id="521b6-159">**GET** _**/v1/meetings/{meetingId}**_</span></span>| <span data-ttu-id="521b6-160">Bot SDK</span><span class="sxs-lookup"><span data-stu-id="521b6-160">Bot SDK</span></span> |

### <a name="getusercontext-api"></a><span data-ttu-id="521b6-161">GetUserContext-API</span><span class="sxs-lookup"><span data-stu-id="521b6-161">GetUserContext API</span></span>

<span data-ttu-id="521b6-162">Informationen zum Identifizieren und Abrufen von Kontextinformationen für Ihre Registerkarteninhalte finden Sie unter [Abrufen des Kontexts für Teams Registerkarte](../tabs/how-to/access-teams-context.md#getting-context-by-using-the-microsoft-teams-javascript-library). `meetingId`wird von einer Registerkarte verwendet, wenn sie im Besprechungskontext ausgeführt wird, und wird für die Antwortnutzlast hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="521b6-162">To identify and retrieve contextual information for your tab content, see [get context for your Teams tab](../tabs/how-to/access-teams-context.md#getting-context-by-using-the-microsoft-teams-javascript-library). `meetingId` is used by a tab when running in the meeting context and is added for the response payload.</span></span>

### <a name="getparticipant-api"></a><span data-ttu-id="521b6-163">GetParticipant-API</span><span class="sxs-lookup"><span data-stu-id="521b6-163">GetParticipant API</span></span>

> [!NOTE]
> * <span data-ttu-id="521b6-164">Zwischenspeichern Sie die Teilnehmerrollen nicht, da der Besprechungsorganisator die Rollen jederzeit ändern kann.</span><span class="sxs-lookup"><span data-stu-id="521b6-164">Do not cache participant roles since the meeting organizer can change the roles any time.</span></span>
> * <span data-ttu-id="521b6-165">Teams unterstützt derzeit keine großen Verteilerlisten oder Listengrößen von mehr als 350 Teilnehmern für die `GetParticipant` API.</span><span class="sxs-lookup"><span data-stu-id="521b6-165">Teams does not currently support large distribution lists or roster sizes of more than 350 participants for the `GetParticipant` API.</span></span>

<span data-ttu-id="521b6-166">Die `GetParticipant` API ermöglicht einem Bot das Abrufen von Teilnehmerinformationen nach Besprechungs-ID und Teilnehmer-ID.</span><span class="sxs-lookup"><span data-stu-id="521b6-166">The `GetParticipant` API allows a bot to fetch participant information by meeting ID and participant ID.</span></span> <span data-ttu-id="521b6-167">Die API enthält Abfrageparameter, Beispiele und Antwortcodes.</span><span class="sxs-lookup"><span data-stu-id="521b6-167">The API includes query parameters, examples, and response codes.</span></span>

#### <a name="query-parameters"></a><span data-ttu-id="521b6-168">Abfrageparameter</span><span class="sxs-lookup"><span data-stu-id="521b6-168">Query parameters</span></span>

<span data-ttu-id="521b6-169">Die `GetParticipant` API enthält die folgenden Abfrageparameter:</span><span class="sxs-lookup"><span data-stu-id="521b6-169">The `GetParticipant` API includes the following query parameters:</span></span>

|<span data-ttu-id="521b6-170">Wert</span><span class="sxs-lookup"><span data-stu-id="521b6-170">Value</span></span>|<span data-ttu-id="521b6-171">Typ</span><span class="sxs-lookup"><span data-stu-id="521b6-171">Type</span></span>|<span data-ttu-id="521b6-172">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="521b6-172">Required</span></span>|<span data-ttu-id="521b6-173">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="521b6-173">Description</span></span>|
|---|---|----|---|
|<span data-ttu-id="521b6-174">**meetingId**</span><span class="sxs-lookup"><span data-stu-id="521b6-174">**meetingId**</span></span>| <span data-ttu-id="521b6-175">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="521b6-175">String</span></span> | <span data-ttu-id="521b6-176">Ja</span><span class="sxs-lookup"><span data-stu-id="521b6-176">Yes</span></span> | <span data-ttu-id="521b6-177">Der Besprechungsbezeichner ist über Bot Invoke und Teams Client SDK verfügbar.</span><span class="sxs-lookup"><span data-stu-id="521b6-177">The meeting identifier is available through Bot Invoke and Teams Client SDK.</span></span>|
|<span data-ttu-id="521b6-178">**participantId**</span><span class="sxs-lookup"><span data-stu-id="521b6-178">**participantId**</span></span>| <span data-ttu-id="521b6-179">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="521b6-179">String</span></span> | <span data-ttu-id="521b6-180">Ja</span><span class="sxs-lookup"><span data-stu-id="521b6-180">Yes</span></span> | <span data-ttu-id="521b6-181">Die Teilnehmer-ID ist die Benutzer-ID.</span><span class="sxs-lookup"><span data-stu-id="521b6-181">The participant ID is the user ID.</span></span> <span data-ttu-id="521b6-182">Sie ist in Tab SSO, Bot Invoke und Teams Client SDK verfügbar.</span><span class="sxs-lookup"><span data-stu-id="521b6-182">It is available in Tab SSO, Bot Invoke, and Teams Client SDK.</span></span> <span data-ttu-id="521b6-183">Es wird empfohlen, eine Teilnehmer-ID aus dem Tab-SSO zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="521b6-183">It is recommended to get a participant ID from the Tab SSO.</span></span> |
|<span data-ttu-id="521b6-184">**tenantId**</span><span class="sxs-lookup"><span data-stu-id="521b6-184">**tenantId**</span></span>| <span data-ttu-id="521b6-185">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="521b6-185">String</span></span> | <span data-ttu-id="521b6-186">Ja</span><span class="sxs-lookup"><span data-stu-id="521b6-186">Yes</span></span> | <span data-ttu-id="521b6-187">Die Mandanten-ID ist für die Mandantenbenutzer erforderlich.</span><span class="sxs-lookup"><span data-stu-id="521b6-187">The tenant ID is required for the tenant users.</span></span> <span data-ttu-id="521b6-188">Sie ist in Tab SSO, Bot Invoke und Teams Client SDK verfügbar.</span><span class="sxs-lookup"><span data-stu-id="521b6-188">It is available in Tab SSO, Bot Invoke, and Teams Client SDK.</span></span> <span data-ttu-id="521b6-189">Es wird empfohlen, eine Mandanten-ID aus dem Tab-SSO zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="521b6-189">It is recommended to get a tenant ID from the Tab SSO.</span></span> |

#### <a name="example"></a><span data-ttu-id="521b6-190">Beispiel</span><span class="sxs-lookup"><span data-stu-id="521b6-190">Example</span></span>

<span data-ttu-id="521b6-191">Die `GetParticipant` API enthält die folgenden Beispiele:</span><span class="sxs-lookup"><span data-stu-id="521b6-191">The `GetParticipant` API includes the following examples:</span></span>

# <a name="c"></a>[<span data-ttu-id="521b6-192">C#</span><span class="sxs-lookup"><span data-stu-id="521b6-192">C#</span></span>](#tab/dotnet)

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

# <a name="javascript"></a>[<span data-ttu-id="521b6-193">JavaScript</span><span class="sxs-lookup"><span data-stu-id="521b6-193">JavaScript</span></span>](#tab/javascript)

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

# <a name="json"></a>[<span data-ttu-id="521b6-194">Json</span><span class="sxs-lookup"><span data-stu-id="521b6-194">JSON</span></span>](#tab/json)

```http
GET /v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}
```

* * *

<span data-ttu-id="521b6-195">Der JSON-Antworttext für `GetParticipant` API ist:</span><span class="sxs-lookup"><span data-stu-id="521b6-195">The JSON response body for `GetParticipant` API is:</span></span>

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

#### <a name="response-codes"></a><span data-ttu-id="521b6-196">Antwortcodes</span><span class="sxs-lookup"><span data-stu-id="521b6-196">Response codes</span></span>

<span data-ttu-id="521b6-197">Die `GetParticipant` API enthält die folgenden Antwortcodes:</span><span class="sxs-lookup"><span data-stu-id="521b6-197">The `GetParticipant` API includes the following response codes:</span></span>

|<span data-ttu-id="521b6-198">Antwortcode</span><span class="sxs-lookup"><span data-stu-id="521b6-198">Response code</span></span>|<span data-ttu-id="521b6-199">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="521b6-199">Description</span></span>|
|---|---|
| <span data-ttu-id="521b6-200">**403**</span><span class="sxs-lookup"><span data-stu-id="521b6-200">**403**</span></span> | <span data-ttu-id="521b6-201">Die App darf keine Teilnehmerinformationen erhalten.</span><span class="sxs-lookup"><span data-stu-id="521b6-201">The app is not allowed to get participant information.</span></span> <span data-ttu-id="521b6-202">Dies ist die häufigste Fehlerantwort und wird ausgelöst, wenn die App nicht in der Besprechung installiert ist.</span><span class="sxs-lookup"><span data-stu-id="521b6-202">This is the most common error response and is triggered if the app is not installed in the meeting.</span></span> <span data-ttu-id="521b6-203">Beispiel: Wenn die App vom Mandantenadministrator deaktiviert oder während der Livewebsitemigration blockiert wird.</span><span class="sxs-lookup"><span data-stu-id="521b6-203">For example, if the app is disabled by tenant admin or blocked during live site migration.</span></span>|
| <span data-ttu-id="521b6-204">**200**</span><span class="sxs-lookup"><span data-stu-id="521b6-204">**200**</span></span> | <span data-ttu-id="521b6-205">Die Teilnehmerinformationen werden erfolgreich abgerufen.</span><span class="sxs-lookup"><span data-stu-id="521b6-205">The participant information is successfully retrieved.</span></span>|
| <span data-ttu-id="521b6-206">**401**</span><span class="sxs-lookup"><span data-stu-id="521b6-206">**401**</span></span> | <span data-ttu-id="521b6-207">Die App antwortet mit einem ungültigen Token.</span><span class="sxs-lookup"><span data-stu-id="521b6-207">The app responds with an invalid token.</span></span>|
| <span data-ttu-id="521b6-208">**404**</span><span class="sxs-lookup"><span data-stu-id="521b6-208">**404**</span></span> | <span data-ttu-id="521b6-209">Die Besprechung ist entweder abgelaufen, oder der Teilnehmer wurde nicht gefunden.</span><span class="sxs-lookup"><span data-stu-id="521b6-209">The meeting has either expired or participant cannot be found.</span></span>|
| <span data-ttu-id="521b6-210">**500**</span><span class="sxs-lookup"><span data-stu-id="521b6-210">**500**</span></span> | <span data-ttu-id="521b6-211">Die Besprechung ist entweder (mehr als 60 Tage) seit dem Ende der Besprechung abgelaufen, oder die Teilnehmer verfügen nicht über Berechtigungen basierend auf ihrer Rolle.</span><span class="sxs-lookup"><span data-stu-id="521b6-211">The meeting has either expired (more than 60 days) since the meeting ended or the participants do not have permissions based on their role.</span></span>|

### <a name="notificationsignal-api"></a><span data-ttu-id="521b6-212">NotificationSignal-API</span><span class="sxs-lookup"><span data-stu-id="521b6-212">NotificationSignal API</span></span>

<span data-ttu-id="521b6-213">Alle Benutzer in einer Besprechung erhalten die über die API gesendeten `NotificationSignal` Benachrichtigungen.</span><span class="sxs-lookup"><span data-stu-id="521b6-213">All users in a meeting receive the notifications sent through the `NotificationSignal` API.</span></span>

> [!NOTE]
> * <span data-ttu-id="521b6-214">Wenn ein Dialogfeld in der Besprechung aufgerufen wird, wird der Inhalt als Chatnachricht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="521b6-214">When an in-meeting dialog box is invoked, the content is presented as a chat message.</span></span>
> * <span data-ttu-id="521b6-215">Derzeit wird das Senden gezielter Benachrichtigungen nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="521b6-215">Currently, sending targeted notifications is not supported.</span></span>

<span data-ttu-id="521b6-216">`NotificationSignal` Mit der API können Sie Besprechungssignale bereitstellen, die mithilfe der vorhandenen Unterhaltungsbenachrichtigungs-API für den Benutzer-Bot-Chat übermittelt werden.</span><span class="sxs-lookup"><span data-stu-id="521b6-216">`NotificationSignal` API enables you to provide meeting signals that are delivered using the existing conversation notification API for user-bot chat.</span></span> <span data-ttu-id="521b6-217">Mit dieser API können Sie basierend auf der Benutzeraktion, die ein Dialogfeld in der Besprechung zeigt, ein Signal senden.</span><span class="sxs-lookup"><span data-stu-id="521b6-217">This API allows you to signal based on user action that shows an in-meeting dialog box.</span></span> <span data-ttu-id="521b6-218">Die API enthält Abfrageparameter, Beispiele und Antwortcodes.</span><span class="sxs-lookup"><span data-stu-id="521b6-218">The API includes query parameter, examples, and response codes.</span></span>

#### <a name="query-parameter"></a><span data-ttu-id="521b6-219">Abfrageparameter</span><span class="sxs-lookup"><span data-stu-id="521b6-219">Query parameter</span></span>

<span data-ttu-id="521b6-220">Die `NotificationSignal` API enthält den folgenden Abfrageparameter:</span><span class="sxs-lookup"><span data-stu-id="521b6-220">The `NotificationSignal` API includes the following query parameter:</span></span>

|<span data-ttu-id="521b6-221">Wert</span><span class="sxs-lookup"><span data-stu-id="521b6-221">Value</span></span>|<span data-ttu-id="521b6-222">Typ</span><span class="sxs-lookup"><span data-stu-id="521b6-222">Type</span></span>|<span data-ttu-id="521b6-223">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="521b6-223">Required</span></span>|<span data-ttu-id="521b6-224">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="521b6-224">Description</span></span>|
|---|---|----|---|
|<span data-ttu-id="521b6-225">**conversationId**</span><span class="sxs-lookup"><span data-stu-id="521b6-225">**conversationId**</span></span>| <span data-ttu-id="521b6-226">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="521b6-226">String</span></span> | <span data-ttu-id="521b6-227">Ja</span><span class="sxs-lookup"><span data-stu-id="521b6-227">Yes</span></span> | <span data-ttu-id="521b6-228">Der Unterhaltungsbezeichner ist als Teil von Bot Invoke verfügbar.</span><span class="sxs-lookup"><span data-stu-id="521b6-228">The conversation identifier is available as part of Bot Invoke.</span></span> |

#### <a name="examples"></a><span data-ttu-id="521b6-229">Beispiele</span><span class="sxs-lookup"><span data-stu-id="521b6-229">Examples</span></span>

<span data-ttu-id="521b6-230">Der `Bot ID` wird im Manifest deklariert, und der Bot empfängt ein Ergebnisobjekt.</span><span class="sxs-lookup"><span data-stu-id="521b6-230">The `Bot ID` is declared in the manifest and the bot receives a result object.</span></span>

> [!NOTE]
> * <span data-ttu-id="521b6-231">Der `completionBotId` Parameter von ist im `externalResourceUrl` angeforderten Nutzlastbeispiel optional.</span><span class="sxs-lookup"><span data-stu-id="521b6-231">The `completionBotId` parameter of the `externalResourceUrl` is optional in the requested payload example.</span></span> <span data-ttu-id="521b6-232">`Bot ID` wird im Manifest deklariert, und der Bot empfängt ein Ergebnisobjekt.</span><span class="sxs-lookup"><span data-stu-id="521b6-232">`Bot ID` is declared in the manifest and the bot receives a result object.</span></span>
> * <span data-ttu-id="521b6-233">Die `externalResourceUrl` Parameter für Breite und Höhe müssen in Pixel angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="521b6-233">The `externalResourceUrl` width and height parameters must be in pixels.</span></span> <span data-ttu-id="521b6-234">Um sicherzustellen, dass die Abmessungen innerhalb der zulässigen Grenzwerte liegen, finden Sie unter [Entwurfsrichtlinien](design/designing-apps-in-meetings.md).</span><span class="sxs-lookup"><span data-stu-id="521b6-234">To ensure the dimensions are within the allowed limits, see [design guidelines](design/designing-apps-in-meetings.md).</span></span>
> * <span data-ttu-id="521b6-235">Die URL ist die Im Besprechungsdialogfeld `<iframe>` geladene Seite.</span><span class="sxs-lookup"><span data-stu-id="521b6-235">The URL is the page loaded as an `<iframe>` in the in-meeting dialog box.</span></span> <span data-ttu-id="521b6-236">Die Domäne muss sich im Array der App `validDomains` im App-Manifest befinden.</span><span class="sxs-lookup"><span data-stu-id="521b6-236">The domain must be in the app's `validDomains` array in your app manifest.</span></span>

<span data-ttu-id="521b6-237">Die `NotificationSignal` API enthält die folgenden Beispiele:</span><span class="sxs-lookup"><span data-stu-id="521b6-237">The `NotificationSignal` API includes the following examples:</span></span>

# <a name="c"></a>[<span data-ttu-id="521b6-238">C#</span><span class="sxs-lookup"><span data-stu-id="521b6-238">C#</span></span>](#tab/dotnet)

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

# <a name="javascript"></a>[<span data-ttu-id="521b6-239">JavaScript</span><span class="sxs-lookup"><span data-stu-id="521b6-239">JavaScript</span></span>](#tab/javascript)

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

# <a name="json"></a>[<span data-ttu-id="521b6-240">Json</span><span class="sxs-lookup"><span data-stu-id="521b6-240">JSON</span></span>](#tab/json)

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

#### <a name="response-codes"></a><span data-ttu-id="521b6-241">Antwortcodes</span><span class="sxs-lookup"><span data-stu-id="521b6-241">Response codes</span></span>

<span data-ttu-id="521b6-242">Die `NotificationSignal` API enthält die folgenden Antwortcodes:</span><span class="sxs-lookup"><span data-stu-id="521b6-242">The `NotificationSignal` API includes the following response codes:</span></span>

|<span data-ttu-id="521b6-243">Antwortcode</span><span class="sxs-lookup"><span data-stu-id="521b6-243">Response code</span></span>|<span data-ttu-id="521b6-244">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="521b6-244">Description</span></span>|
|---|---|
| <span data-ttu-id="521b6-245">**201**</span><span class="sxs-lookup"><span data-stu-id="521b6-245">**201**</span></span> | <span data-ttu-id="521b6-246">Die Aktivität mit Signal wird erfolgreich gesendet.</span><span class="sxs-lookup"><span data-stu-id="521b6-246">The activity with signal is successfully sent.</span></span> |
| <span data-ttu-id="521b6-247">**401**</span><span class="sxs-lookup"><span data-stu-id="521b6-247">**401**</span></span> | <span data-ttu-id="521b6-248">Die App antwortet mit einem ungültigen Token.</span><span class="sxs-lookup"><span data-stu-id="521b6-248">The app responds with an invalid token.</span></span> |
| <span data-ttu-id="521b6-249">**403**</span><span class="sxs-lookup"><span data-stu-id="521b6-249">**403**</span></span> | <span data-ttu-id="521b6-250">Die App kann das Signal nicht senden.</span><span class="sxs-lookup"><span data-stu-id="521b6-250">The app is unable to send the signal.</span></span> <span data-ttu-id="521b6-251">Dies kann aus verschiedenen Gründen geschehen, z. B. wenn der Mandantenadministrator die App deaktiviert, die App während der Livewebsitemigration blockiert wird und so weiter.</span><span class="sxs-lookup"><span data-stu-id="521b6-251">This can happen due to various reasons such as the tenant admin disables the app, the app is blocked during live site migration, and so on.</span></span> <span data-ttu-id="521b6-252">In diesem Fall enthält die Nutzlast eine detaillierte Fehlermeldung.</span><span class="sxs-lookup"><span data-stu-id="521b6-252">In this case, the payload contains a detailed error message.</span></span> |
| <span data-ttu-id="521b6-253">**404**</span><span class="sxs-lookup"><span data-stu-id="521b6-253">**404**</span></span> | <span data-ttu-id="521b6-254">Der Besprechungschat ist nicht vorhanden.</span><span class="sxs-lookup"><span data-stu-id="521b6-254">The meeting chat does not exist.</span></span> |

### <a name="meeting-details-api"></a><span data-ttu-id="521b6-255">Api für Besprechungsdetails</span><span class="sxs-lookup"><span data-stu-id="521b6-255">Meeting Details API</span></span>

> [!NOTE]
> <span data-ttu-id="521b6-256">Dieses Feature ist derzeit nur in der [öffentlichen Entwicklervorschau](../resources/dev-preview/developer-preview-intro.md) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="521b6-256">This feature is currently available in [public developer preview](../resources/dev-preview/developer-preview-intro.md) only.</span></span>

<span data-ttu-id="521b6-257">Mit der Besprechungsdetails-API kann Ihre App statische Besprechungsmetadaten abrufen.</span><span class="sxs-lookup"><span data-stu-id="521b6-257">The Meeting Details API enables your app to get static meeting metadata.</span></span> <span data-ttu-id="521b6-258">Dies sind Datenpunkte, die sich nicht dynamisch ändern.</span><span class="sxs-lookup"><span data-stu-id="521b6-258">These are data points that do not change dynamically.</span></span>
<span data-ttu-id="521b6-259">Die API ist über Bot Services verfügbar.</span><span class="sxs-lookup"><span data-stu-id="521b6-259">The API is available through Bot Services.</span></span>

#### <a name="query-parameter"></a><span data-ttu-id="521b6-260">Abfrageparameter</span><span class="sxs-lookup"><span data-stu-id="521b6-260">Query parameter</span></span>

<span data-ttu-id="521b6-261">Die Besprechungsdetails-API enthält den folgenden Abfrageparameter:</span><span class="sxs-lookup"><span data-stu-id="521b6-261">The Meeting Details API includes the following query parameter:</span></span>

|<span data-ttu-id="521b6-262">Wert</span><span class="sxs-lookup"><span data-stu-id="521b6-262">Value</span></span>|<span data-ttu-id="521b6-263">Typ</span><span class="sxs-lookup"><span data-stu-id="521b6-263">Type</span></span>|<span data-ttu-id="521b6-264">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="521b6-264">Required</span></span>|<span data-ttu-id="521b6-265">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="521b6-265">Description</span></span>|
|---|---|----|---|
|<span data-ttu-id="521b6-266">**meetingId**</span><span class="sxs-lookup"><span data-stu-id="521b6-266">**meetingId**</span></span>| <span data-ttu-id="521b6-267">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="521b6-267">String</span></span> | <span data-ttu-id="521b6-268">Ja</span><span class="sxs-lookup"><span data-stu-id="521b6-268">Yes</span></span> | <span data-ttu-id="521b6-269">Der Besprechungsbezeichner ist über Bot Invoke und Teams Client SDK verfügbar.</span><span class="sxs-lookup"><span data-stu-id="521b6-269">The meeting identifier is available through Bot Invoke and Teams Client SDK.</span></span> |

#### <a name="example"></a><span data-ttu-id="521b6-270">Beispiel</span><span class="sxs-lookup"><span data-stu-id="521b6-270">Example</span></span>

<span data-ttu-id="521b6-271">Die Besprechungsdetails-API enthält die folgenden Beispiele:</span><span class="sxs-lookup"><span data-stu-id="521b6-271">The Meeting Details API includes the following examples:</span></span>

# <a name="c"></a>[<span data-ttu-id="521b6-272">C#</span><span class="sxs-lookup"><span data-stu-id="521b6-272">C#</span></span>](#tab/dotnet)

```csharp
var connectorClient = parameters.TurnContext.TurnState.Get<IConnectorClient>();
var creds = connectorClient.Credentials as AppCredentials;
var bearerToken = await creds.GetTokenAsync().ConfigureAwait(false);
var request = new HttpRequestMessage(HttpMethod.Get, new Uri(new Uri(connectorClient.BaseUri.OriginalString), $"v1/meetings/{meetingId}"));
request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", bearerToken);
HttpResponseMessage response = await (connectorClient as ServiceClient<ConnectorClient>).HttpClient.SendAsync(request, CancellationToken.None).ConfigureAwait(false);
string content;
if (response.Content != null)
{
    content = await response.Content.ReadAsStringAsync().ConfigureAwait(false);
}
```

# <a name="javascript"></a>[<span data-ttu-id="521b6-273">JavaScript</span><span class="sxs-lookup"><span data-stu-id="521b6-273">JavaScript</span></span>](#tab/javascript)

<span data-ttu-id="521b6-274">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="521b6-274">Not available</span></span>

# <a name="json"></a>[<span data-ttu-id="521b6-275">Json</span><span class="sxs-lookup"><span data-stu-id="521b6-275">JSON</span></span>](#tab/json)

```http
GET /v1/meetings/{meetingId}
```

---

<span data-ttu-id="521b6-276">Der JSON-Antworttext für die Besprechungsdetails-API lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="521b6-276">The JSON response body for Meeting Details API is as follows:</span></span>

```json
{ 
   "details": { 
        "id": "meeting ID", 
        "msGraphResourceId": "", 
        "scheduledStartTime": "2020-08-21T02:30:00+00:00", 
        "scheduledEndTime": "2020-08-21T03:00:00+00:00", 
        "joinUrl": "https://teams.microsoft.com/l/xx", 
        "title": "All Hands", 
        "type": "Scheduled" 
    }, 
    "conversation": { 
            "isGroup": true, 
            “conversationType”: “groupchat”, 
            "id": "meeting chat ID" 
    }, 
    "organizer": { 
        "id": "<organizer user ID>", 
        "aadObjectId": "<AAD ID>", 
        "tenantId": "<Tenant ID>" 
    }
} 
```

## <a name="real-time-teams-meeting-events"></a><span data-ttu-id="521b6-277">Echtzeit-Teams Besprechungsereignisse</span><span class="sxs-lookup"><span data-stu-id="521b6-277">Real-time Teams meeting events</span></span>

> [!NOTE]
> <span data-ttu-id="521b6-278">Dieses Feature ist derzeit nur in der [öffentlichen Entwicklervorschau](../resources/dev-preview/developer-preview-intro.md) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="521b6-278">This feature is currently available in [public developer preview](../resources/dev-preview/developer-preview-intro.md) only.</span></span>

<span data-ttu-id="521b6-279">Der Benutzer kann Besprechungsereignisse in Echtzeit empfangen.</span><span class="sxs-lookup"><span data-stu-id="521b6-279">The user can receive real-time meeting events.</span></span> <span data-ttu-id="521b6-280">Sobald eine App einer Besprechung zugeordnet ist, werden der tatsächliche Beginn und die Endzeit der Besprechung für den Bot freigegeben.</span><span class="sxs-lookup"><span data-stu-id="521b6-280">As soon as any app is associated with a meeting, the actual meeting start and meeting end time are shared with the bot.</span></span>

<span data-ttu-id="521b6-281">Die tatsächliche Start- und Endzeit einer Besprechung unterscheiden sich von der geplanten Start- und Endzeit.</span><span class="sxs-lookup"><span data-stu-id="521b6-281">Actual start and end time of a meeting are different from the scheduled start and end time.</span></span> <span data-ttu-id="521b6-282">Die Besprechungsdetails-API stellt die geplante Start- und Endzeit bereit, während das Ereignis die tatsächliche Start- und Endzeit liefert.</span><span class="sxs-lookup"><span data-stu-id="521b6-282">The meeting details API provides the scheduled start and end time while the event provides the actual start and end time.</span></span>

### <a name="example-of-meeting-start-event-payload"></a><span data-ttu-id="521b6-283">Beispiel für die Nutzlast des Besprechungsstartereigniss</span><span class="sxs-lookup"><span data-stu-id="521b6-283">Example of meeting start event payload</span></span>

<span data-ttu-id="521b6-284">Der folgende Code enthält ein Beispiel für die Nutzlast des Besprechungsstartereigniss:</span><span class="sxs-lookup"><span data-stu-id="521b6-284">The following code provides an example of meeting start event payload:</span></span>

```json
{ 
    "name": "Microsoft/MeetingStart", 
    "type": "event", 
    "timestamp": "2021-04-29T16:10:41.1252256Z", 
    "id": "123", 
    "channelId": "msteams", 
    "serviceUrl": "https://microsoft.com", 
    "from": { 
        "id": "userID", 
        "name": "", 
        "aadObjectId": "aadOnjectId" 
    }, 
    "conversation": { 
        "isGroup": true, 
        "tenantId": "tenantId", 
        "id": "thread id" 
    }, 
    "recipient": { 
        "id": "user Id", 
        "name": "user name" 
    }, 
    "entities": [ 
        { 
            "locale": "en-US", 
            "country": "US", 
            "type": "clientInfo" 
        } 
    ], 
    "channelData": { 
        "tenant": { 
            "id": "channel id" 
        }, 
        "source": null, 
        "meeting": { 
            "id": "meeting id" 
        } 
    }, 
    "value": { 
        "MeetingType": "Scheduled", 
        "Title": "Meeting Start/End Event", 
        "Id":"meeting id", 
        "JoinUrl": "url" 
        "StartTime": "2021-04-29T16:17:17.4388966Z" 
    }, 
    "locale": "en-US" 
}
```

### <a name="example-of-meeting-end-event-payload"></a><span data-ttu-id="521b6-285">Beispiel für die Nutzlast des Besprechungsendereigniss</span><span class="sxs-lookup"><span data-stu-id="521b6-285">Example of meeting end event payload</span></span>

<span data-ttu-id="521b6-286">Der folgende Code enthält ein Beispiel für die Nutzlast des Besprechungsendereigniss:</span><span class="sxs-lookup"><span data-stu-id="521b6-286">The following code provides an example of meeting end event payload:</span></span>

```json
{ 
    "name": "Microsoft/MeetingEnd", 
    "type": "event", 
    "timestamp": "2021-04-29T16:17:17.4388966Z", 
    "id": "123", 
    "channelId": "msteams", 
    "serviceUrl": "https://microsoft.com", 
    "from": { 
        "id": "user id", 
        "name": "", 
        "aadObjectId": "aadObjectId" 
    }, 
    "conversation": { 
        "isGroup": true, 
        "tenantId": "tenantId", 
        "id": "thread id" 
    }, 
    "recipient": { 
        "id": "user id", 
        "name": "user name" 
    }, 
    "entities": [ 
        { 
            "locale": "en-US", 
            "country": "US", 
            "type": "clientInfo" 
        } 
    ], 
    "channelData": { 
        "tenant": { 
            "id": "channel id" 
        }, 
        "source": null, 
        "meeting": { 
            "id": "meeting Id" 
        } 
    }, 
    "value": { 
        "MeetingType": "Scheduled", 
        "Title": "Meeting Start/End Event in Canary", 
        "Id": "19:meeting_NTM3ZDJjOTUtZGRhOS00MzYxLTk5NDAtMzY4M2IzZWFjZGE1@thread.v2", 
        "JoinUrl": "url", 
        "EndTime": "2021-04-29T16:17:17.4388966Z" 
    }, 
    "locale": "en-US" 
}
```

### <a name="example-of-getting-metadata-of-a-meeting"></a><span data-ttu-id="521b6-287">Beispiel für das Abrufen von Metadaten einer Besprechung</span><span class="sxs-lookup"><span data-stu-id="521b6-287">Example of getting metadata of a meeting</span></span>

<span data-ttu-id="521b6-288">Ihr Bot empfängt das Ereignis über den `OnEventActivityAsync` Handler.</span><span class="sxs-lookup"><span data-stu-id="521b6-288">Your bot receives the event through the `OnEventActivityAsync` handler.</span></span>

<span data-ttu-id="521b6-289">Zum Deserialisieren der json-Nutzlast wird ein Modellobjekt eingeführt, um die Metadaten einer Besprechung zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="521b6-289">To deserialize the json payload, a model object is introduced to get the metadata of a meeting.</span></span> <span data-ttu-id="521b6-290">Die Metadaten einer Besprechung befinden sich in der `value` Eigenschaft in der Ereignisnutzlast.</span><span class="sxs-lookup"><span data-stu-id="521b6-290">The metadata of a meeting resides in the `value` property in the event payload.</span></span> <span data-ttu-id="521b6-291">Das `MeetingStartEndEventvalue` Modellobjekt wird erstellt, dessen Membervariablen den Schlüsseln unter der `value` Eigenschaft in der Ereignisnutzlast entsprechen.</span><span class="sxs-lookup"><span data-stu-id="521b6-291">The `MeetingStartEndEventvalue` model object is created, whose member variables correspond to the keys under the `value` property in the event payload.</span></span>

<span data-ttu-id="521b6-292">Der folgende Code zeigt, wie Sie die Metadaten einer Besprechung erfassen, die , , , ist, und von einem `MeetingType` `Title` `Id` Besprechungsanfangs- und `JoinUrl` `StartTime` `EndTime` -endereignis:</span><span class="sxs-lookup"><span data-stu-id="521b6-292">The following code shows how to capture the metadata of a meeting that is `MeetingType`, `Title`, `Id`, `JoinUrl`, `StartTime`, and `EndTime` from a meeting start and end event:</span></span>

```csharp
protected override async Task OnEventActivityAsync(
ITurnContext<IEventActivity> turnContext, CancellationToken cancellationToken)
{
    // Event Name is either `Microsoft/MeetingStart` or `Microsoft/MeetingEnd`
    var meetingEventName = turnContext.Activity.Name;
    // Value contains meeting information (ex: meeting type, start time, etc).
    var meetingEventInfo = turnContext.Activity.Value as JObject; 
    var meetingEventInfoObject =
meetingEventInfo.ToObject<MeetingStartEndEventValue>();
    // Create a very simple adaptive card with meeting information
var attachmentCard = createMeetingStartOrEndEventAttachment(meetingEventName,
meetingEventInfoObject);
    await turnContext.SendActivityAsync(MessageFactory.Attachment(attachmentCard));
}
```

<span data-ttu-id="521b6-293">MeetingStartEndEventvalue.cs enthält den folgenden Code:</span><span class="sxs-lookup"><span data-stu-id="521b6-293">The MeetingStartEndEventvalue.cs includes the following code:</span></span>

```csharp
public class MeetingStartEndEventValue
{
    public string Id { get; set; }
    public string Title { get; set; }
    public string MeetingType { get; set; }
    public string JoinUrl { get; set; }
    public string StartTime { get; set; }
    public string EndTime { get; set; }
}
```

## <a name="code-sample"></a><span data-ttu-id="521b6-294">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="521b6-294">Code sample</span></span>

|<span data-ttu-id="521b6-295">Beispielname</span><span class="sxs-lookup"><span data-stu-id="521b6-295">Sample name</span></span> | <span data-ttu-id="521b6-296">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="521b6-296">Description</span></span> | <span data-ttu-id="521b6-297">.NET</span><span class="sxs-lookup"><span data-stu-id="521b6-297">.NET</span></span> | <span data-ttu-id="521b6-298">Node.js</span><span class="sxs-lookup"><span data-stu-id="521b6-298">Node.js</span></span> |
|----------------|-----------------|--------------|--------------|
| <span data-ttu-id="521b6-299">Erweiterbarkeit von Besprechungen</span><span class="sxs-lookup"><span data-stu-id="521b6-299">Meetings extensibility</span></span> | <span data-ttu-id="521b6-300">Microsoft Teams Beispiel für die Besprechungsergehnbarkeit zum Übergeben von Token.</span><span class="sxs-lookup"><span data-stu-id="521b6-300">Microsoft Teams meeting extensibility sample for passing tokens.</span></span> | [<span data-ttu-id="521b6-301">View</span><span class="sxs-lookup"><span data-stu-id="521b6-301">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/csharp) | [<span data-ttu-id="521b6-302">View</span><span class="sxs-lookup"><span data-stu-id="521b6-302">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/nodejs) |
| <span data-ttu-id="521b6-303">Besprechungsinhaltsblasen-Bot</span><span class="sxs-lookup"><span data-stu-id="521b6-303">Meeting content bubble bot</span></span> | <span data-ttu-id="521b6-304">Microsoft Teams beispiel für die Besprechungsergehnbarkeit für die Interaktion mit dem Inhaltsblasenbot in einer Besprechung.</span><span class="sxs-lookup"><span data-stu-id="521b6-304">Microsoft Teams meeting extensibility sample for interacting with content bubble bot in a meeting.</span></span> | [<span data-ttu-id="521b6-305">View</span><span class="sxs-lookup"><span data-stu-id="521b6-305">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/csharp) |  [<span data-ttu-id="521b6-306">View</span><span class="sxs-lookup"><span data-stu-id="521b6-306">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/nodejs)|
| <span data-ttu-id="521b6-307">Meeting meetingSidePanel</span><span class="sxs-lookup"><span data-stu-id="521b6-307">Meeting meetingSidePanel</span></span> | <span data-ttu-id="521b6-308">Microsoft Teams beispiel für die Besprechungsergehnbarkeit für die Interaktion mit dem Seitenbereich in der Besprechung.</span><span class="sxs-lookup"><span data-stu-id="521b6-308">Microsoft Teams meeting extensibility sample for interacting with the side panel in-meeting.</span></span> | [<span data-ttu-id="521b6-309">View</span><span class="sxs-lookup"><span data-stu-id="521b6-309">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-sidepanel/csharp) | [<span data-ttu-id="521b6-310">View</span><span class="sxs-lookup"><span data-stu-id="521b6-310">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-sidepanel/nodejs)|

## <a name="see-also"></a><span data-ttu-id="521b6-311">Weitere Artikel</span><span class="sxs-lookup"><span data-stu-id="521b6-311">See also</span></span>

* [<span data-ttu-id="521b6-312">Entwurfsrichtlinien für Besprechungsdialogdialog</span><span class="sxs-lookup"><span data-stu-id="521b6-312">In-meeting dialog design guidelines</span></span>](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)
* [<span data-ttu-id="521b6-313">Teams Authentifizierungsfluss für Registerkarten</span><span class="sxs-lookup"><span data-stu-id="521b6-313">Teams authentication flow for tabs</span></span>](../tabs/how-to/authentication/auth-flow-tab.md)
* [<span data-ttu-id="521b6-314">Apps für Teams Besprechungen</span><span class="sxs-lookup"><span data-stu-id="521b6-314">Apps for Teams meetings</span></span>](teams-apps-in-meetings.md)

## <a name="next-step"></a><span data-ttu-id="521b6-315">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="521b6-315">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="521b6-316">Aktivieren und Konfigurieren Ihrer Apps für Teams Besprechungen</span><span class="sxs-lookup"><span data-stu-id="521b6-316">Enable and configure your apps for Teams meetings</span></span>](enable-and-configure-your-app-for-teams-meetings.md)
