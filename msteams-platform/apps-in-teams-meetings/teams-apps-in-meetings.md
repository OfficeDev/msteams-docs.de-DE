---
title: Apps in Teams-Besprechungen
author: laujan
description: Übersicht über Apps in Teams-Besprechungen basierend auf Teilnehmer- und Benutzerrolle
ms.topic: overview
ms.author: lajanuar
keywords: Rollen-API für Teams-Apps-Besprechungen für Benutzerteilnehmer
ms.openlocfilehash: ac4e270090dd89d370d37de88b8cba552b77a5cb
ms.sourcegitcommit: 3727fc58e84b6f1752612884c2e0b25e207fb56e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/26/2021
ms.locfileid: "51382338"
---
# <a name="apps-in-teams-meetings"></a><span data-ttu-id="fd67d-104">Apps in Teams-Besprechungen</span><span class="sxs-lookup"><span data-stu-id="fd67d-104">Apps in Teams meetings</span></span>

<span data-ttu-id="fd67d-105">Besprechungen ermöglichen Zusammenarbeit, Partnerschaft, informierte Kommunikation und geteiltes Feedback in einem inklusiven und aktiven Forum.</span><span class="sxs-lookup"><span data-stu-id="fd67d-105">Meetings enable collaboration, partnership, informed communication, and shared feedback in an inclusive and active forum.</span></span> <span data-ttu-id="fd67d-106">Die Besprechungs-App kann je nach Status des Teilnehmers eine Benutzeroberfläche für jede Phase des Besprechungslebenszyklus bereitstellen, einschließlich der Vorbetreff-, Besprechungs- und Post-Meeting-App-Erfahrung.</span><span class="sxs-lookup"><span data-stu-id="fd67d-106">The meeting app can deliver a user experience for each stage of the meeting lifecycle including pre-meeting, in-meeting and post-meeting app experience, depending on the attendee's status.</span></span>

<span data-ttu-id="fd67d-107">Teams-Endbenutzer können während Besprechungen über den Registerkartenkatalog auf Apps zugreifen, z. B.:</span><span class="sxs-lookup"><span data-stu-id="fd67d-107">Teams end-users can access apps during meetings using the tab gallery, for example:</span></span>

* <span data-ttu-id="fd67d-108">Vorabphase eines Kanban-Board</span><span class="sxs-lookup"><span data-stu-id="fd67d-108">Pre-stage a Kanban board</span></span>
* <span data-ttu-id="fd67d-109">Starten eines Dialogfelds mit Aktionen in Besprechungen</span><span class="sxs-lookup"><span data-stu-id="fd67d-109">Launch an in-meeting actionable dialog</span></span>
* <span data-ttu-id="fd67d-110">Erstellen einer Umfrage nach der Besprechung</span><span class="sxs-lookup"><span data-stu-id="fd67d-110">Create a post-meeting poll</span></span>

<span data-ttu-id="fd67d-111">Die Erweiterbarkeit der Besprechungs-App von Teams basiert auf den folgenden Konzepten:</span><span class="sxs-lookup"><span data-stu-id="fd67d-111">Teams’ meeting app extensibility is based on the following concepts:</span></span>

<span data-ttu-id="fd67d-112">✔ besprechungslebenszyklus hat Phasen wie vor, während und nach besprechung Zeitrahmen.</span><span class="sxs-lookup"><span data-stu-id="fd67d-112">✔ Meeting lifecycle has stages such as before, during, and after meeting time frame.</span></span>  
<span data-ttu-id="fd67d-113">✔ teilnehmerrollen in einer Besprechung, z. B. Besprechungsorganisator, Organisator oder Teilnehmer.</span><span class="sxs-lookup"><span data-stu-id="fd67d-113">✔ Participant roles in a meeting such as meeting organizer, presenter, or attendee.</span></span>  
<span data-ttu-id="fd67d-114">✔ Benutzertypen in einer Besprechung, z. B. mandanten-, gast-, verbund- oder anonymer Teams-Benutzer.</span><span class="sxs-lookup"><span data-stu-id="fd67d-114">✔ User types in a meeting such as in-tenant, guest, federated, or anonymous Teams user.</span></span>

<span data-ttu-id="fd67d-115">Dieser Artikel behandelt Informationen zum Besprechungslebenszyklus und zur Integration von Registerkarten, Bots und Messagingerweiterungen in Ihre Besprechung.</span><span class="sxs-lookup"><span data-stu-id="fd67d-115">This article covers information about the meeting lifecycle and how to integrate tabs, bots, and messaging extensions in your meeting.</span></span> <span data-ttu-id="fd67d-116">Außerdem können Sie Teilnehmerrollen identifizieren und auch verschiedene Benutzertypen verwenden, um Aufgaben auszuführen.</span><span class="sxs-lookup"><span data-stu-id="fd67d-116">It also enables you to identify participant roles and also use different user types to perform tasks.</span></span>

> [!NOTE]
> <span data-ttu-id="fd67d-117">Zum Arbeiten mit den Erweiterungsfeatures der Besprechungs-App müssen Sie über die entsprechenden Berechtigungen verfügen.</span><span class="sxs-lookup"><span data-stu-id="fd67d-117">To work with the meeting app extensibility features, you must have the appropriate permissions.</span></span>

### <a name="meeting-lifecycle"></a><span data-ttu-id="fd67d-118">Besprechungslebenszyklus</span><span class="sxs-lookup"><span data-stu-id="fd67d-118">Meeting lifecycle</span></span>

<span data-ttu-id="fd67d-119">Der Besprechungslebenszyklus besteht aus app-Erfahrung vor der Besprechung, in der Besprechung und nach der Besprechung.</span><span class="sxs-lookup"><span data-stu-id="fd67d-119">Meeting lifecycle consists of pre-meeting, in-meeting, and post-meeting app experience.</span></span> <span data-ttu-id="fd67d-120">Sie können Registerkarten, Bots und Messagingerweiterungen in jeder Phase des Besprechungslebenszyklus integrieren.</span><span class="sxs-lookup"><span data-stu-id="fd67d-120">You can integrate tabs, bots, and messaging extensions in each stage of the meeting lifecycle.</span></span>

## <a name="integrate-tabs-into-the-meeting-lifecycle"></a><span data-ttu-id="fd67d-121">Integrieren von Registerkarten in den Besprechungslebenszyklus</span><span class="sxs-lookup"><span data-stu-id="fd67d-121">Integrate tabs into the meeting lifecycle</span></span>

<span data-ttu-id="fd67d-122">Registerkarten ermöglichen Teammitgliedern den Zugriff auf Dienste und Inhalte in einem bestimmten Bereich innerhalb eines Kanals oder Chats.</span><span class="sxs-lookup"><span data-stu-id="fd67d-122">Tabs allow team members to access services and content in a specific space within a channel or chat.</span></span> <span data-ttu-id="fd67d-123">Auf diese Weise kann das Team direkt mit Registerkarten arbeiten und Unterhaltungen über die Tools und Daten führen, die in Registerkarten verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="fd67d-123">This lets the team work directly with tabs and have conversations about the tools and data available within tabs.</span></span> <span data-ttu-id="fd67d-124">In Teams-Besprechungen können Benutzer eine Registerkarte hinzufügen, indem sie plus auswählen</span><span class="sxs-lookup"><span data-stu-id="fd67d-124">In Teams meeting, users can add a tab by selecting plus</span></span> <img src="~/assets/images/apps-in-meetings/plusbutton.png" alt="Plus button" width="30"/><span data-ttu-id="fd67d-125">und die App auswählen, die sie als Registerkarte installieren möchten.</span><span class="sxs-lookup"><span data-stu-id="fd67d-125">, and choosing the app that they want to install as a tab.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fd67d-126">Wenn Sie eine Registerkarte in Ihre Besprechung integriert haben, muss Ihre App dem Authentifizierungsfluss für einmaliges Anmelden [(SSO)](../tabs/how-to/authentication/auth-aad-sso.md) von Teams für Registerkarten folgen.</span><span class="sxs-lookup"><span data-stu-id="fd67d-126">If you have integrated a tab with your meeting, then your app must follow the Teams [single sign-on (SSO) authentication flow](../tabs/how-to/authentication/auth-aad-sso.md) for tabs.</span></span>

> [!NOTE]
> * <span data-ttu-id="fd67d-127">Mobile Clients unterstützen Registerkarten nur in Vor- und Nachbesprechungsphasen.</span><span class="sxs-lookup"><span data-stu-id="fd67d-127">Mobile clients support tabs only in pre and post meeting stages.</span></span> <span data-ttu-id="fd67d-128">Die Besprechungserfahrungen, die im Besprechungsdialogfeld und -panel vorhanden sind, sind derzeit nicht auf Mobilgeräten verfügbar.</span><span class="sxs-lookup"><span data-stu-id="fd67d-128">The in-meeting experiences that is in-meeting dialog and panel are currently not available on mobile.</span></span>
> * <span data-ttu-id="fd67d-129">Apps werden nur in privaten geplanten Besprechungen unterstützt.</span><span class="sxs-lookup"><span data-stu-id="fd67d-129">Apps are supported only in private scheduled meetings.</span></span>

### <a name="pre-meeting-app-experience"></a><span data-ttu-id="fd67d-130">App-Erfahrung vor besprechung</span><span class="sxs-lookup"><span data-stu-id="fd67d-130">Pre-meeting app experience</span></span>

<span data-ttu-id="fd67d-131">**Vorbetreff:**</span><span class="sxs-lookup"><span data-stu-id="fd67d-131">**Pre-meeting experience:**</span></span>

![Pre-Meeting-Erfahrung](../assets/images/apps-in-meetings/PreMeeting.png)

<span data-ttu-id="fd67d-133">**Registerkarte "Pre-Meeting":**</span><span class="sxs-lookup"><span data-stu-id="fd67d-133">**Pre-meeting tab:**</span></span>

![Registerkartenansicht vor der Besprechung](../assets/images/apps-in-meetings/PreMeetingTab.png)

<span data-ttu-id="fd67d-135">✔ benutzer sind Benutzer, die apps zu einer Besprechung in verschiedenen Phasen des Besprechungslebenszyklus hinzufügen können.</span><span class="sxs-lookup"><span data-stu-id="fd67d-135">✔ Permissioned users are users who can add apps to a meeting during different stages of the meeting lifecycle.</span></span> <span data-ttu-id="fd67d-136">Diese Benutzer können apps zu einer Besprechung über den Registerkartenkatalog auf zwei Arten hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="fd67d-136">These users can add apps to a meeting through the tab gallery in two ways:</span></span>

   * <span data-ttu-id="fd67d-137">Verwenden der **Registerkarte Details** im Formular teams scheduling.</span><span class="sxs-lookup"><span data-stu-id="fd67d-137">Using the **Details** tab on the Teams scheduling form.</span></span>

   * <span data-ttu-id="fd67d-138">Verwenden der Registerkarte **Besprechungschat** in einer vorhandenen Besprechung.</span><span class="sxs-lookup"><span data-stu-id="fd67d-138">Using the meeting **Chat** tab in an existing meeting.</span></span>

<span data-ttu-id="fd67d-139">✔ Tab-Apps sind in **Besprechungsdetails** und **Chats-Seiten** über eine Plus-➕ zugänglich.</span><span class="sxs-lookup"><span data-stu-id="fd67d-139">✔ Tab apps are accessible in meetings **Details** and **Chats** pages using a plus ➕ button.</span></span>

<span data-ttu-id="fd67d-140">✔ Registerkartenlayout muss sich in einem organisierten Zustand befinden, wenn mehr als zehn Umfragen oder Umfragen durchgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="fd67d-140">✔ Tab layout must be in an organized state if there are more than ten polls or surveys.</span></span>

### <a name="in-meeting-app-experience"></a><span data-ttu-id="fd67d-141">In-Meeting-App-Erfahrung</span><span class="sxs-lookup"><span data-stu-id="fd67d-141">In-meeting app experience</span></span>

<span data-ttu-id="fd67d-142">✔ Besprechungs-Apps werden in der oberen Leiste des Chatfensters und als Registerkartenerfahrung in Besprechungen mithilfe der Registerkarte "In-Meeting" gehostet. Wenn Benutzer einer Besprechung über den Registerkartenkatalog eine Registerkarte hinzufügen, werden Apps angezeigt, die sich während **der Besprechungserfahrung** befinden.</span><span class="sxs-lookup"><span data-stu-id="fd67d-142">✔ Meeting apps are hosted in the top upper bar of the chat window and as in-meeting tab experience using the in-meeting tab. When users add a tab to a meeting through the tab gallery, apps that are **during meeting** experiences are shown.</span></span>

<span data-ttu-id="fd67d-143">✔ Berechtigte Benutzer können Apps während der Besprechung hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="fd67d-143">✔ Permissioned users can add apps while in the meeting.</span></span>

<span data-ttu-id="fd67d-144">✔ Wenn apps im Kontext einer Besprechung geladen werden, können Sie das Teams Client SDK nutzen, um auf das zu zugreifen und die Erfahrung entsprechend `meetingId` `userMri` zu `frameContext` rendern.</span><span class="sxs-lookup"><span data-stu-id="fd67d-144">✔ When loaded in the context of a meeting, apps can leverage the Teams Client SDK to access the `meetingId`, `userMri`, and `frameContext` to appropriately render the experience.</span></span>

<span data-ttu-id="fd67d-145">✔ Exportieren eines Ergebnisses einer Umfrage oder Umfrage benachrichtigt die Benutzer, dass die Ergebnisse erfolgreich heruntergeladen wurden.</span><span class="sxs-lookup"><span data-stu-id="fd67d-145">✔ Exporting a result of a survey or poll notifies the users that the results successfully downloaded.</span></span>

<span data-ttu-id="fd67d-146">✔ Eine App wird in einer Teams-Besprechung im Seitenbereich oder im Dialogfeld in der Besprechung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="fd67d-146">✔ An app is visible in a Teams meeting in the side panel or the in-meeting dialog box.</span></span> <span data-ttu-id="fd67d-147">Verwenden Sie das Dialogfeld in der Besprechung, um Inhalte mit Aktionen für Besprechungsteilnehmer anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="fd67d-147">Use the in-meeting dialog to showcase actionable content for meeting participants.</span></span> <span data-ttu-id="fd67d-148">*Weitere Informationen* [finden Sie unter Erstellen von Apps für Teams-Besprechungen.](create-apps-for-teams-meetings.md)</span><span class="sxs-lookup"><span data-stu-id="fd67d-148">*See* [Create Apps for Teams meetings](create-apps-for-teams-meetings.md).</span></span>

   > [!NOTE]
   > <span data-ttu-id="fd67d-149">Ihr App-Manifest gibt an, dass Ihre Registerkarte [für den Seitenbereich](create-apps-for-teams-meetings.md#during-a-meeting)optimiert ist, d. h. an der Stelle, an der sie angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="fd67d-149">Your app manifest specifies that your tab is [optimized for side panel](create-apps-for-teams-meetings.md#during-a-meeting), that is where it is displayed.</span></span> <span data-ttu-id="fd67d-150">Sie kann auch Teil einer Share-Tray-Erfahrung sein, die den angegebenen Entwurfsrichtlinien unterliegt.</span><span class="sxs-lookup"><span data-stu-id="fd67d-150">It can also be part of a share-tray experience, subject to specified design guidelines.</span></span>

<span data-ttu-id="fd67d-151">In den folgenden Bildern wird die App als Besprechungsdialogfeld und als separater Seitenbereich angezeigt:</span><span class="sxs-lookup"><span data-stu-id="fd67d-151">The following images display the app as an in-meeting dialog box and as a separate side panel:</span></span>

![In-Meeting-Erfahrung](../assets/images/apps-in-meetings/in-meeting-experience.png)

![In-Meeting-Dialog-Ansicht](../assets/images/apps-in-meetings/in-meeting-dialog.png)

#### <a name="in-meeting-actionable-dialog-for-users"></a><span data-ttu-id="fd67d-154">In-Meeting-Dialogfeld mit Aktionen für Benutzer</span><span class="sxs-lookup"><span data-stu-id="fd67d-154">In-meeting actionable dialog for users</span></span>

![Dialogansicht](../assets/images/apps-in-meetings/in-meeting-dialog-view.png)

### <a name="post-meeting-app-experience"></a><span data-ttu-id="fd67d-156">App-Erfahrung nach der Besprechung</span><span class="sxs-lookup"><span data-stu-id="fd67d-156">Post-meeting app experience</span></span>

![Besprechungsansicht veröffentlichen](../assets/images/apps-in-meetings/PostMeeting.png)

<span data-ttu-id="fd67d-158">✔ Das App-Szenario nach der Besprechung ähnelt der aktuellen Nachbesprechung mit dem zusätzlichen Vorteil, dass Registerkarten auf der Oberfläche vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="fd67d-158">✔ The post-meeting app scenario is similar to the current post-meeting experience with the added benefit of having tabs that exist within the surface.</span></span>

<span data-ttu-id="fd67d-159">✔ Berechtigte Benutzer können Apps aus dem Registerkartenkatalog zu einer Besprechung mithilfe der  Registerkarte **Details** im Teams-Planungsformular und der Registerkarte Besprechungschat in einer vorhandenen Besprechung hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="fd67d-159">✔ Permissioned users can add apps from the tab gallery to a meeting using the **Details** tab on the Teams scheduling form and the meeting **Chat** tab in an existing meeting.</span></span>

<span data-ttu-id="fd67d-160">✔ Registerkartenlayout muss organisiert sein, wenn mehr als zehn Umfragen oder Umfragen durchgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="fd67d-160">✔  Tab layout must be organized when there are more than ten polls or surveys.</span></span>

### <a name="integrate-bots-into-the-meeting-lifecycle"></a><span data-ttu-id="fd67d-161">Integrieren von Bots in den Besprechungslebenszyklus</span><span class="sxs-lookup"><span data-stu-id="fd67d-161">Integrate bots into the meeting lifecycle</span></span>

<span data-ttu-id="fd67d-162">Beginnen Sie bei der Botimplementierung mit [dem Erstellen eines Bots,](../build-your-first-app/build-bot.md) und fahren Sie dann mit dem Erstellen von Apps [für Teams-Besprechungen fort.](../apps-in-teams-meetings/create-apps-for-teams-meetings.md#meeting-apps-api-reference)</span><span class="sxs-lookup"><span data-stu-id="fd67d-162">For bot implementation, start with [build a bot](../build-your-first-app/build-bot.md) and then continue with [create apps for Teams meetings](../apps-in-teams-meetings/create-apps-for-teams-meetings.md#meeting-apps-api-reference).</span></span>

### <a name="integrate-messaging-extensions-into-the-meeting-lifecycle"></a><span data-ttu-id="fd67d-163">Integrieren von Messagingerweiterungen in den Besprechungslebenszyklus</span><span class="sxs-lookup"><span data-stu-id="fd67d-163">Integrate messaging extensions into the meeting lifecycle</span></span>

<span data-ttu-id="fd67d-164">Beginnen Sie bei der Implementierung von Messagingerweiterungen mit dem Erstellen einer [Messagingerweiterung,](../messaging-extensions/how-to/create-messaging-extension.md) und fahren Sie dann mit dem Erstellen von [Apps für Teams-Besprechungen fort.](../apps-in-teams-meetings/create-apps-for-teams-meetings.md#meeting-apps-api-reference)</span><span class="sxs-lookup"><span data-stu-id="fd67d-164">For messaging extension implementation, start with [build a messaging extension](../messaging-extensions/how-to/create-messaging-extension.md) and then continue with [create apps for Teams meetings](../apps-in-teams-meetings/create-apps-for-teams-meetings.md#meeting-apps-api-reference).</span></span>

## <a name="participant-roles-and-user-types-in-a-meeting"></a><span data-ttu-id="fd67d-165">Teilnehmerrollen und Benutzertypen in einer Besprechung</span><span class="sxs-lookup"><span data-stu-id="fd67d-165">Participant roles and user types in a meeting</span></span>

![Teilnehmer an einer Besprechung](../assets/images/apps-in-meetings/participant-roles.png)

### <a name="participant-roles"></a><span data-ttu-id="fd67d-167">Teilnehmerrollen</span><span class="sxs-lookup"><span data-stu-id="fd67d-167">Participant roles</span></span>

<span data-ttu-id="fd67d-168">Die Standardeinstellungen für Teilnehmer werden vom IT-Administrator einer Organisation bestimmt.</span><span class="sxs-lookup"><span data-stu-id="fd67d-168">Default participant settings are determined by an organization's IT administrator.</span></span> <span data-ttu-id="fd67d-169">Es folgen die Teilnehmerrollen in einer Besprechung:</span><span class="sxs-lookup"><span data-stu-id="fd67d-169">The following are the participant roles in a meeting:</span></span>

* <span data-ttu-id="fd67d-170">**Organisator**: Der Organisator plant eine Besprechung, legt die Besprechungsoptionen fest, weist Besprechungsrollen zu und startet die Besprechung.</span><span class="sxs-lookup"><span data-stu-id="fd67d-170">**Organizer**: The organizer schedules a meeting, sets the meeting options, assigns meeting roles, and starts the meeting.</span></span> <span data-ttu-id="fd67d-171">Nur Benutzer mit einem M365-Konto mit einer Teams-Lizenz können Organisator sein und Die Teilnehmerberechtigungen steuern.</span><span class="sxs-lookup"><span data-stu-id="fd67d-171">Only users with a M365 account with a Teams license can be organizers and control attendee permissions.</span></span> <span data-ttu-id="fd67d-172">Ein Besprechungsorganisator kann die Einstellungen für eine bestimmte Besprechung ändern.</span><span class="sxs-lookup"><span data-stu-id="fd67d-172">A meeting organizer can change the settings for a specific meeting.</span></span> <span data-ttu-id="fd67d-173">Organisatoren können diese Änderungen auf der Webseite **"Besprechungsoptionen"** vornehmen.</span><span class="sxs-lookup"><span data-stu-id="fd67d-173">Organizers can make these changes on the **Meeting options** web page.</span></span>
* <span data-ttu-id="fd67d-174">**Organisator**: Organisator hat dieselben Funktionen wie Organisator.</span><span class="sxs-lookup"><span data-stu-id="fd67d-174">**Presenter**: Presenters have the same capabilities as organizer.</span></span> <span data-ttu-id="fd67d-175">Ein Organisator kann jedoch keinen Organisator aus der Sitzung entfernen oder Besprechungsoptionen für die Sitzung ändern.</span><span class="sxs-lookup"><span data-stu-id="fd67d-175">However, a presenter cannot remove an organizer from the session or modify meeting options for the session.</span></span> <span data-ttu-id="fd67d-176">Standardmäßig haben Teilnehmer, die an einer Besprechung teilnahmen, die Rolle des Moderators.</span><span class="sxs-lookup"><span data-stu-id="fd67d-176">By default, participants joining a meeting have the presenter role.</span></span>
* <span data-ttu-id="fd67d-177">**Teilnehmer**: Ein Teilnehmer ist ein Benutzer, der zur Teilnahme an einer Besprechung eingeladen wurde, der jedoch nicht autorisiert ist, als Moderator zu fungieren.</span><span class="sxs-lookup"><span data-stu-id="fd67d-177">**Attendee**: An attendee is a user who has been invited to attend a meeting but who is not authorized to act as a presenter.</span></span> <span data-ttu-id="fd67d-178">Teilnehmer können mit anderen Besprechungsmitgliedern interagieren, aber keine Besprechungseinstellungen verwalten oder Inhalte freigeben.</span><span class="sxs-lookup"><span data-stu-id="fd67d-178">Attendees can interact with other meeting members but cannot manage any of the meeting settings or share content.</span></span>

<span data-ttu-id="fd67d-179">Nur ein Organisator oder Organisator kann Apps hinzufügen, entfernen oder deinstallieren.</span><span class="sxs-lookup"><span data-stu-id="fd67d-179">Only an organizer or presenter can add, remove, or uninstall apps.</span></span> <span data-ttu-id="fd67d-180">Nur Organisator oder Organisator können Umfragen in einer Besprechung erstellen.</span><span class="sxs-lookup"><span data-stu-id="fd67d-180">Only organizer or presenter can create polls in a meeting.</span></span>

<span data-ttu-id="fd67d-181">Weitere Informationen finden Sie [unter Rollen in einer Teams-Besprechung](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).</span><span class="sxs-lookup"><span data-stu-id="fd67d-181">For more information, see [roles in a Teams meeting](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).</span></span>

<span data-ttu-id="fd67d-182">Sie können wie folgt auf  **die Seite Besprechungsoptionen** zugreifen:</span><span class="sxs-lookup"><span data-stu-id="fd67d-182">You can access the  **Meeting options** page as follows:</span></span>

* <span data-ttu-id="fd67d-183">Wechseln Sie in  Teams zu ![ Kalenderkalenderlogo, ](../assets/images/apps-in-meetings/calendar-logo.png) wählen Sie eine Besprechung und dann **Besprechungsoptionen aus.**</span><span class="sxs-lookup"><span data-stu-id="fd67d-183">In Teams, go to **Calendar** ![calendar logo](../assets/images/apps-in-meetings/calendar-logo.png), select a meeting, and then **Meeting options**.</span></span>

* <span data-ttu-id="fd67d-184">Wählen Sie in einer Besprechungseinladung **Besprechungsoptionen aus.**</span><span class="sxs-lookup"><span data-stu-id="fd67d-184">In a meeting invitation, select **Meeting options**.</span></span>

* <span data-ttu-id="fd67d-185">Wählen Sie während einer Besprechung das Symbol Teilnehmer **anzeigen** ![ in den ](../assets/images/apps-in-meetings/show-participants.png) Besprechungssteuerelementen anzeigen aus.</span><span class="sxs-lookup"><span data-stu-id="fd67d-185">During a meeting, select **Show participants** ![show participants icon](../assets/images/apps-in-meetings/show-participants.png) in the meeting controls.</span></span> <span data-ttu-id="fd67d-186">Wählen Sie dann oberhalb der Liste der Teilnehmer Berechtigungen **verwalten aus.**</span><span class="sxs-lookup"><span data-stu-id="fd67d-186">Then, above the list of participants, choose **Manage permissions**.</span></span>

### <a name="user-types"></a><span data-ttu-id="fd67d-187">Benutzertypen</span><span class="sxs-lookup"><span data-stu-id="fd67d-187">User types</span></span>

> [!NOTE]
> <span data-ttu-id="fd67d-188">Benutzer, denen bestimmte Benutzertypen zugewiesen sind, können an Besprechungen teilnehmen und eine der in den [Teilnehmerrollen beschriebenen Teilnehmerrollen übernehmen.](#participant-roles)</span><span class="sxs-lookup"><span data-stu-id="fd67d-188">Users with specific user types assigned to them can join meetings and assume one of the participant roles described in [participant roles](#participant-roles).</span></span> <span data-ttu-id="fd67d-189">Der Benutzertyp ist nicht in der **getParticipantRole-API** enthalten.</span><span class="sxs-lookup"><span data-stu-id="fd67d-189">The user type is not included in the **getParticipantRole** API.</span></span>

<span data-ttu-id="fd67d-190">Die folgenden Benutzertypen bestimmen, was jeder Benutzer tun kann und worauf er zugreifen kann:</span><span class="sxs-lookup"><span data-stu-id="fd67d-190">The following user types identify what each user can do and what they can access:</span></span>

* <span data-ttu-id="fd67d-191">**Mandantenin-mandant:** Mandantenbenutzer gehören der Organisation an und verfügen über Anmeldeinformationen in Azure Active Directory (AAD) für den Mandanten.</span><span class="sxs-lookup"><span data-stu-id="fd67d-191">**In-tenant**: In-tenant users belong to the organization and have credentials in Azure Active Directory (AAD) for the tenant.</span></span> <span data-ttu-id="fd67d-192">Es handelt sich in der Regel um Vollzeit-, Standort- oder Remotemitarbeiter.</span><span class="sxs-lookup"><span data-stu-id="fd67d-192">They are usually full-time, onsite, or remote employees.</span></span> <span data-ttu-id="fd67d-193">Ein Mandantenbenutzer kann ein Organisator, Organisator oder Teilnehmer sein.</span><span class="sxs-lookup"><span data-stu-id="fd67d-193">An in-tenant user can be an organizer, presenter, or attendee.</span></span>
* <span data-ttu-id="fd67d-194">**Gast**: Ein Gast ist ein Teilnehmer aus einer anderen Organisation, der eingeladen ist, auf Teams oder andere Ressourcen im Mandanten der Organisation zu zugreifen.</span><span class="sxs-lookup"><span data-stu-id="fd67d-194">**Guest**: A guest is a participant from another organization invited to access Teams or other resources in the organization's tenant.</span></span> <span data-ttu-id="fd67d-195">Gäste werden dem AAD Ihrer Organisation hinzugefügt und verfügen über dieselben Teams-Funktionen wie ein systemeigenes Teammitglied mit Zugriff auf Teamchats, Besprechungen und Dateien.</span><span class="sxs-lookup"><span data-stu-id="fd67d-195">Guests are added to your organization’s AAD and have the same Teams capabilities as a native team member with access to team chats, meetings, and files.</span></span> <span data-ttu-id="fd67d-196">Ein Gastbenutzer kann ein Organisator, Organisator oder Teilnehmer sein.</span><span class="sxs-lookup"><span data-stu-id="fd67d-196">A guest user can be an organizer, presenter, or attendee.</span></span> <span data-ttu-id="fd67d-197">Weitere Informationen finden Sie unter [Gastzugriff in Teams](/microsoftteams/guest-access).</span><span class="sxs-lookup"><span data-stu-id="fd67d-197">For more information, see [guest access in Teams](/microsoftteams/guest-access).</span></span>
* <span data-ttu-id="fd67d-198">**Verbund oder extern:** Ein Verbundbenutzer ist ein externer Teams-Benutzer in einer anderen Organisation, der zur Teilnahme an einer Besprechung eingeladen wurde.</span><span class="sxs-lookup"><span data-stu-id="fd67d-198">**Federated or external**: A federated user is an external Teams user in another organization who has been invited to join a meeting.</span></span> <span data-ttu-id="fd67d-199">Diese Benutzer verfügen über gültige Anmeldeinformationen bei Verbundpartnern und sind von Teams autorisiert.</span><span class="sxs-lookup"><span data-stu-id="fd67d-199">These users have valid credentials with federated partners and are authorized by Teams.</span></span> <span data-ttu-id="fd67d-200">Sie haben keinen Zugriff auf Ihre Teams oder andere freigegebene Ressourcen aus Ihrer Organisation.</span><span class="sxs-lookup"><span data-stu-id="fd67d-200">They do not have access to your teams or other shared resources from your organization.</span></span> <span data-ttu-id="fd67d-201">Der Gastzugriff ist eine bessere Option für externe Benutzer, um Zugriff auf Teams und Kanäle zu haben.</span><span class="sxs-lookup"><span data-stu-id="fd67d-201">Guest access is a better option for external users to have access to teams and channels.</span></span> <span data-ttu-id="fd67d-202">Weitere Informationen finden Sie unter [Verwalten des externen Zugriffs in Teams](/microsoftteams/manage-external-access).</span><span class="sxs-lookup"><span data-stu-id="fd67d-202">For more information, see [manage external access in Teams](/microsoftteams/manage-external-access).</span></span>
* <span data-ttu-id="fd67d-203">**Anonym:** Anonyme Benutzer verfügen nicht über eine AAD-Identität und sind nicht mit einem Mandanten in Verbindung.</span><span class="sxs-lookup"><span data-stu-id="fd67d-203">**Anonymous**: Anonymous users do not have an AAD identity and are not federated with a tenant.</span></span> <span data-ttu-id="fd67d-204">Der anonyme Teilnehmer ist wie ein externer Benutzer, aber seine Identität wird in der Besprechung nicht projiziert.</span><span class="sxs-lookup"><span data-stu-id="fd67d-204">The anonymous participant is like an external user, but their identity is not projected in the meeting.</span></span> <span data-ttu-id="fd67d-205">Anonyme Benutzer können in einem Besprechungsfenster nicht auf Apps zugreifen.</span><span class="sxs-lookup"><span data-stu-id="fd67d-205">Anonymous users are not able to access apps in a meeting window.</span></span> <span data-ttu-id="fd67d-206">Ein anonymer Benutzer kann kein Organisator sein, aber ein Organisator oder Teilnehmer sein.</span><span class="sxs-lookup"><span data-stu-id="fd67d-206">An anonymous user cannot be an organizer but can be a presenter or attendee.</span></span>

## <a name="see-also"></a><span data-ttu-id="fd67d-207">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="fd67d-207">See also</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="fd67d-208">Tab</span><span class="sxs-lookup"><span data-stu-id="fd67d-208">Tab</span></span>](../tabs/what-are-tabs.md#how-do-tabs-work)

> [!div class="nextstepaction"]
> [<span data-ttu-id="fd67d-209">Bot</span><span class="sxs-lookup"><span data-stu-id="fd67d-209">Bot</span></span>](../bots/what-are-bots.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="fd67d-210">Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="fd67d-210">Messaging extension</span></span>](../messaging-extensions/what-are-messaging-extensions.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="fd67d-211">Entwerfen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="fd67d-211">Design your app</span></span>](../apps-in-teams-meetings/design/designing-apps-in-meetings.md)

## <a name="next-steps"></a><span data-ttu-id="fd67d-212">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="fd67d-212">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="fd67d-213">Erstellen Sie Ihre Anwendung</span><span class="sxs-lookup"><span data-stu-id="fd67d-213">Build your app</span></span>](create-apps-for-teams-meetings.md)
