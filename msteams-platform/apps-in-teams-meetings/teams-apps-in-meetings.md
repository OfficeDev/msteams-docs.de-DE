---
title: Apps in Microsoft Teams-Besprechungen
author: laujan
description: Übersicht über apps in Microsoft Teams-Besprechungen basierend auf der Rolle des Teilnehmers und Benutzers
ms.topic: overview
ms.author: lajanuar
keywords: Teams-apps-Besprechungen Benutzer Teilnehmer-Rollen-API
ms.openlocfilehash: db14049d3150eaaa9634b4fa535a989528b1c6a2
ms.sourcegitcommit: e70d41ae793a407fdbb71bc79ef7b67b40386c96
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2020
ms.locfileid: "49358021"
---
# <a name="apps-in-teams-meetings"></a><span data-ttu-id="046bb-104">Apps in Microsoft Teams-Besprechungen</span><span class="sxs-lookup"><span data-stu-id="046bb-104">Apps in Teams meetings</span></span>

<span data-ttu-id="046bb-105">Besprechungen sind der Schlüssel zur Produktivität in Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="046bb-105">Meetings are key to productivity in Teams.</span></span> <span data-ttu-id="046bb-106">Sie ermöglichen Zusammenarbeit, Partnerschaft, informierte Kommunikation und gemeinsames Feedback in einem integrativen und aktiven Forum.</span><span class="sxs-lookup"><span data-stu-id="046bb-106">They enable collaboration, partnership, informed communication, and shared feedback in an inclusive and active forum.</span></span> <span data-ttu-id="046bb-107">Als Entwickler können Sie [konfigurierbare Registerkarten](../tabs/what-are-tabs.md#how-do-tabs-work)-, [bot](../bots/what-are-bots.md)-und [Nachrichten Erweiterungs](../messaging-extensions/what-are-messaging-extensions.md) Anwendungen erstellen, um die Besprechungs Erfahrung von Teams zu verbessern und zu bereichern.</span><span class="sxs-lookup"><span data-stu-id="046bb-107">As a developer, you can create [configurable tab](../tabs/what-are-tabs.md#how-do-tabs-work), [bot](../bots/what-are-bots.md), and [message extension](../messaging-extensions/what-are-messaging-extensions.md) applications to enhance and enrich a Teams meeting experience.</span></span> <span data-ttu-id="046bb-108">Besprechungs Benutzer können über den Tab-Katalog auf apps zugreifen, um relevante Szenarien wie das vorab Staging einer Kanban-Karte, das Starten eines in-Meeting-Aktions fähigen Dialogs oder das Erstellen einer Umfrage nach der Besprechung zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="046bb-108">Meeting users can access apps, via the tab gallery, to enable relevant scenarios such as pre-staging a Kanban board, launching an in-meeting actionable dialog, or creating a post-meeting poll.</span></span> <span data-ttu-id="046bb-109">Ihre Besprechungs-App kann eine Benutzeroberfläche für jede Phase des Besprechungs Lebenszyklus basierend auf dem Teilnehmerstatus bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="046bb-109">Your meeting app can deliver a user experience for each stage of the meeting lifecycle based upon attendee status.</span></span>

<span data-ttu-id="046bb-110">Die Erweiterungs Center für die Besprechungs-App für Teams werden auf drei Konzepte umstellen:</span><span class="sxs-lookup"><span data-stu-id="046bb-110">Teams’ meeting app extensibility centers on three concepts:</span></span>

<span data-ttu-id="046bb-111">✔ **Besprechungs Lebenszyklus** – vor, während und nach dem Besprechungszeit Rahmen.</span><span class="sxs-lookup"><span data-stu-id="046bb-111">✔ **Meeting lifecycle** — before, during, and after meeting time frame.</span></span>  
<span data-ttu-id="046bb-112">✔ **Teilnehmerrolle** : Besprechungsorganisator, Referent oder Teilnehmer.</span><span class="sxs-lookup"><span data-stu-id="046bb-112">✔ **Participant role** — meeting organizer, presenter, or attendee.</span></span>  
<span data-ttu-id="046bb-113">✔ **Benutzertyp** – Benutzer im Mandanten, im Gast, im Verbund oder im anonymen Team.</span><span class="sxs-lookup"><span data-stu-id="046bb-113">✔ **User type** — in-tenant, guest, federated, or anonymous Teams user.</span></span>

<!-- markdownlint-disable MD001 -->
### <a name="meeting-lifecycle-scenarios"></a><span data-ttu-id="046bb-114">Besprechungs Lebenszyklus-Szenarien</span><span class="sxs-lookup"><span data-stu-id="046bb-114">Meeting lifecycle scenarios</span></span>

## <a name="tabs"></a><span data-ttu-id="046bb-115">Registerkarten</span><span class="sxs-lookup"><span data-stu-id="046bb-115">Tabs</span></span>

> [!IMPORTANT]
> <span data-ttu-id="046bb-116">Wie bei allen Registerkarten Anwendungen muss Ihre APP dem [SSO-Authentifizierungs Fluss](../tabs/how-to/authentication/auth-aad-sso.md) für Teams für Registerkarten entsprechen.</span><span class="sxs-lookup"><span data-stu-id="046bb-116">As with all tab applications, Your app will need to follow the Teams [SSO authentication flow](../tabs/how-to/authentication/auth-aad-sso.md) for tabs.</span></span>

> [!NOTE]
> <span data-ttu-id="046bb-117">Mobile Clients unterstützen Registerkarten nur in Pre-und Post-Besprechungs Oberflächen.</span><span class="sxs-lookup"><span data-stu-id="046bb-117">Mobile clients support Tabs only in Pre and Post Meeting Surfaces.</span></span> <span data-ttu-id="046bb-118">Die in-Meeting-Erlebnisse (in-Meeting-Dialog und-Panel) auf mobilen Geräten werden in Kürze verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="046bb-118">The In-meeting experiences (in-meeting dialog and panel) on mobile will be available soon</span></span>

### <a name="pre-meeting-app-experience"></a><span data-ttu-id="046bb-119">App-Erfahrung vor der Besprechung</span><span class="sxs-lookup"><span data-stu-id="046bb-119">Pre-meeting app experience</span></span>

<span data-ttu-id="046bb-120">**Erfahrung vor der Besprechung:**</span><span class="sxs-lookup"><span data-stu-id="046bb-120">**Pre-meeting experience:**</span></span>

![Erfahrung vor der Besprechung](../assets/images/apps-in-meetings/PreMeeting.png)

<span data-ttu-id="046bb-122">**Registerkarte "Pre-Meeting":**</span><span class="sxs-lookup"><span data-stu-id="046bb-122">**Pre-meeting tab:**</span></span>

![Registerkartenansicht vor der Besprechung](../assets/images/apps-in-meetings/PreMeetingTab.png)

<span data-ttu-id="046bb-124">✔ Berechtigte Benutzer können über den Tab-Katalog auf zwei Arten apps zu einer Besprechung hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="046bb-124">✔ Permissioned users can add apps to a meeting via the tab gallery in two ways:</span></span>

<span data-ttu-id="046bb-125">&emsp;&emsp;&#9679; über die Registerkarte **Details** im Planungsformular für Teams.</span><span class="sxs-lookup"><span data-stu-id="046bb-125">&emsp;&emsp;&#9679; Via the **Details** tab on the Teams scheduling form.</span></span>

<span data-ttu-id="046bb-126">&emsp;&emsp;&#9679; über die Registerkarte Besprechungs **Chat** in einer vorhandenen Besprechung.</span><span class="sxs-lookup"><span data-stu-id="046bb-126">&emsp;&emsp;&#9679;  Via the meeting **Chat** tab in an existing meeting.</span></span></br> </br>

<span data-ttu-id="046bb-127">Auf ✔ Registerkarten-Apps können in Besprechungs **Details** und **Chats** -Seiten mithilfe einer Plus-Symbolschaltfläche (➕) zugegriffen werden. |</span><span class="sxs-lookup"><span data-stu-id="046bb-127">✔ Tab apps are accessible in meetings **Details** and **Chats** pages using a plus icon (➕) button.|</span></span>

<span data-ttu-id="046bb-128">✔ Registerkartenlayout sollte in einem organisierten Zustand sein, wenn es mehr als zehn Umfragen oder Umfragen gibt.</span><span class="sxs-lookup"><span data-stu-id="046bb-128">✔  Tab layout should be in an organized state if there are more than ten polls or surveys.</span></span>

### <a name="in-meeting-app-experience"></a><span data-ttu-id="046bb-129">In-Meeting-App-Erfahrung</span><span class="sxs-lookup"><span data-stu-id="046bb-129">In-meeting app experience</span></span>

<span data-ttu-id="046bb-130">✔ Besprechungs-apps werden in der oberen oberen Leiste des Chatfensters und als in-Meeting-Registerkarten Darstellung über die Registerkarte "in-Meeting" gehostet. Wenn Benutzer eine Registerkarte zu einer Besprechung über den Registerkarten Katalog hinzufügen, werden apps, die **während der Besprechungs** Erfahrung sind, angezeigt.</span><span class="sxs-lookup"><span data-stu-id="046bb-130">✔ Meeting apps will be hosted in the top upper bar of the chat window and as in-meeting tab experience via the in-meeting tab. When users add a tab to a meeting through the tab gallery, apps that are **during meeting** experiences will be surfaced.</span></span>

<span data-ttu-id="046bb-131">✔ Berechtigte Benutzer können während der Besprechung apps hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="046bb-131">✔ Permissioned users can add apps while in the meeting.</span></span>

<span data-ttu-id="046bb-132">✔, Wenn Sie im Kontext einer Besprechung geladen werden, können apps das Microsoft Teams-Client-SDK nutzen, um auf die `meetingId` `userMri` zu zugreifen und `frameContext` die Benutzeroberfläche entsprechend zu rendern.</span><span class="sxs-lookup"><span data-stu-id="046bb-132">✔ When loaded in the context of a meeting, apps will be able to leverage the Teams Client SDK to access the `meetingId`, `userMri`, and `frameContext` to appropriately render the experience.</span></span>

<span data-ttu-id="046bb-133">✔ Das Exportieren eines Ergebnisses einer Umfrage oder Umfragen sollte den Benutzern mitteilen, dass die Ergebnisse erfolgreich heruntergeladen wurden.</span><span class="sxs-lookup"><span data-stu-id="046bb-133">✔ Exporting a result of a survey or polls should notify the users stating, ‘results successfully downloaded’.</span></span>

<span data-ttu-id="046bb-134">✔, Dass eine app in einer Teams-Besprechung in zwei Bereichen angezeigt wird:</span><span class="sxs-lookup"><span data-stu-id="046bb-134">✔ For an app to be visible in a Teams meeting in two areas:</span></span>

<span data-ttu-id="046bb-135">&emsp;&emsp;&#9679; **Seitenbereich**.</span><span class="sxs-lookup"><span data-stu-id="046bb-135">&emsp;&emsp;&#9679; **Side panel**.</span></span> </br>

> [!NOTE]
> <span data-ttu-id="046bb-136">Wenn Ihr _App-Manifest_ angibt, dass Ihre Registerkarte [für den Seitenbereich optimiert](create-apps-for-teams-meetings.md#in-meeting)ist, wird Sie angezeigt.</span><span class="sxs-lookup"><span data-stu-id="046bb-136">If your _app manifest_ specifies that your tab is [optimized for side panel](create-apps-for-teams-meetings.md#in-meeting), that is where it will be displayed.</span></span> <span data-ttu-id="046bb-137">Es kann auch Teil einer Erfahrung mit Freigabe Schacht sein, die bestimmten Entwurfsrichtlinien unterliegt.</span><span class="sxs-lookup"><span data-stu-id="046bb-137">It can also be part of a share-tray experience, subject to specified design guidelines.</span></span>

<span data-ttu-id="046bb-138">&emsp;&emsp;&#9679; **in-Meeting-Dialog**.</span><span class="sxs-lookup"><span data-stu-id="046bb-138">&emsp;&emsp;&#9679; **In-meeting dialog**.</span></span> <span data-ttu-id="046bb-139">Verwenden Sie das in-Meeting-Dialogfeld, um Aktions Inhalte für Besprechungsteilnehmer zu präsentieren.</span><span class="sxs-lookup"><span data-stu-id="046bb-139">Use the in-meeting dialog to showcase actionable content for meeting participants.</span></span> <span data-ttu-id="046bb-140">*Siehe* [Erstellen von Apps für Microsoft Teams-Besprechungen](create-apps-for-teams-meetings.md).</span><span class="sxs-lookup"><span data-stu-id="046bb-140">*See* [Create Apps for Teams meetings](create-apps-for-teams-meetings.md).</span></span>

<span data-ttu-id="046bb-141">**Besprechungs Erfahrung:**</span><span class="sxs-lookup"><span data-stu-id="046bb-141">**In-meeting experience:**</span></span>

![Besprechungs Erfahrung](../assets/images/apps-in-meetings/in-meeting-experience.png)

![In-Meeting-Dialog Ansicht](../assets/images/apps-in-meetings/in-meeting-dialog.png)

<span data-ttu-id="046bb-144">**In-Meeting-Aktion-Dialogfeld für Benutzer:**</span><span class="sxs-lookup"><span data-stu-id="046bb-144">**In-meeting actionable dialog for users:**</span></span>

![Dialog Ansicht](../assets/images/apps-in-meetings/in-meeting-dialog-view.png)

### <a name="post-meeting-app-experience"></a><span data-ttu-id="046bb-146">App-Erfahrung nach der Besprechung</span><span class="sxs-lookup"><span data-stu-id="046bb-146">Post-meeting app experience</span></span>

<span data-ttu-id="046bb-147">**Erfahrung nach der Besprechung:**</span><span class="sxs-lookup"><span data-stu-id="046bb-147">**Post-meeting experience:**</span></span>

![Post-Besprechungs Ansicht](../assets/images/apps-in-meetings/PostMeeting.png)

<span data-ttu-id="046bb-149">✔ Das Szenario für die Post-Meeting-App ähnelt der aktuellen Post-Meeting-Erfahrung mit dem zusätzlichen Vorteil, dass Registerkarten innerhalb der Oberfläche vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="046bb-149">✔ The post-meeting app scenario is similar to the current post-meeting experience with the added benefit of having tabs that exist within the surface.</span></span> 

<span data-ttu-id="046bb-150">✔ Benutzer mit Berechtigungen können Apps aus dem Registerkarten Katalog einer Besprechung über die Registerkarte **Details** im Planungsformular für Teams und die Registerkarte Besprechungs **Chat** in einer vorhandenen Besprechung hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="046bb-150">✔ Permissioned users can add apps from the tab gallery to a meeting via the **Details** tab on the Teams scheduling form and the meeting **Chat** tab in an existing meeting.</span></span>

<span data-ttu-id="046bb-151">✔ Registerkartenlayout sollte in einem organisierten Zustand sein, wenn es mehr als zehn Umfragen oder Umfragen gibt.</span><span class="sxs-lookup"><span data-stu-id="046bb-151">✔  Tab layout should be in an organized state if there are more than ten polls or surveys.</span></span>

### <a name="bots"></a><span data-ttu-id="046bb-152">Bots</span><span class="sxs-lookup"><span data-stu-id="046bb-152">Bots</span></span>

<span data-ttu-id="046bb-153">Informationen zur bot-Implementierung finden Sie in der Dokumentation zu den [Bots in Microsoft Teams-Besprechungen](../bots/how-to/create-a-bot-for-teams.md#bots-in-teams-meetings) .</span><span class="sxs-lookup"><span data-stu-id="046bb-153">For bot implementation, please see our [Bots in Teams meetings](../bots/how-to/create-a-bot-for-teams.md#bots-in-teams-meetings) documentation.</span></span>

### <a name="messaging-extensions"></a><span data-ttu-id="046bb-154">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="046bb-154">Messaging Extensions</span></span>

<span data-ttu-id="046bb-155">Informationen zur Implementierung von Messaging Erweiterungen finden Sie in der Dokumentation zu Microsoft [Teams-Besprechungen unter Messaging Extensions](../messaging-extensions/how-to/create-messaging-extension.md#messaging-extensions-in-teams-meetings) .</span><span class="sxs-lookup"><span data-stu-id="046bb-155">For messaging extension implementation, please see our [Messaging extensions in Teams meetings](../messaging-extensions/how-to/create-messaging-extension.md#messaging-extensions-in-teams-meetings) documentation.</span></span>

## <a name="participant-roles-and-user-types-in-a-meeting"></a><span data-ttu-id="046bb-156">Teilnehmerrollen und Benutzertypen in einer Besprechung</span><span class="sxs-lookup"><span data-stu-id="046bb-156">Participant roles and user types in a meeting</span></span>

![Teilnehmer an einer Besprechung](../assets/images/apps-in-meetings/participant-roles.png)

### <a name="participant-roles"></a><span data-ttu-id="046bb-158">Teilnehmerrollen</span><span class="sxs-lookup"><span data-stu-id="046bb-158">Participant roles</span></span>

<span data-ttu-id="046bb-159">Sie können Ihre APP mit Teilnehmer spezifischer Autorisierung entwerfen.</span><span class="sxs-lookup"><span data-stu-id="046bb-159">You can design your app with participant-specific authorization.</span></span> <span data-ttu-id="046bb-160">Beispielsweise kann nur ein Organisator und/oder Referent eine Umfrage in Besprechungen erstellen.</span><span class="sxs-lookup"><span data-stu-id="046bb-160">For example, perhaps only an organizer and/or presenter can create a poll in meetings.</span></span> <span data-ttu-id="046bb-161">Obwohl die Standardteilnehmer Einstellungen vom IT-Administrator einer Organisation festgelegt werden, kann es sein, dass ein Besprechungsorganisator die Einstellungen für eine bestimmte Besprechung ändern möchte.</span><span class="sxs-lookup"><span data-stu-id="046bb-161">Although default participant settings are determined by an organization's IT administrator, a meeting organizer may want to change the settings for a specific meeting.</span></span> <span data-ttu-id="046bb-162">Organisatoren können diese Änderungen auf der Webseite mit den Besprechungsoptionen vornehmen.</span><span class="sxs-lookup"><span data-stu-id="046bb-162">Organizers can make these changes on the Meeting options web page.</span></span>

1. <span data-ttu-id="046bb-163">**Organisator**.</span><span class="sxs-lookup"><span data-stu-id="046bb-163">**Organizer**.</span></span> <span data-ttu-id="046bb-164">Der Organisator plant eine Besprechung, legt die Besprechungsoptionen fest, ordnet besprechungsrollen zu und startet die Besprechung.</span><span class="sxs-lookup"><span data-stu-id="046bb-164">The organizer schedules a meeting, sets the meeting options, assigns meeting roles, and starts the meeting.</span></span> <span data-ttu-id="046bb-165">Nur Benutzer mit einem M365-Konto (besitzen eine Microsoft Teams-Lizenz) können Organisatoren sein und Berechtigungen für Teilnehmer steuern.</span><span class="sxs-lookup"><span data-stu-id="046bb-165">Only users with a M365 account (possessing a Teams license) can be organizers and control attendee permissions.</span></span>
1. <span data-ttu-id="046bb-166">**Referent**.</span><span class="sxs-lookup"><span data-stu-id="046bb-166">**Presenter**.</span></span> <span data-ttu-id="046bb-167">Referenten haben fast die gleichen Funktionen wie Organisatoren; ein Referent kann einen Organisator jedoch nicht aus der Sitzung entfernen oder Besprechungsoptionen für die Sitzung ändern.</span><span class="sxs-lookup"><span data-stu-id="046bb-167">Presenters have nearly the same capabilities as organizer; however, a presenter cannot remove an organizer from the session or modify meeting options for the session.</span></span> <span data-ttu-id="046bb-168">Standardmäßig haben Teilnehmer, die einer Besprechung beitreten, die Referenten Rolle.</span><span class="sxs-lookup"><span data-stu-id="046bb-168">By default, participants joining a meeting have the presenter role.</span></span>
1. <span data-ttu-id="046bb-169">**Teilnehmer**.</span><span class="sxs-lookup"><span data-stu-id="046bb-169">**Attendee**.</span></span> <span data-ttu-id="046bb-170">Ein Teilnehmer ist ein Benutzer, der zur Teilnahme an einer Besprechung eingeladen wurde, aber nicht berechtigt ist, als Referent zu fungieren.</span><span class="sxs-lookup"><span data-stu-id="046bb-170">An attendee is a user who has been invited to attend a meeting but who is not authorized to act as a presenter.</span></span> <span data-ttu-id="046bb-171">Teilnehmer können mit anderen Besprechungs Mitgliedern interagieren, jedoch keine Besprechungseinstellungen verwalten oder Inhalte freigeben.</span><span class="sxs-lookup"><span data-stu-id="046bb-171">Attendees can interact with other meeting members but cannot manage any of the meeting settings or share content.</span></span>

<span data-ttu-id="046bb-172">_Anzeigen_ [ **von Rollen in einer Microsoft Teams-Besprechung**](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019)</span><span class="sxs-lookup"><span data-stu-id="046bb-172">_See_ [**Roles in a Teams meeting**](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019)</span></span>

<span data-ttu-id="046bb-173">Sie können wie folgt auf die Seite  **Besprechungsoptionen** zugreifen:</span><span class="sxs-lookup"><span data-stu-id="046bb-173">You can access the  **Meeting options** page as follows:</span></span>

<span data-ttu-id="046bb-174">Wechseln Sie &#11200; in Microsoft Teams zu **Kalender** ![ Kalender Logo ](../assets/images/apps-in-meetings/calendar-logo.png) , wählen Sie eine Besprechung und dann **Besprechungsoptionen** aus.</span><span class="sxs-lookup"><span data-stu-id="046bb-174">&#11200; In Teams, go to **Calendar** ![calendar logo](../assets/images/apps-in-meetings/calendar-logo.png), select a meeting, and then **Meeting options**.</span></span>

<span data-ttu-id="046bb-175">Wählen Sie &#11200; in einer Besprechungseinladung die Option **Besprechungsoptionen** aus.</span><span class="sxs-lookup"><span data-stu-id="046bb-175">&#11200; In a meeting invitation, select **Meeting options**.</span></span>

<span data-ttu-id="046bb-176">&#11200; wählen Sie während einer Besprechung **Show participants** ![ ](../assets/images/apps-in-meetings/show-participants.png) in den Besprechungs Steuerelementen das Symbol Teilnehmer anzeigen aus.</span><span class="sxs-lookup"><span data-stu-id="046bb-176">&#11200; During a meeting, select **Show participants** ![show participants icon](../assets/images/apps-in-meetings/show-participants.png) in the meeting controls.</span></span> <span data-ttu-id="046bb-177">Wählen Sie dann oberhalb der Teilnehmerliste die Option **Berechtigungen verwalten** aus.</span><span class="sxs-lookup"><span data-stu-id="046bb-177">Then, above the list of participants, choose **Manage permissions**.</span></span>

### <a name="user-types"></a><span data-ttu-id="046bb-178">Benutzertypen</span><span class="sxs-lookup"><span data-stu-id="046bb-178">User types</span></span>

> [!NOTE]
> <span data-ttu-id="046bb-179">Benutzertypen können an Besprechungen teilnehmen und eine der oben beschriebenen Teilnehmerrollen annehmen.</span><span class="sxs-lookup"><span data-stu-id="046bb-179">User types can join meetings and assume one of the participant roles described above.</span></span> <span data-ttu-id="046bb-180">Der Benutzertyp wird nicht als Teil der **getParticipantRole** -API verfügbar gemacht.</span><span class="sxs-lookup"><span data-stu-id="046bb-180">The User type is not exposed as part of the **getParticipantRole** API.</span></span>

1. <span data-ttu-id="046bb-181">**Im Mandanten**.</span><span class="sxs-lookup"><span data-stu-id="046bb-181">**In-tenant**.</span></span> <span data-ttu-id="046bb-182">Diese Benutzer gehören zur Organisation und verfügen über Anmeldeinformationen in Azure Active Directory für den Mandanten.</span><span class="sxs-lookup"><span data-stu-id="046bb-182">These users belong to the organization and have credentials in Azure Active Directory for the tenant.</span></span> <span data-ttu-id="046bb-183">Dabei handelt es sich normalerweise um Vollzeitmitarbeiter, vor-Ort-oder Remotemitarbeiter.</span><span class="sxs-lookup"><span data-stu-id="046bb-183">They are usually full-time, onsite or remote employees.</span></span>
1. <span data-ttu-id="046bb-184">**Gast**.</span><span class="sxs-lookup"><span data-stu-id="046bb-184">**Guest**.</span></span> <span data-ttu-id="046bb-185">Ein Gast ist ein Teilnehmer einer anderen Organisation, der eingeladen wurde, auf Teams oder andere Ressourcen im Mandanten Ihrer Organisation zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="046bb-185">A guest is a participant from another organization who has been invited to access Teams or other resources in your organization's tenant.</span></span> <span data-ttu-id="046bb-186">Gäste werden dem Active Directory Ihrer Organisation hinzugefügt und können nahezu alle Teams-Funktionen wie ein systemeigenes Teammitglied mit Vollzugriff auf Team Chats, Besprechungen und Dateien erhalten.</span><span class="sxs-lookup"><span data-stu-id="046bb-186">Guests are added to your organization’s Active Directory and can be given nearly all the same Teams capabilities as a native team member with full access to team chats, meetings, and files.</span></span> <span data-ttu-id="046bb-187">_Siehe_ [Gastzugriff in Microsoft Teams](/microsoftteams/guest-access)</span><span class="sxs-lookup"><span data-stu-id="046bb-187">_See_ [Guest access in Microsoft Teams](/microsoftteams/guest-access)</span></span>
1. <span data-ttu-id="046bb-188">**Verbund/extern**.</span><span class="sxs-lookup"><span data-stu-id="046bb-188">**Federated/External**.</span></span> <span data-ttu-id="046bb-189">Ein Verbundbenutzer ist ein externer Teams-Benutzer in einer anderen Organisation, der zur Teilnahme an einer Besprechung eingeladen wurde.</span><span class="sxs-lookup"><span data-stu-id="046bb-189">A federated user is an external Teams user in another organization who has been invited to join a meeting.</span></span> <span data-ttu-id="046bb-190">Da diese Benutzer gültige Anmeldeinformationen für Verbundpartner haben, werden Sie von Microsoft Teams authentifiziert, haben aber keinen Zugriff auf Ihre Teams oder andere freigegebene Ressourcen von Ihrer Organisation.</span><span class="sxs-lookup"><span data-stu-id="046bb-190">Since these users have valid credentials with federated partners, they are treated as authenticated by Teams but do not have access to your teams or other shared resources from your organization.</span></span> <span data-ttu-id="046bb-191">Wenn Sie möchten, dass externe Benutzer Zugriff auf Teams und Kanäle haben, ist der Gastzugriff möglicherweise eine bessere Option.</span><span class="sxs-lookup"><span data-stu-id="046bb-191">If you want external users to have access to teams and channels, guest access might be a better option.</span></span> <span data-ttu-id="046bb-192">_Siehe_ [Verwalten von externem Zugriff in Microsoft Teams](/microsoftteams/manage-external-access)</span><span class="sxs-lookup"><span data-stu-id="046bb-192">_See_ [Manage external access in Microsoft Teams](/microsoftteams/manage-external-access)</span></span>
1. <span data-ttu-id="046bb-193">**Anonym**.</span><span class="sxs-lookup"><span data-stu-id="046bb-193">**Anonymous**.</span></span> <span data-ttu-id="046bb-194">Anonyme Benutzer verfügen nicht über eine Active Directory Identität und sind nicht Verbund mit einem Mandanten.</span><span class="sxs-lookup"><span data-stu-id="046bb-194">Anonymous users do not have an Active Directory identity and are not federated with a tenant.</span></span> <span data-ttu-id="046bb-195">Der anonyme Teilnehmer ist wie ein externer Benutzer, aber seine Identität wird nicht in die Besprechung projiziert.</span><span class="sxs-lookup"><span data-stu-id="046bb-195">The anonymous participant is like an external user, but their identity is not projected into the meeting.</span></span> <span data-ttu-id="046bb-196">Anonyme Benutzer können nicht auf apps in einem Besprechungsfenster zugreifen.</span><span class="sxs-lookup"><span data-stu-id="046bb-196">Anonymous users will not be able to access apps in a meeting window.</span></span>

## <a name="next-steps"></a><span data-ttu-id="046bb-197">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="046bb-197">Next Steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="046bb-198">Apps für Teams-Besprechungen erstellen</span><span class="sxs-lookup"><span data-stu-id="046bb-198">Create apps for Teams meetings</span></span>](create-apps-for-teams-meetings.md)
