---
title: Apps in Teams-Besprechungen
author: laujan
description: Übersicht über Apps in Teams-Besprechungen basierend auf Teilnehmer- und Benutzerrolle
ms.topic: overview
ms.author: lajanuar
keywords: Rollen-API für Teams-Apps-Besprechungen für Benutzerteilnehmer
ms.openlocfilehash: 51fe2e0ebdaa56197bbebd1e5dbcf90698fb1f92
ms.sourcegitcommit: 23ed7edf145df10dcfba15c43978eae9e0d451a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2021
ms.locfileid: "50753553"
---
# <a name="apps-in-teams-meetings"></a><span data-ttu-id="6a350-104">Apps in Teams-Besprechungen</span><span class="sxs-lookup"><span data-stu-id="6a350-104">Apps in Teams meetings</span></span>

<span data-ttu-id="6a350-105">Besprechungen sind für die Produktivität in Teams entscheidend.</span><span class="sxs-lookup"><span data-stu-id="6a350-105">Meetings are key to productivity in Teams.</span></span> <span data-ttu-id="6a350-106">Sie ermöglichen Zusammenarbeit, Partnerschaft, informierte Kommunikation und geteiltes Feedback in einem inklusiven und aktiven Forum.</span><span class="sxs-lookup"><span data-stu-id="6a350-106">They enable collaboration, partnership, informed communication, and shared feedback in an inclusive and active forum.</span></span> <span data-ttu-id="6a350-107">Als Entwickler können Sie konfigurierbare Tab-, [](../messaging-extensions/what-are-messaging-extensions.md) [](../tabs/what-are-tabs.md#how-do-tabs-work) [Bot-](../bots/what-are-bots.md)und Nachrichtenerweiterungsanwendungen erstellen, um eine Teams-Besprechungserfahrung zu verbessern und zu bereichern.</span><span class="sxs-lookup"><span data-stu-id="6a350-107">As a developer, you can create [configurable tab](../tabs/what-are-tabs.md#how-do-tabs-work), [bot](../bots/what-are-bots.md), and [message extension](../messaging-extensions/what-are-messaging-extensions.md) applications to enhance and enrich a Teams meeting experience.</span></span> <span data-ttu-id="6a350-108">Besprechungsbenutzer können über den Registerkartenkatalog auf Apps zugreifen, um relevante Szenarien wie die Vorabbereitstellung eines Kanban-Board, das Starten eines Dialogfelds mit Aktionen in Besprechungen oder das Erstellen einer Umfrage nach der Besprechung zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="6a350-108">Meeting users can access apps, via the tab gallery, to enable relevant scenarios such as pre-staging a Kanban board, launching an in-meeting actionable dialog, or creating a post-meeting poll.</span></span> <span data-ttu-id="6a350-109">Ihre Besprechungs-App kann eine Benutzeroberfläche für jede Phase des Besprechungslebenszyklus basierend auf dem Teilnehmerstatus bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="6a350-109">Your meeting app can deliver a user experience for each stage of the meeting lifecycle based upon attendee status.</span></span>

<span data-ttu-id="6a350-110">Die Erweiterbarkeit der Besprechungs-App von Teams zentriert sich auf drei Konzepte:</span><span class="sxs-lookup"><span data-stu-id="6a350-110">Teams’ meeting app extensibility centers on three concepts:</span></span>

<span data-ttu-id="6a350-111">✔ **Besprechungslebenszyklus** – vor, während und nach dem Besprechungszeitrahmen.</span><span class="sxs-lookup"><span data-stu-id="6a350-111">✔ **Meeting lifecycle** — before, during, and after meeting time frame.</span></span>  
<span data-ttu-id="6a350-112">✔ **Teilnehmerrolle** – Besprechungsorganisator, Organisator oder Teilnehmer.</span><span class="sxs-lookup"><span data-stu-id="6a350-112">✔ **Participant role** — meeting organizer, presenter, or attendee.</span></span>  
<span data-ttu-id="6a350-113">✔ **Benutzertyp** – Mandanten-, Gast-, Verbund- oder anonymer Teams-Benutzer.</span><span class="sxs-lookup"><span data-stu-id="6a350-113">✔ **User type** — in-tenant, guest, federated, or anonymous Teams user.</span></span>

<!-- markdownlint-disable MD001 -->
### <a name="meeting-lifecycle-scenarios"></a><span data-ttu-id="6a350-114">Besprechungslebenszyklusszenarien</span><span class="sxs-lookup"><span data-stu-id="6a350-114">Meeting lifecycle scenarios</span></span>

## <a name="tabs"></a><span data-ttu-id="6a350-115">Registerkarten</span><span class="sxs-lookup"><span data-stu-id="6a350-115">Tabs</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6a350-116">Wie bei allen Registerkartenanwendungen muss Ihre App den Teams [-SSO-Authentifizierungsfluss](../tabs/how-to/authentication/auth-aad-sso.md) für Registerkarten befolgen.</span><span class="sxs-lookup"><span data-stu-id="6a350-116">As with all tab applications, Your app will need to follow the Teams [SSO authentication flow](../tabs/how-to/authentication/auth-aad-sso.md) for tabs.</span></span>

> [!NOTE]
> * <span data-ttu-id="6a350-117">Mobile Clients unterstützen Registerkarten nur in Oberflächen vor besprechungen und nach Besprechungen.</span><span class="sxs-lookup"><span data-stu-id="6a350-117">Mobile clients support tabs only in pre-meeting and post-meeting surfaces.</span></span> <span data-ttu-id="6a350-118">Die Besprechungserfahrungen, z. B. das Dialogfeld in besprechungen und das Panel auf Mobilgeräten, werden in Kürze verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="6a350-118">The in-meeting experiences, such as in-meeting dialog and panel on mobile will be available soon.</span></span>
> * <span data-ttu-id="6a350-119">Apps werden nur in privaten geplanten Besprechungen unterstützt.</span><span class="sxs-lookup"><span data-stu-id="6a350-119">Apps are supported only in private scheduled meetings.</span></span>

### <a name="pre-meeting-app-experience"></a><span data-ttu-id="6a350-120">App-Erfahrung vor besprechung</span><span class="sxs-lookup"><span data-stu-id="6a350-120">Pre-meeting app experience</span></span>

<span data-ttu-id="6a350-121">**Vorbetreff:**</span><span class="sxs-lookup"><span data-stu-id="6a350-121">**Pre-meeting experience:**</span></span>

![Pre-Meeting-Erfahrung](../assets/images/apps-in-meetings/PreMeeting.png)

<span data-ttu-id="6a350-123">**Registerkarte "Pre-Meeting":**</span><span class="sxs-lookup"><span data-stu-id="6a350-123">**Pre-meeting tab:**</span></span>

![Registerkartenansicht vor der Besprechung](../assets/images/apps-in-meetings/PreMeetingTab.png)

<span data-ttu-id="6a350-125">✔ Benutzer mit Berechtigungen können apps zu einer Besprechung über den Registerkartenkatalog auf zwei Arten hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="6a350-125">✔ Permissioned users can add apps to a meeting via the tab gallery in two ways:</span></span>

<span data-ttu-id="6a350-126">&emsp;&emsp;&#9679; Über die **Registerkarte Details** im Teams-Planungsformular.</span><span class="sxs-lookup"><span data-stu-id="6a350-126">&emsp;&emsp;&#9679; Via the **Details** tab on the Teams scheduling form.</span></span>

<span data-ttu-id="6a350-127">&emsp;&emsp;&#9679; Über die Registerkarte **Besprechungschat** in einer vorhandenen Besprechung.</span><span class="sxs-lookup"><span data-stu-id="6a350-127">&emsp;&emsp;&#9679;  Via the meeting **Chat** tab in an existing meeting.</span></span></br> </br>

<span data-ttu-id="6a350-128">✔ Tab-Apps sind in  **Besprechungsdetails und Chats-Seiten** über eine Plussymbolschaltfläche (➕) zugänglich.|</span><span class="sxs-lookup"><span data-stu-id="6a350-128">✔ Tab apps are accessible in meetings **Details** and **Chats** pages using a plus icon (➕) button.|</span></span>

<span data-ttu-id="6a350-129">✔ Tablayout sollte sich in einem organisierten Zustand befinden, wenn mehr als zehn Umfragen oder Umfragen durchgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="6a350-129">✔  Tab layout should be in an organized state if there are more than ten polls or surveys.</span></span>

### <a name="in-meeting-app-experience"></a><span data-ttu-id="6a350-130">In-Meeting-App-Erfahrung</span><span class="sxs-lookup"><span data-stu-id="6a350-130">In-meeting app experience</span></span>

<span data-ttu-id="6a350-131">✔ Besprechungs-Apps werden in der oberen Leiste des Chatfensters und als Registerkartenerfahrung in Besprechungen über die Registerkarte In-Meeting gehostet. Wenn Benutzer einer Besprechung über den Registerkartenkatalog eine Registerkarte hinzufügen, werden Apps angezeigt, die sich während der **Besprechungserfahrung** befinden.</span><span class="sxs-lookup"><span data-stu-id="6a350-131">✔ Meeting apps will be hosted in the top upper bar of the chat window and as in-meeting tab experience via the in-meeting tab. When users add a tab to a meeting through the tab gallery, apps that are **during meeting** experiences will be surfaced.</span></span>

<span data-ttu-id="6a350-132">✔ Berechtigte Benutzer können Apps während der Besprechung hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="6a350-132">✔ Permissioned users can add apps while in the meeting.</span></span>

<span data-ttu-id="6a350-133">✔ Wenn apps im Kontext einer Besprechung geladen werden, können sie das Teams Client SDK nutzen, um auf das zu zugreifen und die Erfahrung entsprechend `meetingId` `userMri` zu `frameContext` rendern.</span><span class="sxs-lookup"><span data-stu-id="6a350-133">✔ When loaded in the context of a meeting, apps will be able to leverage the Teams Client SDK to access the `meetingId`, `userMri`, and `frameContext` to appropriately render the experience.</span></span>

<span data-ttu-id="6a350-134">✔ Exportieren eines Ergebnisses einer Umfrage oder Umfrage sollte die Benutzer mit der Meldung "Ergebnisse erfolgreich heruntergeladen" benachrichtigen.</span><span class="sxs-lookup"><span data-stu-id="6a350-134">✔ Exporting a result of a survey or polls should notify the users stating, ‘results successfully downloaded’.</span></span>

<span data-ttu-id="6a350-135">✔ Damit eine App in einer Teams-Besprechung in zwei Bereichen sichtbar ist:</span><span class="sxs-lookup"><span data-stu-id="6a350-135">✔ For an app to be visible in a Teams meeting in two areas:</span></span>

<span data-ttu-id="6a350-136">&emsp;&emsp;&#9679; **Seitenbereich .**</span><span class="sxs-lookup"><span data-stu-id="6a350-136">&emsp;&emsp;&#9679; **Side panel**.</span></span> </br>

> [!NOTE]
> <span data-ttu-id="6a350-137">Wenn Ihr _App-Manifest_ angibt, dass Ihre Registerkarte [für](create-apps-for-teams-meetings.md#during-a-meeting)den Seitenbereich optimiert ist, wird sie dort angezeigt.</span><span class="sxs-lookup"><span data-stu-id="6a350-137">If your _app manifest_ specifies that your tab is [optimized for side panel](create-apps-for-teams-meetings.md#during-a-meeting), that is where it will be displayed.</span></span> <span data-ttu-id="6a350-138">Sie kann auch Teil einer Share-Tray-Erfahrung sein, die den angegebenen Entwurfsrichtlinien unterliegt.</span><span class="sxs-lookup"><span data-stu-id="6a350-138">It can also be part of a share-tray experience, subject to specified design guidelines.</span></span>

<span data-ttu-id="6a350-139">&emsp;&emsp;&#9679; **In-Meeting-Dialogfeld .**</span><span class="sxs-lookup"><span data-stu-id="6a350-139">&emsp;&emsp;&#9679; **In-meeting dialog**.</span></span> <span data-ttu-id="6a350-140">Verwenden Sie das Dialogfeld in der Besprechung, um Inhalte mit Aktionen für Besprechungsteilnehmer anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="6a350-140">Use the in-meeting dialog to showcase actionable content for meeting participants.</span></span> <span data-ttu-id="6a350-141">*Weitere Informationen* [finden Sie unter Erstellen von Apps für Teams-Besprechungen.](create-apps-for-teams-meetings.md)</span><span class="sxs-lookup"><span data-stu-id="6a350-141">*See* [Create Apps for Teams meetings](create-apps-for-teams-meetings.md).</span></span>

<span data-ttu-id="6a350-142">**In-Meeting-Erfahrung:**</span><span class="sxs-lookup"><span data-stu-id="6a350-142">**In-meeting experience:**</span></span>

![In-Meeting-Erfahrung](../assets/images/apps-in-meetings/in-meeting-experience.png)

![In-Meeting-Dialog-Ansicht](../assets/images/apps-in-meetings/in-meeting-dialog.png)

<span data-ttu-id="6a350-145">**In-Meeting-Dialogfeld mit Aktionen für Benutzer:**</span><span class="sxs-lookup"><span data-stu-id="6a350-145">**In-meeting actionable dialog for users:**</span></span>

![Dialogansicht](../assets/images/apps-in-meetings/in-meeting-dialog-view.png)

### <a name="post-meeting-app-experience"></a><span data-ttu-id="6a350-147">App-Erfahrung nach der Besprechung</span><span class="sxs-lookup"><span data-stu-id="6a350-147">Post-meeting app experience</span></span>

<span data-ttu-id="6a350-148">**Nach der Besprechung:**</span><span class="sxs-lookup"><span data-stu-id="6a350-148">**Post-meeting experience:**</span></span>

![Nach besprechungsansicht](../assets/images/apps-in-meetings/PostMeeting.png)

<span data-ttu-id="6a350-150">✔ Das App-Szenario nach der Besprechung ähnelt der aktuellen Nachbesprechung mit dem zusätzlichen Vorteil, dass Registerkarten auf der Oberfläche vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="6a350-150">✔ The post-meeting app scenario is similar to the current post-meeting experience with the added benefit of having tabs that exist within the surface.</span></span> 

<span data-ttu-id="6a350-151">✔ Berechtigte Benutzer können Apps aus dem Registerkartenkatalog zu einer Besprechung über die  Registerkarte **Details** im Teams-Planungsformular und die Registerkarte Besprechungschat in einer vorhandenen Besprechung hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="6a350-151">✔ Permissioned users can add apps from the tab gallery to a meeting via the **Details** tab on the Teams scheduling form and the meeting **Chat** tab in an existing meeting.</span></span>

<span data-ttu-id="6a350-152">✔ Tablayout sollte sich in einem organisierten Zustand befinden, wenn mehr als zehn Umfragen oder Umfragen durchgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="6a350-152">✔  Tab layout should be in an organized state if there are more than ten polls or surveys.</span></span>

### <a name="bots"></a><span data-ttu-id="6a350-153">Bots</span><span class="sxs-lookup"><span data-stu-id="6a350-153">Bots</span></span>

<span data-ttu-id="6a350-154">Beginnen Sie bei der Botimplementierung mit [dem Erstellen eines Bots,](../build-your-first-app/build-bot.md) und fahren Sie dann mit dem Erstellen von Apps [für Teams-Besprechungen fort.](../apps-in-teams-meetings/create-apps-for-teams-meetings.md#meeting-apps-api-reference)</span><span class="sxs-lookup"><span data-stu-id="6a350-154">For bot implementation, start with [build a bot](../build-your-first-app/build-bot.md) and then continue with [create apps for Teams meetings](../apps-in-teams-meetings/create-apps-for-teams-meetings.md#meeting-apps-api-reference).</span></span>

### <a name="messaging-extensions"></a><span data-ttu-id="6a350-155">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="6a350-155">Messaging extensions</span></span>

<span data-ttu-id="6a350-156">Beginnen Sie bei der Implementierung von Messagingerweiterungen mit dem Erstellen einer [Messagingerweiterung,](../messaging-extensions/how-to/create-messaging-extension.md) und fahren Sie dann mit dem Erstellen von [Apps für Teams-Besprechungen fort.](../apps-in-teams-meetings/create-apps-for-teams-meetings.md#meeting-apps-api-reference)</span><span class="sxs-lookup"><span data-stu-id="6a350-156">For messaging extension implementation, start with [build a messaging extension](../messaging-extensions/how-to/create-messaging-extension.md) and then continue with [create apps for Teams meetings](../apps-in-teams-meetings/create-apps-for-teams-meetings.md#meeting-apps-api-reference).</span></span>

## <a name="participant-roles-and-user-types-in-a-meeting"></a><span data-ttu-id="6a350-157">Teilnehmerrollen und Benutzertypen in einer Besprechung</span><span class="sxs-lookup"><span data-stu-id="6a350-157">Participant roles and user types in a meeting</span></span>

![Teilnehmer an einer Besprechung](../assets/images/apps-in-meetings/participant-roles.png)

### <a name="participant-roles"></a><span data-ttu-id="6a350-159">Teilnehmerrollen</span><span class="sxs-lookup"><span data-stu-id="6a350-159">Participant roles</span></span>

<span data-ttu-id="6a350-160">Sie können Ihre App mit teilnehmerspezifischer Autorisierung entwerfen.</span><span class="sxs-lookup"><span data-stu-id="6a350-160">You can design your app with participant-specific authorization.</span></span> <span data-ttu-id="6a350-161">Beispielsweise kann nur ein Organisator und/oder Organisator eine Umfrage in Besprechungen erstellen.</span><span class="sxs-lookup"><span data-stu-id="6a350-161">For example, perhaps only an organizer and/or presenter can create a poll in meetings.</span></span> <span data-ttu-id="6a350-162">Obwohl die Standardeinstellungen für Teilnehmer vom IT-Administrator einer Organisation bestimmt werden, kann es sein, dass ein Besprechungsorganisator die Einstellungen für eine bestimmte Besprechung ändern möchte.</span><span class="sxs-lookup"><span data-stu-id="6a350-162">Although default participant settings are determined by an organization's IT administrator, a meeting organizer may want to change the settings for a specific meeting.</span></span> <span data-ttu-id="6a350-163">Organisatoren können diese Änderungen auf der Webseite "Besprechungsoptionen" vornehmen.</span><span class="sxs-lookup"><span data-stu-id="6a350-163">Organizers can make these changes on the Meeting options web page.</span></span>

1. <span data-ttu-id="6a350-164">**Organizer**.</span><span class="sxs-lookup"><span data-stu-id="6a350-164">**Organizer**.</span></span> <span data-ttu-id="6a350-165">Der Organisator plant eine Besprechung, legt die Besprechungsoptionen fest, weist Besprechungsrollen zu und startet die Besprechung.</span><span class="sxs-lookup"><span data-stu-id="6a350-165">The organizer schedules a meeting, sets the meeting options, assigns meeting roles, and starts the meeting.</span></span> <span data-ttu-id="6a350-166">Nur Benutzer mit einem M365-Konto (im Besitz einer Teams-Lizenz) können Organisator sein und Die Teilnehmerberechtigungen steuern.</span><span class="sxs-lookup"><span data-stu-id="6a350-166">Only users with a M365 account (possessing a Teams license) can be organizers and control attendee permissions.</span></span>
1. <span data-ttu-id="6a350-167">**Presenter**.</span><span class="sxs-lookup"><span data-stu-id="6a350-167">**Presenter**.</span></span> <span data-ttu-id="6a350-168">Organisator haben nahezu dieselben Funktionen wie Organisator. Ein Organisator kann jedoch keinen Organisator aus der Sitzung entfernen oder Besprechungsoptionen für die Sitzung ändern.</span><span class="sxs-lookup"><span data-stu-id="6a350-168">Presenters have nearly the same capabilities as organizer; however, a presenter cannot remove an organizer from the session or modify meeting options for the session.</span></span> <span data-ttu-id="6a350-169">Standardmäßig haben Teilnehmer, die an einer Besprechung teilnahmen, die Rolle des Moderators.</span><span class="sxs-lookup"><span data-stu-id="6a350-169">By default, participants joining a meeting have the presenter role.</span></span>
1. <span data-ttu-id="6a350-170">**Attendee**.</span><span class="sxs-lookup"><span data-stu-id="6a350-170">**Attendee**.</span></span> <span data-ttu-id="6a350-171">Ein Teilnehmer ist ein Benutzer, der zur Teilnahme an einer Besprechung eingeladen wurde, der jedoch nicht autorisiert ist, als Moderator zu fungieren.</span><span class="sxs-lookup"><span data-stu-id="6a350-171">An attendee is a user who has been invited to attend a meeting but who is not authorized to act as a presenter.</span></span> <span data-ttu-id="6a350-172">Teilnehmer können mit anderen Besprechungsmitgliedern interagieren, aber keine Besprechungseinstellungen verwalten oder Inhalte freigeben.</span><span class="sxs-lookup"><span data-stu-id="6a350-172">Attendees can interact with other meeting members but cannot manage any of the meeting settings or share content.</span></span>

<span data-ttu-id="6a350-173">_Siehe_ [ **Rollen in einer Teams-Besprechung**](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019)</span><span class="sxs-lookup"><span data-stu-id="6a350-173">_See_ [**Roles in a Teams meeting**](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019)</span></span>

<span data-ttu-id="6a350-174">Sie können wie folgt auf  **die Seite Besprechungsoptionen** zugreifen:</span><span class="sxs-lookup"><span data-stu-id="6a350-174">You can access the  **Meeting options** page as follows:</span></span>

<span data-ttu-id="6a350-175">&#11200; In Teams wechseln Sie zu **Kalenderkalenderlogo,** wählen Sie eine Besprechung ![ und dann ](../assets/images/apps-in-meetings/calendar-logo.png) **Besprechungsoptionen aus.**</span><span class="sxs-lookup"><span data-stu-id="6a350-175">&#11200; In Teams, go to **Calendar** ![calendar logo](../assets/images/apps-in-meetings/calendar-logo.png), select a meeting, and then **Meeting options**.</span></span>

<span data-ttu-id="6a350-176">&#11200; Wählen Sie in einer Besprechungseinladung **Besprechungsoptionen aus.**</span><span class="sxs-lookup"><span data-stu-id="6a350-176">&#11200; In a meeting invitation, select **Meeting options**.</span></span>

<span data-ttu-id="6a350-177">&#11200; Wählen Sie während einer Besprechung **das** Symbol Teilnehmer anzeigen ![ in den ](../assets/images/apps-in-meetings/show-participants.png) Besprechungssteuerelementen anzeigen aus.</span><span class="sxs-lookup"><span data-stu-id="6a350-177">&#11200; During a meeting, select **Show participants** ![show participants icon](../assets/images/apps-in-meetings/show-participants.png) in the meeting controls.</span></span> <span data-ttu-id="6a350-178">Wählen Sie dann oberhalb der Liste der Teilnehmer Berechtigungen **verwalten aus.**</span><span class="sxs-lookup"><span data-stu-id="6a350-178">Then, above the list of participants, choose **Manage permissions**.</span></span>

### <a name="user-types"></a><span data-ttu-id="6a350-179">Benutzertypen</span><span class="sxs-lookup"><span data-stu-id="6a350-179">User types</span></span>

> [!NOTE]
> <span data-ttu-id="6a350-180">Benutzertypen können an Besprechungen teilnehmen und eine der oben beschriebenen Teilnehmerrollen annehmen.</span><span class="sxs-lookup"><span data-stu-id="6a350-180">User types can join meetings and assume one of the participant roles described above.</span></span> <span data-ttu-id="6a350-181">Der Benutzertyp wird nicht als Teil der **getParticipantRole-API verfügbar** gemacht.</span><span class="sxs-lookup"><span data-stu-id="6a350-181">The User type is not exposed as part of the **getParticipantRole** API.</span></span>

1. <span data-ttu-id="6a350-182">**Mandantenindant**.</span><span class="sxs-lookup"><span data-stu-id="6a350-182">**In-tenant**.</span></span> <span data-ttu-id="6a350-183">Diese Benutzer gehören zur Organisation und verfügen über Anmeldeinformationen in Azure Active Directory für den Mandanten.</span><span class="sxs-lookup"><span data-stu-id="6a350-183">These users belong to the organization and have credentials in Azure Active Directory for the tenant.</span></span> <span data-ttu-id="6a350-184">Es handelt sich in der Regel um Vollzeit-, Standort- oder Remotemitarbeiter.</span><span class="sxs-lookup"><span data-stu-id="6a350-184">They are usually full-time, onsite or remote employees.</span></span>
1. <span data-ttu-id="6a350-185">**Gast**.</span><span class="sxs-lookup"><span data-stu-id="6a350-185">**Guest**.</span></span> <span data-ttu-id="6a350-186">Ein Gast ist ein Teilnehmer aus einer anderen Organisation, der eingeladen wurde, auf Teams oder andere Ressourcen im Mandanten Ihrer Organisation zu zugreifen.</span><span class="sxs-lookup"><span data-stu-id="6a350-186">A guest is a participant from another organization who has been invited to access Teams or other resources in your organization's tenant.</span></span> <span data-ttu-id="6a350-187">Gäste werden zum Active Directory Ihrer Organisation hinzugefügt und können nahezu dieselben Teams-Funktionen wie ein systemeigenes Teammitglied mit Vollzugriff auf Teamchats, Besprechungen und Dateien erhalten.</span><span class="sxs-lookup"><span data-stu-id="6a350-187">Guests are added to your organization’s Active Directory and can be given nearly all the same Teams capabilities as a native team member with full access to team chats, meetings, and files.</span></span> <span data-ttu-id="6a350-188">_Siehe_ [Gastzugriff in Microsoft Teams](/microsoftteams/guest-access)</span><span class="sxs-lookup"><span data-stu-id="6a350-188">_See_ [Guest access in Microsoft Teams](/microsoftteams/guest-access)</span></span>
1. <span data-ttu-id="6a350-189">**Federated/External**.</span><span class="sxs-lookup"><span data-stu-id="6a350-189">**Federated/External**.</span></span> <span data-ttu-id="6a350-190">Ein Verbundbenutzer ist ein externer Teams-Benutzer in einer anderen Organisation, der zur Teilnahme an einer Besprechung eingeladen wurde.</span><span class="sxs-lookup"><span data-stu-id="6a350-190">A federated user is an external Teams user in another organization who has been invited to join a meeting.</span></span> <span data-ttu-id="6a350-191">Da diese Benutzer über gültige Anmeldeinformationen bei Verbundpartnern verfügen, werden sie von Teams als authentifiziert behandelt, haben jedoch keinen Zugriff auf Ihre Teams oder andere freigegebene Ressourcen aus Ihrer Organisation.</span><span class="sxs-lookup"><span data-stu-id="6a350-191">Since these users have valid credentials with federated partners, they are treated as authenticated by Teams but do not have access to your teams or other shared resources from your organization.</span></span> <span data-ttu-id="6a350-192">Wenn externe Benutzer Zugriff auf Teams und Kanäle haben sollen, ist der Gastzugriff möglicherweise eine bessere Option.</span><span class="sxs-lookup"><span data-stu-id="6a350-192">If you want external users to have access to teams and channels, guest access might be a better option.</span></span> <span data-ttu-id="6a350-193">_Weitere Informationen_ [finden Sie unter Verwalten des externen Zugriffs in Microsoft Teams](/microsoftteams/manage-external-access)</span><span class="sxs-lookup"><span data-stu-id="6a350-193">_See_ [Manage external access in Microsoft Teams](/microsoftteams/manage-external-access)</span></span>
1. <span data-ttu-id="6a350-194">**Anonym**.</span><span class="sxs-lookup"><span data-stu-id="6a350-194">**Anonymous**.</span></span> <span data-ttu-id="6a350-195">Anonyme Benutzer verfügen nicht über eine Active Directory-Identität und sind nicht mit einem Mandanten partnerisiert.</span><span class="sxs-lookup"><span data-stu-id="6a350-195">Anonymous users do not have an Active Directory identity and are not federated with a tenant.</span></span> <span data-ttu-id="6a350-196">Der anonyme Teilnehmer ist wie ein externer Benutzer, seine Identität wird jedoch nicht in die Besprechung projiziert.</span><span class="sxs-lookup"><span data-stu-id="6a350-196">The anonymous participant is like an external user, but their identity is not projected into the meeting.</span></span> <span data-ttu-id="6a350-197">Anonyme Benutzer können in einem Besprechungsfenster nicht auf Apps zugreifen.</span><span class="sxs-lookup"><span data-stu-id="6a350-197">Anonymous users will not be able to access apps in a meeting window.</span></span>

## <a name="next-steps"></a><span data-ttu-id="6a350-198">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="6a350-198">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6a350-199">Entwerfen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="6a350-199">Design your app</span></span>](../apps-in-teams-meetings/design/designing-apps-in-meetings.md)
> [!div class="nextstepaction"]
> [<span data-ttu-id="6a350-200">Erstellen Sie Ihre Anwendung</span><span class="sxs-lookup"><span data-stu-id="6a350-200">Build your app</span></span>](create-apps-for-teams-meetings.md)
