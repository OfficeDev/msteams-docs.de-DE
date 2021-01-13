---
title: Apps in Teams-Besprechungen
author: laujan
description: Übersicht über Apps in Teams-Besprechungen basierend auf der Teilnehmer- und Benutzerrolle
ms.topic: overview
ms.author: lajanuar
keywords: Teams-Apps-Besprechungen – Benutzerteilnehmer-Rollen-API
ms.openlocfilehash: 217737cbbf73104d4d78cf817e6df0244229c53c
ms.sourcegitcommit: 4539479289b43812eaae07a1c0f878bed815d2d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/12/2021
ms.locfileid: "49797757"
---
# <a name="apps-in-teams-meetings"></a><span data-ttu-id="26b83-104">Apps in Teams-Besprechungen</span><span class="sxs-lookup"><span data-stu-id="26b83-104">Apps in Teams meetings</span></span>

<span data-ttu-id="26b83-105">Besprechungen sind für die Produktivität in Teams entscheidend.</span><span class="sxs-lookup"><span data-stu-id="26b83-105">Meetings are key to productivity in Teams.</span></span> <span data-ttu-id="26b83-106">Sie ermöglichen Zusammenarbeit, Partnerschaft, informierte Kommunikation und geteiltes Feedback in einem inklusiven und aktiven Forum.</span><span class="sxs-lookup"><span data-stu-id="26b83-106">They enable collaboration, partnership, informed communication, and shared feedback in an inclusive and active forum.</span></span> <span data-ttu-id="26b83-107">Als Entwickler können Sie konfigurierbare Anwendungen für [](../messaging-extensions/what-are-messaging-extensions.md) [Registerkarten,](../tabs/what-are-tabs.md#how-do-tabs-work) [Bots](../bots/what-are-bots.md)und Nachrichtenerweiterungen erstellen, um eine Besprechungserfahrung in Teams zu verbessern und zu erweitern.</span><span class="sxs-lookup"><span data-stu-id="26b83-107">As a developer, you can create [configurable tab](../tabs/what-are-tabs.md#how-do-tabs-work), [bot](../bots/what-are-bots.md), and [message extension](../messaging-extensions/what-are-messaging-extensions.md) applications to enhance and enrich a Teams meeting experience.</span></span> <span data-ttu-id="26b83-108">Besprechungsbenutzer können über den Registerkartenkatalog auf Apps zugreifen, um relevante Szenarien wie die Vorabbereitstellung eines Kanban-Board, das Starten eines Dialogfelds mit Aktionen in Besprechungen oder das Erstellen einer Umfrage nach der Besprechung zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="26b83-108">Meeting users can access apps, via the tab gallery, to enable relevant scenarios such as pre-staging a Kanban board, launching an in-meeting actionable dialog, or creating a post-meeting poll.</span></span> <span data-ttu-id="26b83-109">Ihre Besprechungs-App kann eine Benutzererfahrung für jede Phase des Besprechungslebenszyklus basierend auf dem Teilnehmerstatus bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="26b83-109">Your meeting app can deliver a user experience for each stage of the meeting lifecycle based upon attendee status.</span></span>

<span data-ttu-id="26b83-110">Die Erweiterbarkeit der Besprechungs-App von Teams zentriert sich auf drei Konzepte:</span><span class="sxs-lookup"><span data-stu-id="26b83-110">Teams’ meeting app extensibility centers on three concepts:</span></span>

<span data-ttu-id="26b83-111">✔ **Besprechungslebenszyklus** – vor, während und nach Besprechungszeitrahmen.</span><span class="sxs-lookup"><span data-stu-id="26b83-111">✔ **Meeting lifecycle** — before, during, and after meeting time frame.</span></span>  
<span data-ttu-id="26b83-112">✔ Rolle **"Teilnehmer"** – Besprechungsorganisator, Organisator oder Teilnehmer.</span><span class="sxs-lookup"><span data-stu-id="26b83-112">✔ **Participant role** — meeting organizer, presenter, or attendee.</span></span>  
<span data-ttu-id="26b83-113">✔ **Benutzertyp –** Mandanten-, Gast-, Verbund- oder anonymer Teams-Benutzer.</span><span class="sxs-lookup"><span data-stu-id="26b83-113">✔ **User type** — in-tenant, guest, federated, or anonymous Teams user.</span></span>

<!-- markdownlint-disable MD001 -->
### <a name="meeting-lifecycle-scenarios"></a><span data-ttu-id="26b83-114">Szenarien für den Besprechungslebenszyklus</span><span class="sxs-lookup"><span data-stu-id="26b83-114">Meeting lifecycle scenarios</span></span>

## <a name="tabs"></a><span data-ttu-id="26b83-115">Registerkarten</span><span class="sxs-lookup"><span data-stu-id="26b83-115">Tabs</span></span>

> [!IMPORTANT]
> <span data-ttu-id="26b83-116">Wie bei allen Registerkartenanwendungen muss Ihre App den [Teams-SSO-Authentifizierungsfluss](../tabs/how-to/authentication/auth-aad-sso.md) für Registerkarten befolgen.</span><span class="sxs-lookup"><span data-stu-id="26b83-116">As with all tab applications, Your app will need to follow the Teams [SSO authentication flow](../tabs/how-to/authentication/auth-aad-sso.md) for tabs.</span></span>

> [!NOTE]
> <span data-ttu-id="26b83-117">Mobile Clients unterstützen Registerkarten nur in Oberflächen vor und nach Besprechungen.</span><span class="sxs-lookup"><span data-stu-id="26b83-117">Mobile clients support Tabs only in Pre and Post Meeting Surfaces.</span></span> <span data-ttu-id="26b83-118">Die Besprechungserfahrungen (Dialogfeld und Bereich in Besprechungen) auf mobilgeräten werden in Kürze verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="26b83-118">The In-meeting experiences (in-meeting dialog and panel) on mobile will be available soon</span></span>

### <a name="pre-meeting-app-experience"></a><span data-ttu-id="26b83-119">App-Erfahrung vor der Besprechung</span><span class="sxs-lookup"><span data-stu-id="26b83-119">Pre-meeting app experience</span></span>

<span data-ttu-id="26b83-120">**Vor der Besprechung:**</span><span class="sxs-lookup"><span data-stu-id="26b83-120">**Pre-meeting experience:**</span></span>

![Benutzererfahrung vor der Besprechung](../assets/images/apps-in-meetings/PreMeeting.png)

<span data-ttu-id="26b83-122">**Registerkarte "Pre-meeting":**</span><span class="sxs-lookup"><span data-stu-id="26b83-122">**Pre-meeting tab:**</span></span>

![Registerkartenansicht vor der Besprechung](../assets/images/apps-in-meetings/PreMeetingTab.png)

<span data-ttu-id="26b83-124">✔ Benutzer mit Berechtigung können apps zu einer Besprechung über den Registerkartenkatalog auf zwei Arten hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="26b83-124">✔ Permissioned users can add apps to a meeting via the tab gallery in two ways:</span></span>

<span data-ttu-id="26b83-125">&emsp;&emsp;&#9679; Über die Registerkarte **"Details"** im Teams-Planungsformular.</span><span class="sxs-lookup"><span data-stu-id="26b83-125">&emsp;&emsp;&#9679; Via the **Details** tab on the Teams scheduling form.</span></span>

<span data-ttu-id="26b83-126">&emsp;&emsp;&#9679; Über die Registerkarte **"Besprechungschat"** in einer vorhandenen Besprechung.</span><span class="sxs-lookup"><span data-stu-id="26b83-126">&emsp;&emsp;&#9679;  Via the meeting **Chat** tab in an existing meeting.</span></span></br> </br>

<span data-ttu-id="26b83-127">✔ Registerkarten-Apps können auf  **Besprechungsdetails-** und Chatseiten über eine Schaltfläche für ein Pluszeichen (➕) zugegriffen werden.|</span><span class="sxs-lookup"><span data-stu-id="26b83-127">✔ Tab apps are accessible in meetings **Details** and **Chats** pages using a plus icon (➕) button.|</span></span>

<span data-ttu-id="26b83-128">✔ Registerkartenlayout sollte sich in einem organisierten Zustand befinden, wenn mehr als zehn Umfragen oder Umfragen durchgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="26b83-128">✔  Tab layout should be in an organized state if there are more than ten polls or surveys.</span></span>

### <a name="in-meeting-app-experience"></a><span data-ttu-id="26b83-129">In-Meeting-App-Erfahrung</span><span class="sxs-lookup"><span data-stu-id="26b83-129">In-meeting app experience</span></span>

<span data-ttu-id="26b83-130">✔ Besprechungs-Apps werden in der oberen oberen Leiste des Chatfensters und als Registerkartenerfahrung in Besprechungen über die Registerkarte "In-Meeting" gehostet. Wenn Benutzer einer Besprechung über den Registerkartenkatalog  eine Registerkarte hinzufügen, werden Apps angezeigt, die sich während der Besprechungsoberfläche befinden.</span><span class="sxs-lookup"><span data-stu-id="26b83-130">✔ Meeting apps will be hosted in the top upper bar of the chat window and as in-meeting tab experience via the in-meeting tab. When users add a tab to a meeting through the tab gallery, apps that are **during meeting** experiences will be surfaced.</span></span>

<span data-ttu-id="26b83-131">✔ Berechtigte Benutzer können während der Besprechung Apps hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="26b83-131">✔ Permissioned users can add apps while in the meeting.</span></span>

<span data-ttu-id="26b83-132">✔ Im Kontext einer Besprechung geladen werden, können Apps das Teams-Client-SDK verwenden, um auf das zu greifen und die Erfahrung entsprechend `meetingId` `userMri` zu `frameContext` rendern.</span><span class="sxs-lookup"><span data-stu-id="26b83-132">✔ When loaded in the context of a meeting, apps will be able to leverage the Teams Client SDK to access the `meetingId`, `userMri`, and `frameContext` to appropriately render the experience.</span></span>

<span data-ttu-id="26b83-133">✔ Exportieren eines Ergebnisses einer Umfrage oder Umfrage sollte die Benutzer darüber informieren, dass die Ergebnisse erfolgreich heruntergeladen wurden.</span><span class="sxs-lookup"><span data-stu-id="26b83-133">✔ Exporting a result of a survey or polls should notify the users stating, ‘results successfully downloaded’.</span></span>

<span data-ttu-id="26b83-134">✔, damit eine App in einer Besprechung in Teams in zwei Bereichen sichtbar ist:</span><span class="sxs-lookup"><span data-stu-id="26b83-134">✔ For an app to be visible in a Teams meeting in two areas:</span></span>

<span data-ttu-id="26b83-135">&emsp;&emsp;&#9679; **Seitenbereich .**</span><span class="sxs-lookup"><span data-stu-id="26b83-135">&emsp;&emsp;&#9679; **Side panel**.</span></span> </br>

> [!NOTE]
> <span data-ttu-id="26b83-136">Wenn Ihr _App-Manifest_ angibt, dass Ihre Registerkarte für [den](create-apps-for-teams-meetings.md#during-a-meeting)Seitenbereich optimiert ist, wird sie dort angezeigt.</span><span class="sxs-lookup"><span data-stu-id="26b83-136">If your _app manifest_ specifies that your tab is [optimized for side panel](create-apps-for-teams-meetings.md#during-a-meeting), that is where it will be displayed.</span></span> <span data-ttu-id="26b83-137">Sie kann auch Teil einer Share-Tray-Erfahrung sein, die bestimmten Entwurfsrichtlinien unterliegt.</span><span class="sxs-lookup"><span data-stu-id="26b83-137">It can also be part of a share-tray experience, subject to specified design guidelines.</span></span>

<span data-ttu-id="26b83-138">&emsp;&emsp;&#9679; **In-Meeting-Dialogfeld .**</span><span class="sxs-lookup"><span data-stu-id="26b83-138">&emsp;&emsp;&#9679; **In-meeting dialog**.</span></span> <span data-ttu-id="26b83-139">Verwenden Sie das Dialogfeld in der Besprechung, um Aktionen für Besprechungsteilnehmer anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="26b83-139">Use the in-meeting dialog to showcase actionable content for meeting participants.</span></span> <span data-ttu-id="26b83-140">*Siehe "Erstellen* [von Apps für Teams-Besprechungen".](create-apps-for-teams-meetings.md)</span><span class="sxs-lookup"><span data-stu-id="26b83-140">*See* [Create Apps for Teams meetings](create-apps-for-teams-meetings.md).</span></span>

<span data-ttu-id="26b83-141">**In-Meeting-Erfahrung:**</span><span class="sxs-lookup"><span data-stu-id="26b83-141">**In-meeting experience:**</span></span>

![In-Meeting-Erfahrung](../assets/images/apps-in-meetings/in-meeting-experience.png)

![Ansicht "Besprechungsdialog"](../assets/images/apps-in-meetings/in-meeting-dialog.png)

<span data-ttu-id="26b83-144">**Dialogfeld mit Aktionen in Besprechungen für Benutzer:**</span><span class="sxs-lookup"><span data-stu-id="26b83-144">**In-meeting actionable dialog for users:**</span></span>

![Dialogansicht](../assets/images/apps-in-meetings/in-meeting-dialog-view.png)

### <a name="post-meeting-app-experience"></a><span data-ttu-id="26b83-146">App-Erfahrung nach der Besprechung</span><span class="sxs-lookup"><span data-stu-id="26b83-146">Post-meeting app experience</span></span>

<span data-ttu-id="26b83-147">**Nach der Besprechung:**</span><span class="sxs-lookup"><span data-stu-id="26b83-147">**Post-meeting experience:**</span></span>

![Ansicht nach der Besprechung](../assets/images/apps-in-meetings/PostMeeting.png)

<span data-ttu-id="26b83-149">✔ das Post-Meeting-App-Szenario ähnelt der aktuellen Oberfläche nach der Besprechung mit dem zusätzlichen Vorteil, dass Registerkarten innerhalb der Oberfläche vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="26b83-149">✔ The post-meeting app scenario is similar to the current post-meeting experience with the added benefit of having tabs that exist within the surface.</span></span> 

<span data-ttu-id="26b83-150">✔ berechtigten Benutzern können Apps aus dem Registerkartenkatalog über die Registerkarte **"Details"**  im Planungsformular von Teams und die Registerkarte "Besprechungschat" in einer vorhandenen Besprechung zu einer Besprechung hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="26b83-150">✔ Permissioned users can add apps from the tab gallery to a meeting via the **Details** tab on the Teams scheduling form and the meeting **Chat** tab in an existing meeting.</span></span>

<span data-ttu-id="26b83-151">✔ Registerkartenlayout sollte sich in einem organisierten Zustand befinden, wenn mehr als zehn Umfragen oder Umfragen durchgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="26b83-151">✔  Tab layout should be in an organized state if there are more than ten polls or surveys.</span></span>

### <a name="bots"></a><span data-ttu-id="26b83-152">Bots</span><span class="sxs-lookup"><span data-stu-id="26b83-152">Bots</span></span>

<span data-ttu-id="26b83-153">Informationen zur Botimplementierung finden Sie in der [Dokumentation zu Bots in Teams-Besprechungen.](../bots/how-to/create-a-bot-for-teams.md#bots-in-teams-meetings)</span><span class="sxs-lookup"><span data-stu-id="26b83-153">For bot implementation, please see our [Bots in Teams meetings](../bots/how-to/create-a-bot-for-teams.md#bots-in-teams-meetings) documentation.</span></span>

### <a name="messaging-extensions"></a><span data-ttu-id="26b83-154">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="26b83-154">Messaging Extensions</span></span>

<span data-ttu-id="26b83-155">Informationen zur Implementierung von Messagingerweiterungen finden Sie in der Dokumentation zu [Messagingerweiterungen in Teams-Besprechungen.](../messaging-extensions/how-to/create-messaging-extension.md#messaging-extensions-in-teams-meetings)</span><span class="sxs-lookup"><span data-stu-id="26b83-155">For messaging extension implementation, please see our [Messaging extensions in Teams meetings](../messaging-extensions/how-to/create-messaging-extension.md#messaging-extensions-in-teams-meetings) documentation.</span></span>

## <a name="participant-roles-and-user-types-in-a-meeting"></a><span data-ttu-id="26b83-156">Teilnehmerrollen und Benutzertypen in einer Besprechung</span><span class="sxs-lookup"><span data-stu-id="26b83-156">Participant roles and user types in a meeting</span></span>

![Teilnehmer an einer Besprechung](../assets/images/apps-in-meetings/participant-roles.png)

### <a name="participant-roles"></a><span data-ttu-id="26b83-158">Teilnehmerrollen</span><span class="sxs-lookup"><span data-stu-id="26b83-158">Participant roles</span></span>

<span data-ttu-id="26b83-159">Sie können Ihre App mit teilnehmerspezifischer Autorisierung entwerfen.</span><span class="sxs-lookup"><span data-stu-id="26b83-159">You can design your app with participant-specific authorization.</span></span> <span data-ttu-id="26b83-160">Beispielsweise kann nur ein Organisator und/oder Organisator eine Umfrage in Besprechungen erstellen.</span><span class="sxs-lookup"><span data-stu-id="26b83-160">For example, perhaps only an organizer and/or presenter can create a poll in meetings.</span></span> <span data-ttu-id="26b83-161">Obwohl die Standardeinstellungen für Teilnehmer vom IT-Administrator einer Organisation bestimmt werden, kann ein Besprechungsorganisator die Einstellungen für eine bestimmte Besprechung ändern.</span><span class="sxs-lookup"><span data-stu-id="26b83-161">Although default participant settings are determined by an organization's IT administrator, a meeting organizer may want to change the settings for a specific meeting.</span></span> <span data-ttu-id="26b83-162">Organisatoren können diese Änderungen auf der Webseite für Besprechungsoptionen vornehmen.</span><span class="sxs-lookup"><span data-stu-id="26b83-162">Organizers can make these changes on the Meeting options web page.</span></span>

1. <span data-ttu-id="26b83-163">**Organizer**.</span><span class="sxs-lookup"><span data-stu-id="26b83-163">**Organizer**.</span></span> <span data-ttu-id="26b83-164">Der Organisator plant eine Besprechung, legt die Besprechungsoptionen fest, weist Besprechungsrollen zu und startet die Besprechung.</span><span class="sxs-lookup"><span data-stu-id="26b83-164">The organizer schedules a meeting, sets the meeting options, assigns meeting roles, and starts the meeting.</span></span> <span data-ttu-id="26b83-165">Nur Benutzer mit einem M365-Konto (besitzen eine Teams-Lizenz) können Organisatoren sein und die Teilnehmerberechtigungen steuern.</span><span class="sxs-lookup"><span data-stu-id="26b83-165">Only users with a M365 account (possessing a Teams license) can be organizers and control attendee permissions.</span></span>
1. <span data-ttu-id="26b83-166">**Presenter**.</span><span class="sxs-lookup"><span data-stu-id="26b83-166">**Presenter**.</span></span> <span data-ttu-id="26b83-167">Organisatoren verfügen nahezu über die gleichen Funktionen wie Organisator. Ein Organisator kann jedoch keinen Organisator aus der Sitzung entfernen oder Besprechungsoptionen für die Sitzung ändern.</span><span class="sxs-lookup"><span data-stu-id="26b83-167">Presenters have nearly the same capabilities as organizer; however, a presenter cannot remove an organizer from the session or modify meeting options for the session.</span></span> <span data-ttu-id="26b83-168">Standardmäßig haben Teilnehmer, die einer Besprechung beitreten, die Rolle des Moderators.</span><span class="sxs-lookup"><span data-stu-id="26b83-168">By default, participants joining a meeting have the presenter role.</span></span>
1. <span data-ttu-id="26b83-169">**Teilnehmer**.</span><span class="sxs-lookup"><span data-stu-id="26b83-169">**Attendee**.</span></span> <span data-ttu-id="26b83-170">Ein Teilnehmer ist ein Benutzer, der zur Teilnahme an einer Besprechung eingeladen wurde, aber nicht berechtigt ist, als Moderator zu fungieren.</span><span class="sxs-lookup"><span data-stu-id="26b83-170">An attendee is a user who has been invited to attend a meeting but who is not authorized to act as a presenter.</span></span> <span data-ttu-id="26b83-171">Teilnehmer können mit anderen Besprechungsmitgliedern interagieren, aber keine Besprechungseinstellungen verwalten oder Inhalte freigeben.</span><span class="sxs-lookup"><span data-stu-id="26b83-171">Attendees can interact with other meeting members but cannot manage any of the meeting settings or share content.</span></span>

<span data-ttu-id="26b83-172">_Siehe_ [ **"Rollen in einer Teams-Besprechung"**](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019)</span><span class="sxs-lookup"><span data-stu-id="26b83-172">_See_ [**Roles in a Teams meeting**](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019)</span></span>

<span data-ttu-id="26b83-173">Sie können wie folgt auf die Seite  **"Besprechungsoptionen"** zugreifen:</span><span class="sxs-lookup"><span data-stu-id="26b83-173">You can access the  **Meeting options** page as follows:</span></span>

<span data-ttu-id="26b83-174">&#11200; In Teams wechseln Sie zum **Kalenderlogo** des Kalenders, wählen Sie eine Besprechung ![ und dann ](../assets/images/apps-in-meetings/calendar-logo.png) **Besprechungsoptionen aus.**</span><span class="sxs-lookup"><span data-stu-id="26b83-174">&#11200; In Teams, go to **Calendar** ![calendar logo](../assets/images/apps-in-meetings/calendar-logo.png), select a meeting, and then **Meeting options**.</span></span>

<span data-ttu-id="26b83-175">&#11200; Wählen Sie in einer Besprechungseinladung **Besprechungsoptionen aus.**</span><span class="sxs-lookup"><span data-stu-id="26b83-175">&#11200; In a meeting invitation, select **Meeting options**.</span></span>

<span data-ttu-id="26b83-176">&#11200; Wählen Sie während einer Besprechung das Symbol **"Teilnehmer** ![ anzeigen" in den ](../assets/images/apps-in-meetings/show-participants.png) Besprechungssteuerelementen aus.</span><span class="sxs-lookup"><span data-stu-id="26b83-176">&#11200; During a meeting, select **Show participants** ![show participants icon](../assets/images/apps-in-meetings/show-participants.png) in the meeting controls.</span></span> <span data-ttu-id="26b83-177">Wählen Sie dann über der Liste der Teilnehmer die Option **"Berechtigungen verwalten" aus.**</span><span class="sxs-lookup"><span data-stu-id="26b83-177">Then, above the list of participants, choose **Manage permissions**.</span></span>

### <a name="user-types"></a><span data-ttu-id="26b83-178">Benutzertypen</span><span class="sxs-lookup"><span data-stu-id="26b83-178">User types</span></span>

> [!NOTE]
> <span data-ttu-id="26b83-179">Benutzertypen können an Besprechungen teilnehmen und eine der oben beschriebenen Teilnehmerrollen übernehmen.</span><span class="sxs-lookup"><span data-stu-id="26b83-179">User types can join meetings and assume one of the participant roles described above.</span></span> <span data-ttu-id="26b83-180">Der Benutzertyp wird nicht als Teil der **getParticipantRole-API verfügbar** gemacht.</span><span class="sxs-lookup"><span data-stu-id="26b83-180">The User type is not exposed as part of the **getParticipantRole** API.</span></span>

1. <span data-ttu-id="26b83-181">**Mandanteninte mandant**.</span><span class="sxs-lookup"><span data-stu-id="26b83-181">**In-tenant**.</span></span> <span data-ttu-id="26b83-182">Diese Benutzer gehören zur Organisation und verfügen über Anmeldeinformationen in Azure Active Directory für den Mandanten.</span><span class="sxs-lookup"><span data-stu-id="26b83-182">These users belong to the organization and have credentials in Azure Active Directory for the tenant.</span></span> <span data-ttu-id="26b83-183">Sie sind in der Regel Vollzeit-, Standort- oder Remotemitarbeiter.</span><span class="sxs-lookup"><span data-stu-id="26b83-183">They are usually full-time, onsite or remote employees.</span></span>
1. <span data-ttu-id="26b83-184">**Gast**.</span><span class="sxs-lookup"><span data-stu-id="26b83-184">**Guest**.</span></span> <span data-ttu-id="26b83-185">Ein Gast ist ein Teilnehmer aus einer anderen Organisation, der eingeladen wurde, auf Teams oder andere Ressourcen im Mandanten Ihrer Organisation zu zugreifen.</span><span class="sxs-lookup"><span data-stu-id="26b83-185">A guest is a participant from another organization who has been invited to access Teams or other resources in your organization's tenant.</span></span> <span data-ttu-id="26b83-186">Gäste werden dem Active Directory Ihrer Organisation hinzugefügt und können nahezu dieselben Funktionen wie ein systemeigenes Teammitglied mit Vollzugriff auf Teamchats, Besprechungen und Dateien erhalten.</span><span class="sxs-lookup"><span data-stu-id="26b83-186">Guests are added to your organization’s Active Directory and can be given nearly all the same Teams capabilities as a native team member with full access to team chats, meetings, and files.</span></span> <span data-ttu-id="26b83-187">_Siehe Gastzugriff_ [in Microsoft Teams](/microsoftteams/guest-access)</span><span class="sxs-lookup"><span data-stu-id="26b83-187">_See_ [Guest access in Microsoft Teams](/microsoftteams/guest-access)</span></span>
1. <span data-ttu-id="26b83-188">**Partner/Extern**.</span><span class="sxs-lookup"><span data-stu-id="26b83-188">**Federated/External**.</span></span> <span data-ttu-id="26b83-189">Ein Verbundbenutzer ist ein externer Teams-Benutzer in einer anderen Organisation, der zur Teilnahme an einer Besprechung eingeladen wurde.</span><span class="sxs-lookup"><span data-stu-id="26b83-189">A federated user is an external Teams user in another organization who has been invited to join a meeting.</span></span> <span data-ttu-id="26b83-190">Da diese Benutzer über gültige Anmeldeinformationen bei Verbundpartnern verfügen, werden sie als von Teams authentifiziert behandelt, haben jedoch keinen Zugriff auf Ihre Teams oder andere freigegebene Ressourcen aus Ihrer Organisation.</span><span class="sxs-lookup"><span data-stu-id="26b83-190">Since these users have valid credentials with federated partners, they are treated as authenticated by Teams but do not have access to your teams or other shared resources from your organization.</span></span> <span data-ttu-id="26b83-191">Wenn Externe Benutzer Zugriff auf Teams und Kanäle haben sollen, ist der Gastzugriff möglicherweise die bessere Option.</span><span class="sxs-lookup"><span data-stu-id="26b83-191">If you want external users to have access to teams and channels, guest access might be a better option.</span></span> <span data-ttu-id="26b83-192">_Siehe "Verwalten_ [des externen Zugriffs in Microsoft Teams"](/microsoftteams/manage-external-access)</span><span class="sxs-lookup"><span data-stu-id="26b83-192">_See_ [Manage external access in Microsoft Teams](/microsoftteams/manage-external-access)</span></span>
1. <span data-ttu-id="26b83-193">**Anonym**.</span><span class="sxs-lookup"><span data-stu-id="26b83-193">**Anonymous**.</span></span> <span data-ttu-id="26b83-194">Anonyme Benutzer verfügen nicht über eine Active Directory-Identität und sind nicht mit einem Mandanten im Verbund.</span><span class="sxs-lookup"><span data-stu-id="26b83-194">Anonymous users do not have an Active Directory identity and are not federated with a tenant.</span></span> <span data-ttu-id="26b83-195">Der anonyme Teilnehmer ist wie ein externer Benutzer, aber seine Identität wird nicht in die Besprechung projiziert.</span><span class="sxs-lookup"><span data-stu-id="26b83-195">The anonymous participant is like an external user, but their identity is not projected into the meeting.</span></span> <span data-ttu-id="26b83-196">Anonyme Benutzer können in einem Besprechungsfenster nicht auf Apps zugreifen.</span><span class="sxs-lookup"><span data-stu-id="26b83-196">Anonymous users will not be able to access apps in a meeting window.</span></span>

## <a name="next-steps"></a><span data-ttu-id="26b83-197">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="26b83-197">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="26b83-198">Entwerfen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="26b83-198">Design your app</span></span>](create-apps-for-teams-meetings.md)
> [!div class="nextstepaction"]
> [<span data-ttu-id="26b83-199">Erstellen Sie Ihre Anwendung</span><span class="sxs-lookup"><span data-stu-id="26b83-199">Build your app</span></span>](create-apps-for-teams-meetings.md)
