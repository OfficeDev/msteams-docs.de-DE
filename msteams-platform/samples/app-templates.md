---
title: Microsoft Teams-App-Vorlagen
description: Links und Beschreibungen von App-Vorlagen für die Microsoft Teams-Plattform
ms.topic: reference
keywords: Beispielbeispiele für Microsoft Teams Vorlagen
localization_priority: Normal
ms.author: lajanuar
author: surbhigupta
ms.openlocfilehash: 72bb5506e552dfa3d35426e99a7ee74088ef41f6
ms.sourcegitcommit: 0a775ae12419f3bc7484e557f4b4ae815bab64ec
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/08/2021
ms.locfileid: "53333694"
---
# <a name="app-templates-for-microsoft-teams"></a><span data-ttu-id="a6839-104">App-Vorlagen für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="a6839-104">App templates for Microsoft Teams</span></span>

<span data-ttu-id="a6839-105">App-Vorlagen sind Beispiele für vollständige Apps für Microsoft Teams, die Open Source sind und auf GitHub verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="a6839-105">App templates are examples of complete apps for Microsoft Teams that are open-source and available on GitHub.</span></span> <span data-ttu-id="a6839-106">Jede App-Vorlage enthält detaillierte Anweisungen für die Bereitstellung und Installation dieser App für Ihre Organisation.</span><span class="sxs-lookup"><span data-stu-id="a6839-106">Each app template contains detailed instructions for deploying and installing that app for your organization.</span></span> <span data-ttu-id="a6839-107">Außerdem wird eine Beispiel-App bereitgestellt, die Sie sofort installieren und verwenden können.</span><span class="sxs-lookup"><span data-stu-id="a6839-107">It also provides a sample app that you can install and start using immediately.</span></span> <span data-ttu-id="a6839-108">Der vollständige Quellcode ist ebenfalls verfügbar, sodass Sie ihn im Detail untersuchen oder den Code verzweigen und an Ihre spezifischen Anforderungen anpassen können.</span><span class="sxs-lookup"><span data-stu-id="a6839-108">The complete source code is also available, which allows you to explore it in detail or fork the code and alter it to meet your specific requirements.</span></span>
<span data-ttu-id="a6839-109">Alle App-Vorlagen werden unter den [MIT-Lizenzbedingungen](https://github.com/OfficeDev/microsoft-teams-apps-eprescription/blob/master/LICENSE) bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="a6839-109">All app templates are provided under the [MIT License](https://github.com/OfficeDev/microsoft-teams-apps-eprescription/blob/master/LICENSE) terms.</span></span>

> [!NOTE] 
> <span data-ttu-id="a6839-110">Sie müssen Apps, die aus App-Vorlagen für Ihre Benutzer und Organisationen erstellt wurden, lizenzieren und unterstützen.</span><span class="sxs-lookup"><span data-stu-id="a6839-110">You must license and support apps created from app templates for your users and organizations.</span></span>

<span data-ttu-id="a6839-111">**&#9734; Gibt neu veröffentlichte App-Vorlagen an.**</span><span class="sxs-lookup"><span data-stu-id="a6839-111">**&#9734; Indicates newly released app templates.**</span></span>

### <a name="key-benefits"></a><span data-ttu-id="a6839-112">Wichtige Vorteile</span><span class="sxs-lookup"><span data-stu-id="a6839-112">Key benefits</span></span>

* <span data-ttu-id="a6839-113">**Direkte Bereitstellung in der Cloud:** Alle App-Vorlagen enthalten Bereitstellungsskripts, mit denen Sie alle erforderlichen Dienste in Microsoft Azure oder der Power Platform hosten können.</span><span class="sxs-lookup"><span data-stu-id="a6839-113">**Deploy directly to the cloud:** All app templates include deployment scripts that allows you to host all required services in Microsoft Azure or the Power Platform.</span></span> 
* <span data-ttu-id="a6839-114">**Empfohlener Beispielcode:** Die App-Vorlagen entsprechen den empfohlenen bewährten Methoden für Sicherheit und Infrastruktur.</span><span class="sxs-lookup"><span data-stu-id="a6839-114">**Recommended sample code:** The app templates conform to recommended best practices around security and infrastructure.</span></span> <span data-ttu-id="a6839-115">Alle von der Community übermittelten Änderungen an den App-Vorlagen werden überprüft, um die Konformität sicherzustellen.</span><span class="sxs-lookup"><span data-stu-id="a6839-115">All community submitted changes to the app templates are reviewed to ensure conformance.</span></span>
* <span data-ttu-id="a6839-116">**Anpassbar und erweiterbar:** Während alle App-Vorlagen mit minimaler Konfiguration bereitgestellt werden, werden die gesamte Codebasis und Bereitstellungsskripts bereitgestellt, sodass Sie sie einfach anpassen oder an Ihre individuellen Anforderungen erweitern können.</span><span class="sxs-lookup"><span data-stu-id="a6839-116">**Customizable and extensible:** While all app templates are deployed with minimal configuration, the entire code base and deployment scripts are provided, so that you can easily customize or extend them to fit your unique needs.</span></span>
* <span data-ttu-id="a6839-117">**Ausführliche Dokumentation:** Alle App-Vorlagen werden von einer End-to-End-Dokumentation zu Lösungsarchitektur, Bereitstellung und Konfigurationsschritten begleitet.</span><span class="sxs-lookup"><span data-stu-id="a6839-117">**Detailed documentation:** All app templates are accompanied by end-to-end documentation on solution architecture, deployment, and configuration steps.</span></span>  

## <a name="adoption-bot"></a><span data-ttu-id="a6839-118">Einführungs-Bot</span><span class="sxs-lookup"><span data-stu-id="a6839-118">Adoption Bot</span></span> 

<span data-ttu-id="a6839-119">Adoption Bot ist ein Benutzer-Care-Chat-Bot, der mit Power Virtual Agent für Teams PVA erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="a6839-119">Adoption Bot is a user care chat bot built with Power Virtual Agent for Teams PVA.</span></span> <span data-ttu-id="a6839-120">Sie wird als PVA-Version von FAQ Plus betrachtet.</span><span class="sxs-lookup"><span data-stu-id="a6839-120">It is considered as the PVA version of FAQ Plus.</span></span> <span data-ttu-id="a6839-121">Adoption Bot beantwortet mehr als 100 allgemeine Fragen zu Microsoft 365 und Teams.</span><span class="sxs-lookup"><span data-stu-id="a6839-121">Adoption Bot answers 100+ common questions about Microsoft 365 and Teams.</span></span> <span data-ttu-id="a6839-122">Sie können die vorhandenen Themen bearbeiten, Eigene Themen hinzufügen und vorhandene HÄUFIG gestellte Fragen erfassen.</span><span class="sxs-lookup"><span data-stu-id="a6839-122">You can edit the existing topics, add your own topics, and ingest existing FAQs.</span></span> <span data-ttu-id="a6839-123">Wenn Benutzer zusätzliche Hilfe benötigen, kann der Einführungsbot sie mit Experten verbinden oder sogar auf offene Servicetickets mit Premium-Flow-Connectors erweitert werden.</span><span class="sxs-lookup"><span data-stu-id="a6839-123">If users need additional help, Adoption Bot can connect them to experts or even be extended to open service tickets with premium flow connectors.</span></span> <span data-ttu-id="a6839-124">Dieser Bot ist selbst installiert oder in eine benutzerdefinierte App integriert, z. B. den [Einführungshub.](https://github.com/akporzondek/adoption_hub)</span><span class="sxs-lookup"><span data-stu-id="a6839-124">This bot is self-installed or built into a custom app, such as the [Adoption Hub](https://github.com/akporzondek/adoption_hub).</span></span>

[<span data-ttu-id="a6839-125">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-125">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-adopt-bot)

## <a name="adoption-tool--champion-management-platform-9734"></a><span data-ttu-id="a6839-126">Einführungstool – Champion Management Platform &#9734;</span><span class="sxs-lookup"><span data-stu-id="a6839-126">Adoption Tool- Champion Management Platform &#9734;</span></span>

<span data-ttu-id="a6839-127">Die Vorlage der Champion Management Platform (CMP)-App hilft Ihnen, Ihre Teamarbeitspionier zu verwalten, zu skalieren und zu inspirieren, um mehr zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="a6839-127">The Champion Management Platform (CMP) app template helps you manage, scale, and inspire your teamwork champions to achieve more.</span></span> <span data-ttu-id="a6839-128">Diese App-Vorlage basiert auf dem SharePoint-Framework und wird in eine Registerkarte innerhalb eines Teams geladen.</span><span class="sxs-lookup"><span data-stu-id="a6839-128">This app template is built on the SharePoint Framework and loaded into a tab within a team.</span></span> <span data-ttu-id="a6839-129">Gruppen können dieses Tool nutzen, um die Programmmitgliedschaft zu verwalten, eine Bestenliste und Ereignistypen für die Protokollierung bereitzustellen und Tools zum Überlagern digitaler Badges an Programmteilnehmer bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="a6839-129">Groups can leverage this tool to help manage program membership, provide a leaderboard and event types for logging, and tools to overlay digital badges to program participants.</span></span>

[<span data-ttu-id="a6839-130">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-130">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-champion-management)

## <a name="adoption-tool--microsoft-365-learning-pathways-get-started-9734"></a><span data-ttu-id="a6839-131">Einführungstool– Microsoft 365 Learning Pfade (Erste Schritte) &#9734;</span><span class="sxs-lookup"><span data-stu-id="a6839-131">Adoption Tool- Microsoft 365 Learning Pathways (Get Started) &#9734;</span></span>

<span data-ttu-id="a6839-132">Mit der Erste Schritte App-Vorlage können Sie die Leistungsfähigkeit Microsoft 365 Lernpfade innerhalb von Microsoft Teams nutzen.</span><span class="sxs-lookup"><span data-stu-id="a6839-132">The Get Started app template allows you to bring the power of Microsoft 365 learning pathways inside of Microsoft Teams.</span></span> <span data-ttu-id="a6839-133">Mit dieser App-Vorlage können Sie einfachen Zugriff auf bestimmte Schulungsseiten oder andere Intranetressourcen gewähren und die Inhalte direkt in Teams laden.</span><span class="sxs-lookup"><span data-stu-id="a6839-133">This app template allows you to grant easy access to specific training pages or other intranet assets and load the content directly within Teams.</span></span> <span data-ttu-id="a6839-134">Sie können den App-Namen oder das Logo auch so ändern, dass er ihrem Unternehmensbranding entspricht.</span><span class="sxs-lookup"><span data-stu-id="a6839-134">You can also change the app name or logo to match your company branding.</span></span>

[<span data-ttu-id="a6839-135">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-135">Get it on GitHub</span></span>](https://github.com/msft-teams/tools/tree/master/M365%20Learning%20Pathways)

## <a name="appointment-manager"></a><span data-ttu-id="a6839-136">Termin-Manager</span><span class="sxs-lookup"><span data-stu-id="a6839-136">Appointment Manager</span></span> 

<span data-ttu-id="a6839-137">Appointment Manager ist eine Teams App-Vorlage, die Unternehmen dabei unterstützt, virtuelle Termine mit Verbrauchern über Teams zu erstellen, zu verwalten und durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="a6839-137">Appointment Manager is a Teams app template to help businesses create, manage, and conduct virtual appointments with consumers through Teams.</span></span> <span data-ttu-id="a6839-138">Neue Terminanfragen von Verbrauchern sind in Teams Kanälen sichtbar, wo sie schnell zugewiesen und mitarbeitern in einem Team zugewiesen werden.</span><span class="sxs-lookup"><span data-stu-id="a6839-138">New appointment requests from consumers are visible in Teams channels, where they are quickly assigned and reassigned to staff in a team.</span></span> <span data-ttu-id="a6839-139">Terminanfragen werden auf Team- oder persönlicher Ebene über benutzerdefinierte Registerkarten angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a6839-139">Appointment requests are viewed at team or personal levels through custom tabs.</span></span> <span data-ttu-id="a6839-140">Jeder Termin ist mit einer Teams Onlinebesprechung verknüpft, daher können die Mitarbeiter und Verbraucher einfach zur geplanten Zeit an der Besprechung teilnehmen.</span><span class="sxs-lookup"><span data-stu-id="a6839-140">Every appointment is associated with a Teams online meeting, hence the staff and consumers can easily join the meeting at the scheduled time.</span></span>

<span data-ttu-id="a6839-141">Die App-Vorlage kann zur einfachen Terminverwaltung in Microsoft Bookings integriert werden.</span><span class="sxs-lookup"><span data-stu-id="a6839-141">The app template integrates with Microsoft Bookings for easy appointment management.</span></span> <span data-ttu-id="a6839-142">Geplante Termine werden automatisch in den Kalendern der zugewiesenen Mitarbeiter angezeigt, und Verbraucher erhalten anpassbare E-Mail-Benachrichtigungen und Erinnerungen mit eingebetteten Besprechungslinks.</span><span class="sxs-lookup"><span data-stu-id="a6839-142">Scheduled appointments automatically appear on assigned staff members' calendars, and consumers receive customizable email notifications and reminders with embedded meeting links.</span></span>

[<span data-ttu-id="a6839-143">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-143">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-appointment-manager)

<span data-ttu-id="a6839-144">![Termin-Manager – Übersicht über ](../assets/images/appointment-manager-overview.png)
 ![ Terminmanager in Teams](../assets/images/appointment-manager-2.png)</span><span class="sxs-lookup"><span data-stu-id="a6839-144">![Appointment Manager Overview](../assets/images/appointment-manager-overview.png)
![Appointment Manager in Teams](../assets/images/appointment-manager-2.png)</span></span>

## <a name="ask-away"></a><span data-ttu-id="a6839-145">Ask Away</span><span class="sxs-lookup"><span data-stu-id="a6839-145">Ask Away</span></span>

<span data-ttu-id="a6839-146">Ask Away ist ein [Microsoft Teams Bot,](../bots/what-are-bots.md) mit dem Benutzer Fragen und Antworten durchführen können, die als Q&A-Sitzungen innerhalb Teams bezeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="a6839-146">Ask Away is a [Microsoft Teams bot](../bots/what-are-bots.md) that enables users to conduct Question and Answer, called Q&A sessions within Teams.</span></span> <span data-ttu-id="a6839-147">Mithilfe des Ask Away-Bots können Teammitglieder Fragen übermitteln und abstimmen, die von Kollegen geteilt werden, sodass Q&A-Hosts ganz einfach Fragen von höchster Qualität in einem Kanal oder Chat sammeln können.</span><span class="sxs-lookup"><span data-stu-id="a6839-147">Using the Ask Away bot, team members can submit and up-vote questions shared by colleagues allowing Q&A hosts to easily gather top-of-mind questions within a channel or chat.</span></span> <span data-ttu-id="a6839-148">Der Bot wird verwendet, um eine Echtzeit-Q-&A-Sitzung in einer Teams-Besprechung durchzuführen, und ermöglicht es Teilnehmern, Fragen live über den Chat zu übermitteln.</span><span class="sxs-lookup"><span data-stu-id="a6839-148">The bot is used to conduct a real-time Q&A session in a Teams meeting and allows attendees to submit questions live through chat.</span></span>

[<span data-ttu-id="a6839-149">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-149">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-askaway)

:::row:::
  :::column span="2":::
    ![Ansicht des Popup-Dialogfelds für die Bestenliste, in dem Benutzer über Fragen abstimmen können](../assets/images/ask-away-app.png)  
:::column-end:::
:::row-end:::

## <a name="associate-insights"></a><span data-ttu-id="a6839-151">Assoziierte Einblicke</span><span class="sxs-lookup"><span data-stu-id="a6839-151">Associate Insights</span></span>

<span data-ttu-id="a6839-152">Associate Insights ist eine [Power Apps](/powerapps/maker/canvas-apps/embed-teams-app) Vorlage, die Mitarbeiter in Service und Produktion in die Lage versetzt, Kundenmeinungen, Ressentiments und Wahrnehmungen direkt zu erfassen und zu übermitteln.</span><span class="sxs-lookup"><span data-stu-id="a6839-152">Associate Insights is a [Power Apps](/powerapps/maker/canvas-apps/embed-teams-app) template that empowers firstline workers to directly capture and submit customer opinion, sentiment, and perception.</span></span> <span data-ttu-id="a6839-153">Mitarbeiter in Service und Produktion sind häufig der erste Mitarbeiter des Unternehmens, der mit Kunden an einem 1:1-Kontaktpunkt zusammenarbeiten kann.</span><span class="sxs-lookup"><span data-stu-id="a6839-153">Firstline workers are often the first company representative to engage with customers in a one-to-one point-of contact.</span></span> <span data-ttu-id="a6839-154">Die gesammelten Daten werden von Geschäftsteams gemeinsam genutzt und verwendet, z. B. über eine Power BI Teams Registerkarte, um die Produktverbesserung zu verbessern und die Benutzererfahrung zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="a6839-154">The collected data are shared and used collaboratively by business teams, such as through a Power BI Teams tab, for product improvement and enhancing the customer experience.</span></span>

[<span data-ttu-id="a6839-155">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-155">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-associateinsights)

:::row:::
  :::column span="2":::
    ![Feedbackansicht der von der App generierten Einblicke](../assets/images/associate-insights-app.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Power BI Ansicht der von der App generierten Einblicke](../assets/images/associate-insights-app2.png)
:::column-end:::
:::row-end:::

## <a name="attendance"></a><span data-ttu-id="a6839-158">Anwesenheit</span><span class="sxs-lookup"><span data-stu-id="a6839-158">Attendance</span></span>

<span data-ttu-id="a6839-159">Die Anwesenheits-App ist eine [Power Apps](/powerapps/maker/canvas-apps/embed-teams-app) Registerkarte, die in einem Team angeheftet ist.</span><span class="sxs-lookup"><span data-stu-id="a6839-159">The Attendance app is a [Power Apps](/powerapps/maker/canvas-apps/embed-teams-app) tab that are pinned in a team.</span></span> <span data-ttu-id="a6839-160">Es wurde entwickelt, um Anwesenheitsinformationen in Einstellungen wie Lern- und Schulungsumgebungen zu erfassen.</span><span class="sxs-lookup"><span data-stu-id="a6839-160">It is designed to record presence in settings, such as learning and training environments.</span></span> <span data-ttu-id="a6839-161">Benutzer können die Teilnahme für bis zu 30 Tage in der Vergangenheit markieren oder bearbeiten und zusammengefasste Anwesenheitsberichte für eine ganze Gruppe oder einzelne Teilnehmer anzeigen.</span><span class="sxs-lookup"><span data-stu-id="a6839-161">Users can mark or edit attendance for up to 30 days in the past and view summarized attendance reports for an entire group or individual attendees.</span></span> <span data-ttu-id="a6839-162">Weitere Informationen zur Teilnahme an Teams finden Sie unter ["Abrufen" auf GitHub.](https://github.com/OfficeDev/microsoft-teams-apps-attendance)</span><span class="sxs-lookup"><span data-stu-id="a6839-162">For more information on teams attendance, see [Get it on GitHub](https://github.com/OfficeDev/microsoft-teams-apps-attendance).</span></span>

<span data-ttu-id="a6839-163">In der folgenden Abbildung wird die Demo der Anwesenheits-App angezeigt:</span><span class="sxs-lookup"><span data-stu-id="a6839-163">The following image displays the attendance app demo:</span></span>  

![Demo zur Anwesenheits-App](../assets/images/attendance-app.png)

## <a name="book-a-room"></a><span data-ttu-id="a6839-165">Book-a-room</span><span class="sxs-lookup"><span data-stu-id="a6839-165">Book-a-room</span></span>

<span data-ttu-id="a6839-166">"Book-a-room" ist ein [Microsoft Teams Bot,](../bots/what-are-bots.md) mit dem Benutzer schnell einen Besprechungsraum für 30, 60 oder 90 Minuten ab der aktuellen Zeit suchen und reservieren können.</span><span class="sxs-lookup"><span data-stu-id="a6839-166">Book-a-room is a [Microsoft Teams bot](../bots/what-are-bots.md) that allows users quickly to find and reserve a meeting room for 30, 60, or 90 minutes starting from the current time.</span></span> <span data-ttu-id="a6839-167">Die Standardzeit beträgt 30 Minuten.</span><span class="sxs-lookup"><span data-stu-id="a6839-167">The default time is 30 minutes.</span></span> <span data-ttu-id="a6839-168">Der Book-a-Room-Bot umfasst persönliche oder 1:1-Unterhaltungen.</span><span class="sxs-lookup"><span data-stu-id="a6839-168">The Book-a-room bot scopes to personal or 1:1 conversations.</span></span> <span data-ttu-id="a6839-169">Weitere Informationen zur Book-a-Room-App finden Sie unter ["Get it on GitHub."](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom)</span><span class="sxs-lookup"><span data-stu-id="a6839-169">For more information on Book-a-room app, see [Get it on GitHub](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom).</span></span>  
<span data-ttu-id="a6839-170">In der folgenden Abbildung wird die Demo "Book-a-room" angezeigt:</span><span class="sxs-lookup"><span data-stu-id="a6839-170">The following image displays the Book-a-room demo:</span></span>

![Demo zu "Book-a-room"](../assets/images/book-a-room.png)

## <a name="building-access"></a><span data-ttu-id="a6839-172">Gebäudezugriff</span><span class="sxs-lookup"><span data-stu-id="a6839-172">Building Access</span></span>

<span data-ttu-id="a6839-173">Building Access ist eine Microsoft [Power Platform-basierte](https://powerapps.microsoft.com/blog/now-in-preview-customize-teams-with-built-in-power-platform-capabilities/) App, die die Verwaltung von Schwellenwerten für die Erstellung von Sicherheitslücken und sozialen Abgrenzungsnormen unterstützt, indem Es Einrichtungen-Directors ermöglicht, die Anwesenheit von Mitarbeitern vor Ort zu verwalten, nachzuverfolgen und zu melden.</span><span class="sxs-lookup"><span data-stu-id="a6839-173">Building Access is a Microsoft [Power Platform](https://powerapps.microsoft.com/blog/now-in-preview-customize-teams-with-built-in-power-platform-capabilities/) based app that supports the administration of building occupancy thresholds and social distancing norms by enabling facilities directors to manage, track, and report employee on-site presence.</span></span> <span data-ttu-id="a6839-174">Die App, die mit Microsoft [Power Apps](/powerapps/powerapps-overview)und [Power Automate](/power-automate/getting-started)erstellt wurde, ist tief in Microsoft Teams integriert und ermöglicht Es Organisationen, die Bereitschaft zum Aufbau zu bestimmen, Berechtigungskriterien für den Zugriff vor Ort festzulegen und Einblicke für die zukünftige Planung zu sammeln.</span><span class="sxs-lookup"><span data-stu-id="a6839-174">The app, built using Microsoft [Power Apps](/powerapps/powerapps-overview), and [Power Automate](/power-automate/getting-started), deeply integrates with Microsoft Teams and enables organizations to determine building readiness, establish eligibility criteria for on-site access, and gather insights for future planning.</span></span>

[<span data-ttu-id="a6839-175">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-175">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-buildingaccess)

:::row:::
   :::column span="":::
     ![Erstellen einer Zugriffsreservierungskarte](../assets/images/building-access-reservation.png)
   :::column-end:::
   :::column span="":::
      ![Erstellen der Zugriffstastenansicht](../assets/images/building-access-access-key.png)
   :::column-end:::
:::row-end:::

## <a name="celebrations"></a><span data-ttu-id="a6839-178">Feiern</span><span class="sxs-lookup"><span data-stu-id="a6839-178">Celebrations</span></span>

<span data-ttu-id="a6839-179">Es handelt sich um eine Teams-App, die Teammitgliedern dabei hilft, ihre Geburtstage, Jahrestage und andere wiederkehrende Ereignisse zu begehen.</span><span class="sxs-lookup"><span data-stu-id="a6839-179">Celebrations is a Teams app that helps team members to celebrate each others' birthdays, anniversaries, and other recurring events.</span></span> <span data-ttu-id="a6839-180">Es erinnert sich an besondere Gelegenheiten aller Teammitglieder und sendet eine freundliche Nachricht in allen Teams, die zum Zeitpunkt der Ereigniserstellung ausgewählt wurden, damit die Teammitglieder sich an ihrem Tag besonders fühlen.</span><span class="sxs-lookup"><span data-stu-id="a6839-180">It remembers special occasions of all the team members and sends a friendly message in all the teams selected at the time of event creation, to make the team members feel special on their day.</span></span>

<span data-ttu-id="a6839-181">Die App bietet allen Teammitgliedern eine einfache Benutzeroberfläche zum persönlichen Hinzufügen und Anzeigen ihrer Ereignisse und ermöglicht es dem Benutzer, die Teams auszuwählen, in denen die Ereignisse freigegeben werden.</span><span class="sxs-lookup"><span data-stu-id="a6839-181">The app provides an easy interface for all the team members to personally add and view their events and also allows the user to select the teams in which the events gets shared.</span></span>

[<span data-ttu-id="a6839-182">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-182">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-celebrations-app)

## <a name="checklist"></a><span data-ttu-id="a6839-183">Checkliste</span><span class="sxs-lookup"><span data-stu-id="a6839-183">Checklist</span></span>

<span data-ttu-id="a6839-184">Prüfliste ist eine benutzerdefinierte Microsoft Teams [Messaging-Erweiterungs-App,](../messaging-extensions/what-are-messaging-extensions.md) mit der Sie mit Ihrem Team zusammenarbeiten können, indem Sie eine freigegebene Checkliste in einem Chat oder Kanal erstellen.</span><span class="sxs-lookup"><span data-stu-id="a6839-184">Checklist is a custom Microsoft Teams [messaging extension](../messaging-extensions/what-are-messaging-extensions.md) app that enables you to collaborate with your team by creating a shared checklist in a chat or channel.</span></span> <span data-ttu-id="a6839-185">Die App wird auf allen Teams Plattformclients unterstützt, z. B. Desktopbrowser, iOS und Android.</span><span class="sxs-lookup"><span data-stu-id="a6839-185">The app is supported across all Teams platform clients, such as desktop browser, iOS, and Android.</span></span> <span data-ttu-id="a6839-186">Die App ist bereit für die Bereitstellung als Teil Ihres Microsoft 365-Abonnements.</span><span class="sxs-lookup"><span data-stu-id="a6839-186">The app is ready for deployment as part of your Microsoft 365 subscription.</span></span>  

[<span data-ttu-id="a6839-187">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-187">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-checklist-app)

:::row:::
:::column span="2":::
    ![Erstellen einer Prüfliste in Teams Ansicht](../assets/images/checklist-app-template-compose-view.gif)  
:::column-end:::
:::row-end:::

## <a name="classroom-drop-in"></a><span data-ttu-id="a6839-189">Kursraum-Drop-In</span><span class="sxs-lookup"><span data-stu-id="a6839-189">Classroom Drop-in</span></span> 

<span data-ttu-id="a6839-190">Classroom Drop-in ist eine Microsoft [Power Platform-basierte](https://powerapps.microsoft.com/blog/now-in-preview-customize-teams-with-built-in-power-platform-capabilities/)App, die Es Systemleitern ermöglicht, Kursteams zu finden, bedeutet virtuelle Kursräume und sich selbst oder andere zu diesen Kursteams für einen bestimmten Drop-In-Zeitraum hinzuzufügen, je nach Bedarf.</span><span class="sxs-lookup"><span data-stu-id="a6839-190">Classroom Drop-in is a Microsoft [Power Platform](https://powerapps.microsoft.com/blog/now-in-preview-customize-teams-with-built-in-power-platform-capabilities/)-based app that enables system leaders to find class teams, means virtual classrooms and add themselves or others to these class teams for a specified drop-in period, as needed.</span></span> <span data-ttu-id="a6839-191">Die App, die mit Microsoft [Power Apps](/powerapps/powerapps-overview) und [Power Automate](/power-automate/getting-started)erstellt wurde, ist tief in Microsoft Teams integriert, um sicherzustellen, dass Bildungseinrichtung ihre Vorgänge in einer hybriden Lernumgebung optimieren kann, indem sie den Zugriff auf relevante Projektbeteiligten für Kursteams gemäß den Geschäftsanforderungen ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="a6839-191">The app built using Microsoft [Power Apps](/powerapps/powerapps-overview) and [Power Automate](/power-automate/getting-started), deeply integrates with Microsoft Teams to ensure educational institutes can optimize their operations in a hybrid learning environment by providing access to relevant stakeholders for class teams per business requirements.</span></span>

[<span data-ttu-id="a6839-192">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-192">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-classroom-dropin)

![Kursraum-Drop-In-Anforderung](../assets/images/classroom-drop-in-request.png)

## <a name="company-communicator"></a><span data-ttu-id="a6839-194">Unternehmens-Communicator</span><span class="sxs-lookup"><span data-stu-id="a6839-194">Company Communicator</span></span>

<span data-ttu-id="a6839-195">Die Unternehmens-Communicator-App ermöglicht es Unternehmensteams, Nachrichten zu erstellen und zu senden, die für mehrere Teams oder eine große Anzahl von Mitarbeitern per Chat vorgesehen sind, sodass die Organisation Mitarbeiter direkt dort erreichen kann, wo sie zusammenarbeiten.</span><span class="sxs-lookup"><span data-stu-id="a6839-195">The Company Communicator app enables corporate teams to create and send messages intended for multiple teams or large number of employees over chat allowing organization to reach employees right where they collaborate.</span></span> <span data-ttu-id="a6839-196">Nutzen Sie diese Vorlage für mehrere Szenarien, z. B. Ankündigungen neuer Initiativen, Mitarbeiter-Onboarding, modernes Lernen und Entwicklung oder organisationsweite Übertragungen.</span><span class="sxs-lookup"><span data-stu-id="a6839-196">Utilize this template for multiple scenarios such as new initiative announcements, employee onboarding, modern learning, and development or organization-wide broadcasts.</span></span>

<span data-ttu-id="a6839-197">Die App bietet eine einfache Benutzeroberfläche für festgelegte Benutzer zum Erstellen, Anzeigen einer Vorschau, Zusammenarbeit und Senden von Nachrichten.</span><span class="sxs-lookup"><span data-stu-id="a6839-197">The app provides an easy interface for designated users to create, preview, collaborate and send messages.</span></span>

<span data-ttu-id="a6839-198">Es bietet eine Grundlage zum Erstellen von benutzerdefinierten, gezielten Kommunikationsfunktionen, z. B. benutzerdefinierte Telemetrie darüber, wie viele Benutzer eine Nachricht bestätigt oder mit dieser interagiert haben.</span><span class="sxs-lookup"><span data-stu-id="a6839-198">It provides a foundation to build custom targeted communication capabilities such as custom telemetry on how many users acknowledged or interacted with a message.</span></span>

[<span data-ttu-id="a6839-199">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-199">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-company-communicator-app)

![jCompany Communicator Verfassenfeldansicht](../assets/images/CompanyCommunicatorCompose.png)

## <a name="contact-group-lookup"></a><span data-ttu-id="a6839-201">Kontaktgruppen-Nachschlagevorgang</span><span class="sxs-lookup"><span data-stu-id="a6839-201">Contact Group Lookup</span></span>

<span data-ttu-id="a6839-202">Die Kontaktgruppen-Nachschlage-App bietet einen praktischen und nützlichen Ansatz zum Erstellen, Zugreifen und Verwalten der Kontaktgruppen Ihrer Organisation, die früher als Verteilerlisten oder Kommunikationsgruppen bezeichnet wurden.</span><span class="sxs-lookup"><span data-stu-id="a6839-202">The Contact Group Lookup app provides a convenient and useful approach to creating, accessing, and managing your organization's contact groups, formerly known as distribution lists or communication groups.</span></span> <span data-ttu-id="a6839-203">Benutzer können schnell Gruppenmitglieder anzeigen und mit ihnen chatten, den Mitgliederstatus anzeigen und einen Gruppenchat mit ausgewählten Mitgliedern in der Kontaktgruppe erstellen, alles innerhalb der Teams Umgebung.</span><span class="sxs-lookup"><span data-stu-id="a6839-203">Users can quickly view and chat with group members, view member status, and create a group chat with selected members in the contact group, all within the Teams environment.</span></span>

[<span data-ttu-id="a6839-204">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-204">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-app-contactgrouplookup)

:::row:::
:::column span="2":::
    ![Angeheftete Favoritenansicht für Kontaktgruppensuche](../assets/images/contact-group-lookup-favorites.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Demo zum Starten des Chats für die Kontaktgruppensuche](../assets/images/contact-group-lookup-chat.png)
:::column-end:::
:::row-end:::

## <a name="co-worker-appreciation"></a><span data-ttu-id="a6839-207">Kollegen ( Co-Worker- Und Arbeitskraft)</span><span class="sxs-lookup"><span data-stu-id="a6839-207">Co-worker Appreciation</span></span> 

<span data-ttu-id="a6839-208">Mithilfe der Vorlage "Mitarbeiterarbeitshilfe" in Microsoft Teams können Benutzer die Erfolge ihrer Kollegen im Kontext der Teams erkennen.</span><span class="sxs-lookup"><span data-stu-id="a6839-208">Using the co-worker appreciation template in Microsoft Teams, users can recognize their colleagues' achievements within the Teams’ context.</span></span> <span data-ttu-id="a6839-209">Wenn Kollegen auswählen, einen Kollegen zu beloben, werden Empfänger und andere Teammitglieder in einer Kanalunterhaltung markiert und erhalten eine Benachrichtigung über die Preisdetails des Kanals.</span><span class="sxs-lookup"><span data-stu-id="a6839-209">When co-workers select to reward a colleague, recipients and other team members are tagged in a channel conversation and they receive a notification about the channel's award details.</span></span> <span data-ttu-id="a6839-210">Die Preise werden in der Teams-App aufgezeichnet, die sicher, portierbar und leicht freigabefähig ist.</span><span class="sxs-lookup"><span data-stu-id="a6839-210">The awards are recorded in the Teams app, which is secure, portable, and easily shareable.</span></span> <span data-ttu-id="a6839-211">Dies wird als die PowerApps-basierte Version der Open Badges-App-Vorlage mit einer Bestenliste betrachtet.</span><span class="sxs-lookup"><span data-stu-id="a6839-211">This is considered as the PowerApps based version of the Open Badges app template, with a leaderboard.</span></span>

[<span data-ttu-id="a6839-212">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-212">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-coworker-appreciation)

![Insgesamt](../assets/images/coworker-appreciation-1.png)

## <a name="crowdsourcer"></a><span data-ttu-id="a6839-214">CrowdSourcer</span><span class="sxs-lookup"><span data-stu-id="a6839-214">CrowdSourcer</span></span>

<span data-ttu-id="a6839-215">CrowdSourcer ist ein [Microsoft Teams Bot,](../bots/what-are-bots.md) der teams abgefragte Informationen bereitstellt, die gemeinsam von Gruppenmitgliedern stammen.</span><span class="sxs-lookup"><span data-stu-id="a6839-215">CrowdSourcer is a [Microsoft Teams bot](../bots/what-are-bots.md) that gives teams queried information sourced collaboratively from group members.</span></span> <span data-ttu-id="a6839-216">Es hilft ihnen, häufig gestellte Fragen zu beantworten und den Teilnehmern zu ermöglichen, sich aktiv zu engagieren und zu einer interessanten und hilfreichen Informationsressource beizutragen.</span><span class="sxs-lookup"><span data-stu-id="a6839-216">It helps to answer frequently asked questions while enabling participants to actively engage in and contribute to a fun and helpful information resource.</span></span>

[<span data-ttu-id="a6839-217">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-217">Get it on Github</span></span>](https://github.com/OfficeDev/microsoft-teams-crowdsourcer-app)

![Crowdsource-Endbenutzerinteraktion](../assets/images/crowdsourcer.png)

## <a name="custom-stickers"></a><span data-ttu-id="a6839-219">Custom Stickers</span><span class="sxs-lookup"><span data-stu-id="a6839-219">Custom Stickers</span></span>

<span data-ttu-id="a6839-220">Self-Expression ist der Kern einer fehlerfreien Teamkultur.</span><span class="sxs-lookup"><span data-stu-id="a6839-220">Self-expression is core to a healthy team culture.</span></span> <span data-ttu-id="a6839-221">Diese App-Vorlage ist eine [Messaging-Erweiterung,](~/messaging-extensions/what-are-messaging-extensions.md) mit der Ihre Benutzer benutzerdefinierte Aufkleber und GIFs innerhalb Microsoft Teams verwenden können.</span><span class="sxs-lookup"><span data-stu-id="a6839-221">This app template is a [messaging extension](~/messaging-extensions/what-are-messaging-extensions.md) that enables your users to use custom stickers and GIFs within Microsoft Teams.</span></span> <span data-ttu-id="a6839-222">Diese Vorlage bietet eine einfache webbasierte Konfigurationsumgebung, bei der jeder Benutzer mit Konfigurationszugriff gifs, Aufkleber und Bilder hochladen kann, die seine Benutzer haben sollen, sodass Ihr gesamtes Team eine beliebige Gruppe von Stickern verwenden kann.</span><span class="sxs-lookup"><span data-stu-id="a6839-222">This template provides an easy web-based configuration experience where anyone with configuration access can upload the GIFs, stickers, and images they want their users to have, allowing your entire team to use any set of stickers you choose.</span></span>

<span data-ttu-id="a6839-223">Diese App ermöglicht auch die einfache Freigabe von Bildern, GIFs und Aufklebern in teamsweit, ohne zugriff auf SharePoint Websites oder einzelne Kanäle als Speicher- und Freigabemechanismen zu benötigen.</span><span class="sxs-lookup"><span data-stu-id="a6839-223">This app also enables easy sharing of images, GIFs, stickers across teams without needing access to SharePoint sites or individual channels as storage and sharing mechanisms.</span></span> <span data-ttu-id="a6839-224">Beispielsweise können Produktteams ganz einfach Produktbilder und GIFs programmgesteuert für Soziale Medien, Marketing und Vertriebsteams freigeben.</span><span class="sxs-lookup"><span data-stu-id="a6839-224">For example, product teams can easily share product images and GIFs to social media, marketing, and sales teams programmatically.</span></span> <span data-ttu-id="a6839-225">Sie können diese App auch erweitern, indem sie einen Benachrichtigungsfluss für bestimmte Teams oder Einzelpersonen auslöst, wenn neue Bilder und GIFs verfügbar gemacht werden.</span><span class="sxs-lookup"><span data-stu-id="a6839-225">One can also extend this app by triggering a notification flow to specific teams or individuals when new images, and GIFs are made available.</span></span>

[<span data-ttu-id="a6839-226">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-226">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-stickers-app)

![Aufkleber-App](../assets/images/stickers.png)

## <a name="employee-ideas"></a><span data-ttu-id="a6839-228">Ideen für Mitarbeiter</span><span class="sxs-lookup"><span data-stu-id="a6839-228">Employee Ideas</span></span>

<span data-ttu-id="a6839-229">Die App "Mitarbeiterideen" ist die PowerApps-Version der Azure-basierten App-Vorlage "Großartige Ideen".</span><span class="sxs-lookup"><span data-stu-id="a6839-229">The Employee Ideas app is the PowerApps version of the Azure based Great Ideas app template.</span></span> <span data-ttu-id="a6839-230">Die App ermöglicht es den Teams Benutzern, eine Ideenkampagne einzurichten und zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="a6839-230">The app enables the Teams users to set up and configure an idea campaign.</span></span> <span data-ttu-id="a6839-231">Eine Ideenkampagne ist eine Kategorie zum Gruppieren von Ideen zu allgemeinen Designs.</span><span class="sxs-lookup"><span data-stu-id="a6839-231">An idea campaign is a category for grouping ideas around common themes.</span></span>

<span data-ttu-id="a6839-232">Teams Benutzer können auch die folgenden Aktivitäten ausführen:</span><span class="sxs-lookup"><span data-stu-id="a6839-232">Teams users can also perform the following activities:</span></span>

* <span data-ttu-id="a6839-233">Konfigurieren Sie ein Standardübermittlungsformular, das Mitarbeiter für jede Idee übermitteln müssen.</span><span class="sxs-lookup"><span data-stu-id="a6839-233">Configure a standard submission form that employees must submit for each idea.</span></span> 
* <span data-ttu-id="a6839-234">Überprüfen und verwalten Sie die Ideen und die Liste der Kampagnen.</span><span class="sxs-lookup"><span data-stu-id="a6839-234">Review and manage the ideas and list of campaigns.</span></span>
* <span data-ttu-id="a6839-235">Ändern und Löschen von Kampagnen.</span><span class="sxs-lookup"><span data-stu-id="a6839-235">Modify and delete campaigns.</span></span>
* <span data-ttu-id="a6839-236">Überprüfen Sie die Ideen der Leiter.</span><span class="sxs-lookup"><span data-stu-id="a6839-236">Review leader boards of ideas.</span></span>
* <span data-ttu-id="a6839-237">Stimmen Sie für priorisierte Ideen, und teilen Sie sie.</span><span class="sxs-lookup"><span data-stu-id="a6839-237">Vote for and share prioritized ideas.</span></span>
* <span data-ttu-id="a6839-238">Übermitteln von Ideen für eine Kampagne.</span><span class="sxs-lookup"><span data-stu-id="a6839-238">Submit ideas for a campaign.</span></span>
* <span data-ttu-id="a6839-239">Sehen Sie sich die Idee eines anderen Teammitglieds an.</span><span class="sxs-lookup"><span data-stu-id="a6839-239">View other team member's idea.</span></span>
* <span data-ttu-id="a6839-240">Stimmen Sie über die am häufigsten verwendeten Ideen ab.</span><span class="sxs-lookup"><span data-stu-id="a6839-240">Vote on most liked ideas.</span></span>
* <span data-ttu-id="a6839-241">Überprüfen Sie die Leistung ihrer Ideen im Vergleich zu anderen innerhalb einer Kampagne.</span><span class="sxs-lookup"><span data-stu-id="a6839-241">Review the performance of their ideas compared with others within a campaign.</span></span>

[<span data-ttu-id="a6839-242">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-242">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-employeeideas)

![Verwalten der Kampagnenansicht](../assets/images/employee-ideas-manage-campaigns.png) 

## <a name="e-prescriptions"></a><span data-ttu-id="a6839-244">E-Rezepturen</span><span class="sxs-lookup"><span data-stu-id="a6839-244">E-Prescriptions</span></span> 

<span data-ttu-id="a6839-245">E-Behandlungen ist eine [Power Apps-basierte](/powerapps/maker/canvas-apps/embed-teams-app) App, die Telemedikamente und virtuelle Pflege verbessert, indem der Prozess der Ausgabe von E-Rezepten für Patienten automatisiert wird.</span><span class="sxs-lookup"><span data-stu-id="a6839-245">E-Prescriptions is a [Power Apps](/powerapps/maker/canvas-apps/embed-teams-app) based app that enhances telemedicine and virtual care by automating the process of issuing e-prescriptions to patients.</span></span> <span data-ttu-id="a6839-246">Medizinische Experten können Termine schnell überprüfen, E-Mails generieren und E-Mails mit E-Mails an Patienten direkt innerhalb der Teams-Plattform senden.</span><span class="sxs-lookup"><span data-stu-id="a6839-246">Medical professionals can quickly review appointments, generate e-prescriptions, and send emails with e-prescription attachments to patients directly within the Teams platform.</span></span>

[<span data-ttu-id="a6839-247">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-247">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-eprescription) 

:::row:::
:::column span="2":::
    ![Screenshot der App "E-Verjährungen".](../assets/images/e-prescriptions-app-template.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Screenshot der App "E-Verjährungen".](../assets/images/e-prescriptions-app-template-admin.png)
:::column-end:::
:::row-end:::

## <a name="employee-training"></a><span data-ttu-id="a6839-252">Mitarbeiterschulung</span><span class="sxs-lookup"><span data-stu-id="a6839-252">Employee Training</span></span> 

<span data-ttu-id="a6839-253">Die Mitarbeiterschulung ist eine Microsoft Teams-App, mit der Organisatoren Lern- und Schulungsereignisse für Ihre Organisation auf einfache Weise veröffentlichen, nachverfolgen und bewerben können.</span><span class="sxs-lookup"><span data-stu-id="a6839-253">Employee training is a Microsoft Teams app that enables organizers to easily publish, track, and promote learning and training events for your organization.</span></span>  <span data-ttu-id="a6839-254">Mit der App können Ereignisplaner Erinnerungen und Benachrichtigungen an Ereignisempfänger senden, und Mitarbeiter können auf Interesse an bevorstehenden Ereignissen hinweisen, über aktuelle Ereignisse auf dem Laufenden bleiben und Ereignisdetails mit Kollegen über die Teams Messaging-Erweiterung teilen.</span><span class="sxs-lookup"><span data-stu-id="a6839-254">With the app, event planners can send reminders and notifications to event registrants and employees can indicate interest in upcoming events, stay updated on current events, and share event details with colleagues through the Teams messaging extension.</span></span>

[<span data-ttu-id="a6839-255">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-255">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-employeetraining)

:::row:::
:::column span="2":::
    <span data-ttu-id="a6839-256">**Anzeigen von Schulungsereignissen** ![ für Mitarbeiter Abbildung der Registerkarte "Mitarbeiterschulung"](../assets/images/employee-training-discover-tab.png)</span><span class="sxs-lookup"><span data-stu-id="a6839-256">**View employee training events** ![Employee training tab image](../assets/images/employee-training-discover-tab.png)</span></span>  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    <span data-ttu-id="a6839-257">**Erstellen eines Mitarbeiterschulungsereignisses** ![ Formular zum Erstellen eines Ereignisses für Mitarbeiterschulungen](../assets/images/employee-training-create-event.jpg)</span><span class="sxs-lookup"><span data-stu-id="a6839-257">**Create employee training event** ![Employee training create event form](../assets/images/employee-training-create-event.jpg)</span></span>
:::column-end:::
:::row-end:::

## <a name="expert-finder"></a><span data-ttu-id="a6839-258">Expertensuche</span><span class="sxs-lookup"><span data-stu-id="a6839-258">Expert Finder</span></span>

<span data-ttu-id="a6839-259">Expert Finder ist ein [Microsoft Teams Bot,](../bots/what-are-bots.md) der bestimmte Organisationsmitglieder basierend auf ihren Fähigkeiten, Interessen und Bildungsattributen identifiziert.</span><span class="sxs-lookup"><span data-stu-id="a6839-259">Expert Finder is a [Microsoft Teams bot](../bots/what-are-bots.md) that identifies specific organization members based on their skills, interests, and education attributes.</span></span> <span data-ttu-id="a6839-260">Mitglieder finden Experten innerhalb einer Organisation, die mit einer Stichwortsuche von Azure Active Directory Benutzerprofilen übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="a6839-260">Members find experts within an organization that match a keyword search of Azure Active Directory user profiles.</span></span>

[<span data-ttu-id="a6839-261">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-261">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-expertfinder)

![Demo zu Suchergebnissen für Expertensuche](../assets/images/expert-finder.png)

## <a name="faq-plus"></a><span data-ttu-id="a6839-263">FAQ Plus</span><span class="sxs-lookup"><span data-stu-id="a6839-263">FAQ Plus</span></span>

<span data-ttu-id="a6839-264">Unterhaltungs-F&A-Bots sind eine einfache Möglichkeit, Antworten auf häufig gestellte Fragen von Benutzern bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="a6839-264">Conversational Q&A bots are an easy way to provide answers to frequently asked questions by users.</span></span> <span data-ttu-id="a6839-265">Die meisten Bots können jedoch nicht auf sinnvolle Weise mit Benutzern interagieren, da sich kein Menschen in der Schleife befindet, wenn der Bot fehlschlägt.</span><span class="sxs-lookup"><span data-stu-id="a6839-265">But, most bots fail to engage with users in meaningful way because there is no human in the loop when the bot fails.</span></span> <span data-ttu-id="a6839-266">Faq bot is a friendly Q&A bot that brings a human in the loop when it is unable to help.</span><span class="sxs-lookup"><span data-stu-id="a6839-266">FAQ bot is a friendly Q&A bot that brings a human in the loop when it is unable to help.</span></span> <span data-ttu-id="a6839-267">Man kann dem Bot eine Frage stellen, und der Bot antwortet mit einer Antwort, wenn er in der Wissensdatenbank enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="a6839-267">One can ask the bot a question and the bot responds with an answer if it is contained in the knowledge base.</span></span> <span data-ttu-id="a6839-268">Wenn dies nicht der Fall ist, ermöglicht der Bot dem Benutzer, eine Abfrage zu übermitteln, die dann in ein vorkonfiguriertes Team von Experten gepostet wird, die zur Unterstützung beitragen, indem sie auf die Benachrichtigungen innerhalb des Teams selbst reagieren.</span><span class="sxs-lookup"><span data-stu-id="a6839-268">If not, the bot allows the user to submit a query which then gets posted to a pre-configured team of experts who help to provide support by acting upon the notifications from within the team itself.</span></span>

> [!NOTE]
> <span data-ttu-id="a6839-269">Die neueste Version von **FAQ Plus** unterstützt verbesserte Q&A-Lösungen, indem ein Expertenteam folgende Aufgaben ausführen kann:</span><span class="sxs-lookup"><span data-stu-id="a6839-269">The latest release of **FAQ Plus** supports improved Q&A resolutions by enabling a team of experts to complete the following:</span></span>
>
> <span data-ttu-id="a6839-270">&#x2714; Hinzufügen eines neuen Q-&As direkt zur Knowledge Base mithilfe von Nachrichtenerweiterungen.</span><span class="sxs-lookup"><span data-stu-id="a6839-270">&#x2714; Add new Q&As directly to the knowledge base using message extensions.</span></span>
>
> <span data-ttu-id="a6839-271">&#x2714; Bearbeiten und Löschen von Q-&A-Paaren, die von einem Bot hinzugefügt wurden.</span><span class="sxs-lookup"><span data-stu-id="a6839-271">&#x2714; Edit and delete Q&A pairs added by a bot.</span></span>
>
> <span data-ttu-id="a6839-272">&#x2714; Nachverfolgen des Überarbeitungsverlaufs von Q&As.</span><span class="sxs-lookup"><span data-stu-id="a6839-272">&#x2714; Track the revision history of Q&As.</span></span>
>
> <span data-ttu-id="a6839-273">&#x2714; Konfigurieren sie eine Antwort mit zusätzlichen Details, die als [adaptive Karte](../task-modules-and-cards/cards/cards-reference.md#adaptive-card)angezeigt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="a6839-273">&#x2714; Configure an answer with additional details to display as an [Adaptive Card](../task-modules-and-cards/cards/cards-reference.md#adaptive-card).</span></span>
>
[<span data-ttu-id="a6839-274">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-274">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-faqplusv2)

![FAQ Plus GIF](../assets/images/FAQPlusEndUser.gif)

## <a name="get-support-app"></a><span data-ttu-id="a6839-276">Support-App abrufen</span><span class="sxs-lookup"><span data-stu-id="a6839-276">Get Support App</span></span>

<span data-ttu-id="a6839-277">Die App "Support abrufen" wird von Organisationen verwendet, die Microsoft Teams verwenden, um es allen Benutzern zu ermöglichen, Unterstützung von Vorgesetzten anzufordern.</span><span class="sxs-lookup"><span data-stu-id="a6839-277">The Get Support app is used by organizations that are using Microsoft Teams, to enable any set of users to request assistance from supervisors.</span></span> <span data-ttu-id="a6839-278">Diese App enthält die folgenden Features:</span><span class="sxs-lookup"><span data-stu-id="a6839-278">This app includes the following features:</span></span>
* <span data-ttu-id="a6839-279">Anfordern von Unterstützung für verschiedene Kategorien aus einer Power App.</span><span class="sxs-lookup"><span data-stu-id="a6839-279">Requesting assistance on different categories from a Power App.</span></span>
* <span data-ttu-id="a6839-280">Benachrichtigungen, die an Anforderer gesendet werden und sie darüber informieren, wer zugewiesen ist.</span><span class="sxs-lookup"><span data-stu-id="a6839-280">Notifications sent to requestors informing them of who is assigned.</span></span>
* <span data-ttu-id="a6839-281">Benachrichtigungen, die an zugewiesene Vorgesetzte gesendet werden und sie darüber informieren, wer Unterstützung benötigt.</span><span class="sxs-lookup"><span data-stu-id="a6839-281">Notifications sent to assigned supervisors informing them of who needs assistance.</span></span> 
* <span data-ttu-id="a6839-282">Analysieren von Eskalationen und Mustern in SharePoint und Power BI.</span><span class="sxs-lookup"><span data-stu-id="a6839-282">Analyzing escalations and patterns in SharePoint and Power BI.</span></span>

[<span data-ttu-id="a6839-283">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-283">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-app-get-support/)

![Support gif erhalten](../assets/images/get-support.gif)

## <a name="goal-tracker"></a><span data-ttu-id="a6839-285">Zielverfolgung</span><span class="sxs-lookup"><span data-stu-id="a6839-285">Goal Tracker</span></span>

<span data-ttu-id="a6839-286">Die Zielverfolgungs-App ist eine umfassende Lösung für Ihre Organisation, um die Festlegung von Zielen, das Beobachten des Fortschritts und das Bestätigen des Erfolgs innerhalb Microsoft Teams zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="a6839-286">The Goal Tracker app is a comprehensive solution for your organization to support establishing goals, observing progress, and acknowledging success within Microsoft Teams.</span></span> <span data-ttu-id="a6839-287">Die App ermöglicht es Benutzern, Ziele auf beruflicher, persönlicher und Teamebene festzulegen, nachzuverfolgen und zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="a6839-287">The app enables users to set, track, and update objectives on a professional, personal, and team level.</span></span> <span data-ttu-id="a6839-288">Teammitglieder erhalten auch rechtzeitig Erinnerungen und Statusaktualisierungen, um konzentriert zu bleiben und auf dem Laufenden zu bleiben.</span><span class="sxs-lookup"><span data-stu-id="a6839-288">Team members also receive timely reminders and status updates to remain focused and stay on track.</span></span>

[<span data-ttu-id="a6839-289">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-289">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-app-goaltracker)

:::row:::
  :::column span="2":::
    ![Ziele festlegen](../assets/images/goal-tracker-set-goals-view.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Anzeigen festgelegter Ziele](../assets/images/goal-tracker-your-goals-view.png)
:::column-end:::
:::row-end:::

## <a name="great-ideas"></a><span data-ttu-id="a6839-292">Großartige Ideen</span><span class="sxs-lookup"><span data-stu-id="a6839-292">Great Ideas</span></span>

<span data-ttu-id="a6839-293">Die Great Ideas-App unterstützt und unterstützt Innovation und Kreativität in Ihrer Organisation.</span><span class="sxs-lookup"><span data-stu-id="a6839-293">The Great Ideas app supports and empowers innovation and creativity within your organization.</span></span> <span data-ttu-id="a6839-294">Die App ermöglicht Es Ihren Mitarbeitern, Ideen mit Kollegen und Führungskräften zu teilen, neue Übermittlungen zu entdecken, Beiträge für Peer-Berücksichtigung ins Blickpunkt zu setzen und ihre Stimme für die besten Vorschläge innerhalb Microsoft Teams zu geben.</span><span class="sxs-lookup"><span data-stu-id="a6839-294">The app enables your employees to share ideas with colleagues and leadership, discover new submissions, spotlight contributions for peer consideration, and cast their vote for the best proposals within Microsoft Teams.</span></span>

[<span data-ttu-id="a6839-295">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-295">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-greatideas)

:::row:::
  :::column span="2":::
    ![Eingereichte Ideen anzeigen](../assets/images/great-ideas-all-view.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Ideen anzeigen](../assets/images/great-ideas-digest-view.png)
:::column-end:::
:::row-end:::

## <a name="group-activities"></a><span data-ttu-id="a6839-298">Gruppenaktivitäten</span><span class="sxs-lookup"><span data-stu-id="a6839-298">Group Activities</span></span>

<span data-ttu-id="a6839-299">"Gruppenaktivitäten" ist eine Microsoft Teams-App, die es Teambesitzern erleichtert, schnell Aktivitätsgruppen zu erstellen und Workflows für die Zusammenarbeit im Kontext von Microsoft Teams zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="a6839-299">Group Activities is a Microsoft Teams app that makes it easy for team owners to quickly create activity groups and manage collaboration workflows within the context of Microsoft Teams.</span></span> <span data-ttu-id="a6839-300">Aktivitätsautoren können Aktivitäten erstellen, Teammitglieder nach dem Zufallsprinzip in Gruppen verteilen und optional vom Bot Erinnerungen senden lassen, bis die Aktivitäten abgeschlossen sind.</span><span class="sxs-lookup"><span data-stu-id="a6839-300">Activity authors are enabled to create activities, randomly distribute team members in groups, and optionally have the bot send reminders until activities are complete.</span></span>

[<span data-ttu-id="a6839-301">Get it on GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-301">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-groupactivities)

:::row:::
  :::column span="2":::
    ![Liste der Gruppenaktivitäten in Teams](../assets/images/group-activities-1.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Benachrichtigung über Gruppenaktivität in einem Kanal](../assets/images/group-activities-2.png)
:::column-end:::
:::row-end:::

## <a name="group-connect-9734"></a><span data-ttu-id="a6839-304">Gruppen-Verbinden &#9734;</span><span class="sxs-lookup"><span data-stu-id="a6839-304">Group Connect &#9734;</span></span>

<span data-ttu-id="a6839-305">Gruppen-Verbinden ist eine Microsoft Teams-App, die Organisationsmitgliedern hilft, Mitarbeitergruppen zu finden und informationen zu finden, die für Mitarbeitergruppen relevant sind.</span><span class="sxs-lookup"><span data-stu-id="a6839-305">Group Connect is a Microsoft Teams app that helps organization members discover employee groups and find information relevant to employee groups.</span></span> <span data-ttu-id="a6839-306">Die App ist mit umfangreichen Funktionen für Organisationsleiter integriert, um mit ihren Mitarbeitern über Gruppen, Ereignisse und Ressourcen zu kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="a6839-306">The app comes built-in with rich capabilities for organization leaders to communicate with their employees regarding groups, events, and resources.</span></span> <span data-ttu-id="a6839-307">Die Gruppen-Verbinden-App gleicht auch Gruppenmitglieder in der gewünschten Häufigkeit miteinander ab, um netzwerke und den Innerbetrieb innerhalb einer Gruppe zu fördern.</span><span class="sxs-lookup"><span data-stu-id="a6839-307">The Group Connect app also matches group members with each other at their desired frequency to encourage networking and cohesion within a group.</span></span> <span data-ttu-id="a6839-308">Weitere Informationen dazu, wie Sie die Gruppen-Verbinden-App nutzen können, um Mitarbeitergruppen in Ihrer Organisation zu unterstützen, finden Sie in der App auf GitHub.</span><span class="sxs-lookup"><span data-stu-id="a6839-308">For more information on how you can leverage the Group Connect app to help employee groups foster within your organization, see the app on GitHub.</span></span>

[<span data-ttu-id="a6839-309">Get it on GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-309">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-groupconnect)

![Ermitteln von D-&-I-Gruppen](https://github.com/OfficeDev/microsoft-teams-apps-diversityandinclusion/wiki/Images/temp_group_connect_landing.png)

## <a name="grow-your-skills"></a><span data-ttu-id="a6839-311">Erweitern Sie Ihre Fähigkeiten</span><span class="sxs-lookup"><span data-stu-id="a6839-311">Grow Your Skills</span></span>

<span data-ttu-id="a6839-312">Die App "Ihre Fähigkeiten erweitern" unterstützt das professionelle Wachstum und die Entwicklung, indem mitarbeiter in die Lage versetzt werden, an ergänzenden Projekten für Ihre Organisation mitzuwirken und gleichzeitig neue Fähigkeiten zu erlernen.</span><span class="sxs-lookup"><span data-stu-id="a6839-312">The Grow Your Skills app supports professional growth and development by enabling employees to contribute to supplemental projects for your organization while simultaneously learning new skills.</span></span> <span data-ttu-id="a6839-313">Mitarbeiter können die App verwenden, um Möglichkeiten zu finden, die ihren Interessen entsprechen, eine sinnvolle Zusammenarbeit mit Kollegen zu genießen und neue Erfahrungs- und Leistungsniveaus in der Teams Umgebung zu erwerben.</span><span class="sxs-lookup"><span data-stu-id="a6839-313">Employees can use the app to locate opportunities that meet their interests, enjoy meaningful collaboration with peers, and acquire new levels of expertise and capabilities, all within the Teams environment.</span></span>

[<span data-ttu-id="a6839-314">Get it on GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-314">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-growyourskills)

:::row:::
  :::column span="2":::
    ![Ansicht "Verfügbare Projekte"](../assets/images/grow-your-skills-all-projects-view.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Ansicht "Erworbene Fähigkeiten" des Betrachters](../assets/images/grow-your-skills-acquired-skills-view.png)
:::column-end:::
:::row-end:::

## <a name="hr-support"></a><span data-ttu-id="a6839-317">HR Support</span><span class="sxs-lookup"><span data-stu-id="a6839-317">HR Support</span></span>

<span data-ttu-id="a6839-318">Der HR-Support-Bot ist ein freundlicher Q-&Ein Bot, der einen Support-Experten oder Experten aus dem HR-Team in die Schleife bringt, wenn er nicht helfen kann.</span><span class="sxs-lookup"><span data-stu-id="a6839-318">HR Support bot is a friendly Q&A bot that brings a support professional or expert from the HR team in the loop when it is unable to help.</span></span> <span data-ttu-id="a6839-319">Man kann dem Bot eine Frage stellen, und der Bot antwortet mit einer Antwort, wenn er in der Wissensdatenbank enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="a6839-319">One can ask the bot a question and the bot responds with an answer if it is contained in the knowledge base.</span></span> <span data-ttu-id="a6839-320">Wenn dies nicht der Fall ist, ermöglicht der Bot dem Benutzer, eine Abfrage zu übermitteln, die dann in einem vorkonfigurierten Team von Experten veröffentlicht wird, die bei der Unterstützung helfen, indem sie auf die Benachrichtigungen innerhalb ihres Teams selbst reagieren.</span><span class="sxs-lookup"><span data-stu-id="a6839-320">If not, the bot allows the user to submit a query which then gets posted in a pre-configured team of experts who are help to provide support by acting upon the notifications from within their team itself.</span></span> <span data-ttu-id="a6839-321">Darüber hinaus schlägt der Bot Links zu empfohlenen HR-Richtlinien oder Fragen vor, indem er nach vorkonfigurierten Tags in der Frage sucht.</span><span class="sxs-lookup"><span data-stu-id="a6839-321">Additionally, the bot suggests links to recommended HR policies or questions by searching for pre-configured tags in the question.</span></span> <span data-ttu-id="a6839-322">Diese Kacheln finden Sie auf der zugeordneten Registerkarte als Kurzübersicht.</span><span class="sxs-lookup"><span data-stu-id="a6839-322">These tiles are found in the associated tab as a quick reference.</span></span> <span data-ttu-id="a6839-323">Der Personalsupport eignet sich gut für eine leichte Q-&A und bietet schnelle Unterstützung beim Starten neuer Projekte oder Initiativen in der Organisation.</span><span class="sxs-lookup"><span data-stu-id="a6839-323">HR Support works well for light weight Q&A and to provide quick support when launching new projects or initiatives in the organization.</span></span>

[<span data-ttu-id="a6839-324">Get it on GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-324">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-hrsupport-app)

![HR Support](../assets/images/expert-user.png)

## <a name="icebreaker"></a><span data-ttu-id="a6839-326">Icebreaker</span><span class="sxs-lookup"><span data-stu-id="a6839-326">Icebreaker</span></span>

<span data-ttu-id="a6839-327">Icebreaker ist ein [Microsoft Teams Bot,](../bots/what-are-bots.md) der Ihrem Team hilft, sich näher zu bringen, indem jede Woche zwei zufällige Teammitglieder zusammenkommen, um sich zu treffen.</span><span class="sxs-lookup"><span data-stu-id="a6839-327">Icebreaker is a [Microsoft Teams bot](../bots/what-are-bots.md) that helps your team get closer by pairing two random team members up every week to meet.</span></span> <span data-ttu-id="a6839-328">Der Bot vereinfacht die Planung, indem er automatisch freie Zeiten vorschlägt, die für beide Mitglieder funktionieren.</span><span class="sxs-lookup"><span data-stu-id="a6839-328">The bot makes scheduling easy by automatically suggesting free times that work for both members.</span></span> <span data-ttu-id="a6839-329">Stärken Sie persönliche Verbindungen, und erstellen Sie mit dieser App eine engmaschige Community.</span><span class="sxs-lookup"><span data-stu-id="a6839-329">Strengthen personal connections and build a tightly knit community with this app.</span></span>

<span data-ttu-id="a6839-330">Neben der Förderung persönlicher Verbindungen in Ihrem gesamten Team kann die Icebreaker-App dazu beitragen, interessenbasierte Communitys in Ihrer Organisation zu fördern.</span><span class="sxs-lookup"><span data-stu-id="a6839-330">In addition to encouraging personal connections across your entire team, the Icebreaker app can help cultivate interest-based communities within your organization.</span></span> <span data-ttu-id="a6839-331">Sie können diese App beispielsweise für eine DevOps Interessengruppen verwenden, um Ideen und bewährte Methoden organisch in Ihrer Organisation zu verteilen.</span><span class="sxs-lookup"><span data-stu-id="a6839-331">For example, you can use this app for a DevOps interest group to help ideas and best practices organically spread across your organization.</span></span>

[<span data-ttu-id="a6839-332">Get it on GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-332">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-icebreaker-app)

![Icebreaker-App](../assets/images/icebreaker.png)

## <a name="incentives"></a><span data-ttu-id="a6839-334">Anreize</span><span class="sxs-lookup"><span data-stu-id="a6839-334">Incentives</span></span>

<span data-ttu-id="a6839-335">Incentives ist eine [Power Apps](/powerapps/maker/canvas-apps/embed-teams-app) Vorlage, die die Beteiligung von Mitarbeitern an bestimmten Aktivitäten wie Schulungen und Change Management-Initiativen verwaltet und verfolgt.</span><span class="sxs-lookup"><span data-stu-id="a6839-335">Incentives is a [Power Apps](/powerapps/maker/canvas-apps/embed-teams-app) template that manages and tracks incentivized employee participation in designated activities, such as trainings and change management initiatives.</span></span> <span data-ttu-id="a6839-336">Administratoren verwenden die App, um festgelegte Aktivitäten einzurichten, Punkte für den Abschluss zuzuweisen und die erforderlichen Berechtigungspunkte für Diebesungen anzugeben.</span><span class="sxs-lookup"><span data-stu-id="a6839-336">Admins use the app to establish designated activities, assign points for completion, and specify required eligibility point levels for rewards.</span></span> <span data-ttu-id="a6839-337">Mitarbeiter verwenden die App, um ihre gesammelten Punkte anzuzeigen und nach Erreichen der Berechtigung einlösbare Preise anzufordern und in Anspruch zu nehmen.</span><span class="sxs-lookup"><span data-stu-id="a6839-337">Employees use the app to view their accumulated points and, upon reaching eligibility, request and claim redeemable rewards.</span></span>

[<span data-ttu-id="a6839-338">Get it on GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-338">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-incentives)

![Incentives-App-Demo](../assets/images/incentives-app.png)

## <a name="incident-reporter"></a><span data-ttu-id="a6839-340">Vorfallbericht</span><span class="sxs-lookup"><span data-stu-id="a6839-340">Incident Reporter</span></span>

<span data-ttu-id="a6839-341">Incident Reporter ist ein [Microsoft Teams Bot,](../bots/what-are-bots.md) der die Verwaltung von Vorfällen in Ihrer Organisation optimiert.</span><span class="sxs-lookup"><span data-stu-id="a6839-341">Incident Reporter is a [Microsoft Teams bot](../bots/what-are-bots.md)  that optimizes the management of incidents in your organization.</span></span> <span data-ttu-id="a6839-342">Der Bot erleichtert die automatisierte Sammlung von Vorfalldaten, angepasste Vorfallberichte, relevante Benachrichtigungen von Beteiligten und die End-to-End-Vorfallverfolgung.</span><span class="sxs-lookup"><span data-stu-id="a6839-342">The bot facilitates automated incident data collection, customized incident reports, relevant stakeholder notifications, and end-to-end incident tracking.</span></span>

[<span data-ttu-id="a6839-343">Get it on GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-343">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-incidentreport)

:::row:::
  :::column span="2":::
    ![Bereichsansicht für Vorfallberichtsgruppen](../assets/images/incident-reporter-02.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Persönliche Bereichsansicht des Vorfallberichts](../assets/images/incident-reporter-01.jpg)
:::column-end:::
:::row-end:::

## <a name="inspection"></a><span data-ttu-id="a6839-346">Inspektion</span><span class="sxs-lookup"><span data-stu-id="a6839-346">Inspection</span></span> 

 <span data-ttu-id="a6839-347">Bei der Überprüfung handelt es sich um eine Microsoft Teams-App, mit der Mitarbeiter in Service und Produktion alles überprüfen können, von Standorten bis hin zu Objekten und Geräten.</span><span class="sxs-lookup"><span data-stu-id="a6839-347">Inspection is a Microsoft Teams app that enables front line workers to inspect anything from  locations to assets and equipments.</span></span> <span data-ttu-id="a6839-348">Beispielsweise ein Einzelhandelsgeschäft, eine Produktionsanlage oder Ein- und Maschinen.</span><span class="sxs-lookup"><span data-stu-id="a6839-348">For example, a retail store, manufacturing plant, or vehicles and machines.</span></span> <span data-ttu-id="a6839-349">Es gibt zwei Apps in dieser Lösung, die jeweils für unterschiedliche Benutzertypen vorgesehen sind.</span><span class="sxs-lookup"><span data-stu-id="a6839-349">There are two apps in this solution, each intended for different types of users.</span></span>

<span data-ttu-id="a6839-350">Die App ermöglicht es Den Mitarbeitern der Ersten Reihe, ein Objekt oder einen Bereich zu überprüfen, die Qualität von Produkten und Diensten zu verwalten oder die Sicherheit am Arbeitsplatz zu gewährleisten.</span><span class="sxs-lookup"><span data-stu-id="a6839-350">The app empowers the front line workers to inspect an asset or area, to manage quality of products and services, or maintain safety at workplace.</span></span> <span data-ttu-id="a6839-351">Es erleichtert die Kommunikation zwischen Teammitgliedern, um Probleme zu beheben, die während der Überprüfung gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="a6839-351">It facilitates communication between team members to address issues found during inspection.</span></span> <span data-ttu-id="a6839-352">Die App stellt einfache Berichte für Manager bereit, um die Problembehebung zu beschleunigen und Trends hervorzuheben.</span><span class="sxs-lookup"><span data-stu-id="a6839-352">The app provides simple reports for managers to expedite issue resolution and highlight trends.</span></span>

[<span data-ttu-id="a6839-353">Get it on GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-353">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-inspection)

 ![Übersicht über die Überprüfung](../assets/images/inspection-app.png)  


## <a name="issue-reporting"></a><span data-ttu-id="a6839-355">Problemberichterstattung</span><span class="sxs-lookup"><span data-stu-id="a6839-355">Issue Reporting</span></span>

<span data-ttu-id="a6839-356">Die Problemberichterstattungs-App ermöglicht es Mitarbeitern und Vorgesetzten, Probleme zu lösen und zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="a6839-356">The Issue Reporting app empowers the employees and managers to raise and manage issues.</span></span> <span data-ttu-id="a6839-357">Es besteht aus zwei Apps, der Problemberichterstattungs-App zum Melden von Problemen und der App "Probleme verwalten" zum Verwalten von Problemen.</span><span class="sxs-lookup"><span data-stu-id="a6839-357">It consists of two apps, Issue reporting app for reporting issues and Manage Issues app for managing issues.</span></span>

<span data-ttu-id="a6839-358">Die Teammanager verwenden die App "Probleme verwalten", um die App-Erfahrung zu konfigurieren, einschließlich des Kanals, in dem Microsoft Teams Nachrichten und Planner-Aufgaben von der App erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="a6839-358">The team managers use the Manage Issues app to configure the app experience, including the channel in which Microsoft Teams messages and Planner tasks are created by the app.</span></span> <span data-ttu-id="a6839-359">Manager verwenden die App auch, um Vorlagenformulare zu erstellen, um Details zu sammeln, wenn ein Benutzer ein Problem meldet.</span><span class="sxs-lookup"><span data-stu-id="a6839-359">Managers also use the app to create template forms to collect details when a user reports an issue.</span></span> <span data-ttu-id="a6839-360">Beispiel: Überprüfen, Bearbeiten oder Löschen von Vorlagenformularen für Probleme.</span><span class="sxs-lookup"><span data-stu-id="a6839-360">For example, review, edit, or delete issue template forms.</span></span> <span data-ttu-id="a6839-361">Die App wird auch verwendet, um Teamprobleme zu überprüfen, den Problemverlauf zu melden und die Problemlösung effizient zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="a6839-361">The app is also used to review team issues, report on issue history, and efficiently manage issue resolution.</span></span>

<span data-ttu-id="a6839-362">Die Mitarbeiter verwenden die Problemberichterstattungs-App, um Probleme und Details zu protokollieren, die zur Behebung erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="a6839-362">The employees use the Issue reporting app to log issues and details required to resolve them.</span></span> <span data-ttu-id="a6839-363">Die App wird auch verwendet, um vorhandene Probleme zu ändern und zu beheben und eine allgemeine Übersicht über Einzelne oder Teamprobleme zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="a6839-363">The app is also used to modify and resolve existing issues and get a high-level view of individual or team issues.</span></span>

[<span data-ttu-id="a6839-364">Get it on GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-364">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-issuereporting)

![Teamansicht für Problemberichterstattung](../assets/images/issue-reporting-team-view.png)  

## <a name="new-employee-onboarding"></a><span data-ttu-id="a6839-366">Onboarding neuer Mitarbeiter</span><span class="sxs-lookup"><span data-stu-id="a6839-366">New Employee Onboarding</span></span> 

<span data-ttu-id="a6839-367">Das Onboarding neuer Mitarbeiter ist eine integrierte Microsoft Teams und [SharePoint Onboarding-Lösung](https://lookbook.microsoft.com/details/75e60a32-9849-4ed4-b83e-b2b08983ad19) für neue Mitarbeiter, die es Ihrer Organisation ermöglicht, mitarbeitern auf ihrer Neueinstellungen-Reise eine konsistente, qualitativ hochwertige Onboarding-Erfahrung zu bieten.</span><span class="sxs-lookup"><span data-stu-id="a6839-367">New Employee Onboarding is an integrated Microsoft Teams and [SharePoint New Employee Onboarding Solution](https://lookbook.microsoft.com/details/75e60a32-9849-4ed4-b83e-b2b08983ad19) that enables your organization to provide a consistent, high-quality onboarding experience for employees on their new-hire journey.</span></span> <span data-ttu-id="a6839-368">Die App wird von Personalteams und Einstellungsmanagern verwendet, um relevante Informationen während des Orientierungs- und Einführungsprozesses bereitzustellen, und von Neueinstellungen, um Feedback zu teilen, Einführungen bereitzustellen und Onboarding-Aufgaben auszuführen.</span><span class="sxs-lookup"><span data-stu-id="a6839-368">The app is used by human resource teams and hiring managers to provide relevant information throughout the orientation and induction process and by new hires to share feedback, provide introductions, and complete onboarding tasks.</span></span>

[<span data-ttu-id="a6839-369">Get it on GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-369">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-newemployeeonboarding)

:::row:::
  :::column span="2":::
    <span data-ttu-id="a6839-370">Willkommenskarte für **neue Mitarbeiter** ![ Abbildung der Willkommenskarte für neue Mitarbeiter](../assets/images/new-employee-welcome-card.png)</span><span class="sxs-lookup"><span data-stu-id="a6839-370">**New employee welcome card** ![Image of new employee welcome card](../assets/images/new-employee-welcome-card.png)</span></span>
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    <span data-ttu-id="a6839-371">Prüfliste für **neue Mitarbeiter** ![ Abbildung der Checkliste für neue Mitarbeiter](../assets/images/new-employee-checklist.png)</span><span class="sxs-lookup"><span data-stu-id="a6839-371">**New employee checklist** ![Image of new employee checklist](../assets/images/new-employee-checklist.png)</span></span>  
:::column-end:::
:::row-end:::

## <a name="open-badges"></a><span data-ttu-id="a6839-372">Offene Badges</span><span class="sxs-lookup"><span data-stu-id="a6839-372">Open Badges</span></span>

<span data-ttu-id="a6839-373">Open Badges ist eine Microsoft Teams-App, die es Einzelpersonen ermöglicht, digitale Lernanmeldeinformations-Badges im Teams Kontext zu erwerben und sie überall zu teilen.</span><span class="sxs-lookup"><span data-stu-id="a6839-373">Open Badges is a Microsoft Teams app that enables individuals to earn digital learning credential badges within the Teams context and share them everywhere.</span></span> <span data-ttu-id="a6839-374">Mithilfe der Funktionen der Externen-Zertifizierungsstelle für digitale Badges, [Badgr,](https://badgr.org/)werden die ausgestellten Badges im Badgr-Profil eines Empfängers aufgezeichnet und stehen zur Verfügung, um ein umfassendes Bild der Lebenszeit-Lernerfahrungen zu erstellen und zu teilen.</span><span class="sxs-lookup"><span data-stu-id="a6839-374">Using capabilities from the third-party digital badge issuing authority, [Badgr](https://badgr.org/), awarded badges are recorded in a recipient's Badgr profile and available to build and share a rich picture of lifetime learning journeys.</span></span>

[<span data-ttu-id="a6839-375">Get it on GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-375">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-openbadges)

:::row:::
  :::column span="2":::
    ![Abbildung der verfügbaren Badges](../assets/images/open-badges-1.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Ansicht "Badges"](../assets/images/open-badges-2.png)
:::column-end:::
:::row-end:::

## <a name="poll"></a><span data-ttu-id="a6839-378">Umfrage</span><span class="sxs-lookup"><span data-stu-id="a6839-378">Poll</span></span> 

<span data-ttu-id="a6839-379">Poll ist eine benutzerdefinierte Microsoft Teams [Messaging-Erweiterungs-App,](../messaging-extensions/what-are-messaging-extensions.md) mit der Sie schnell Umfragen in einem Chat oder Kanal erstellen und senden können, um Team-Ansichten und -Einstellungen zu erfassen.</span><span class="sxs-lookup"><span data-stu-id="a6839-379">Poll is a custom Microsoft Teams [messaging extension](../messaging-extensions/what-are-messaging-extensions.md) app that enables you to quickly create and send polls in a chat or a channel to gather team opinions and preferences.</span></span> <span data-ttu-id="a6839-380">Die App wird auf allen Teams Plattformclients unterstützt, z. B. Desktop, Browser, iOS und Android, und ist als Teil Ihres Microsoft 365-Abonnements bereit für die Bereitstellung.</span><span class="sxs-lookup"><span data-stu-id="a6839-380">The app is supported across all Teams platform clients, such as desktop, browser, iOS, and Android and is ready for deployment as part of your Microsoft 365 subscription.</span></span>

[<span data-ttu-id="a6839-381">Get it on GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-381">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-poll-app)

:::row:::
  :::column span="1":::
    ![Umfrage in Teams Ansicht erstellen](../assets/images/poll-app-template-compose-view.gif)  
:::column-end:::
:::row-end:::

## <a name="quick-responses"></a><span data-ttu-id="a6839-383">Schnelle Antworten</span><span class="sxs-lookup"><span data-stu-id="a6839-383">Quick Responses</span></span>

<span data-ttu-id="a6839-384">Quick Responses ist eine Microsoft Teams-App, die eine robuste Lösung zur effektiven Beantwortung häufig gestellter Fragen von Benutzern bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="a6839-384">Quick Responses is a Microsoft Teams app that delivers a robust solution for effectively answering users' commonly asked questions FAQs.</span></span> <span data-ttu-id="a6839-385">Anstatt jede Abfrage manuell und kontinuierlich zu wiederholen, erstellt die App eine Bibliothek mit Antworten für eine interaktive Benutzeroberfläche über Teams [Messaging-Erweiterungen.](../messaging-extensions/what-are-messaging-extensions.md)</span><span class="sxs-lookup"><span data-stu-id="a6839-385">Instead of answering each query manually and continuously repeating information, the app builds a library of responses for an interactive user experience through Teams [messaging extensions](../messaging-extensions/what-are-messaging-extensions.md).</span></span>

[<span data-ttu-id="a6839-386">Get it on GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-386">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-quickresponses)

![Beispielansicht der Antworten](../assets/images/quick-responses.png)

## <a name="quiz--9734"></a><span data-ttu-id="a6839-388">Quiz &#9734;</span><span class="sxs-lookup"><span data-stu-id="a6839-388">Quiz  &#9734;</span></span>

<span data-ttu-id="a6839-389">Quiz ist eine benutzerdefinierte [Teams Messaging-Erweiterungs-App,](../messaging-extensions/what-are-messaging-extensions.md) mit der Sie ein Quiz innerhalb eines Chats oder Kanals für die Wissensüberprüfung und sofortige Ergebnisse erstellen können.</span><span class="sxs-lookup"><span data-stu-id="a6839-389">Quiz is a custom [Teams messaging extension](../messaging-extensions/what-are-messaging-extensions.md) app that enables you to create a quiz within a chat or a channel for knowledge check and instantaneous results.</span></span> <span data-ttu-id="a6839-390">Sie können Quiz für Kurs- und Offlineprüfungen, die Wissensüberprüfung innerhalb eines Teams und für unterhaltungsbezogene Quizfragen innerhalb eines Teams verwenden.</span><span class="sxs-lookup"><span data-stu-id="a6839-390">You can use Quiz for, In-class and offline exams, Knowledge check within team, and for fun quizzes within a team.</span></span> <span data-ttu-id="a6839-391">Quiz-App wird auf mehreren Plattformen unterstützt, z. B. Teams Desktop-, Browser-, iOS- und Android-Clients.</span><span class="sxs-lookup"><span data-stu-id="a6839-391">Quiz app is supported across multiple platforms, such as Teams desktop, browser, iOS, and Android clients.</span></span> <span data-ttu-id="a6839-392">Diese App ist bereit für die Bereitstellung als Teil Ihres vorhandenen Microsoft 365-Abonnements.</span><span class="sxs-lookup"><span data-stu-id="a6839-392">This app is ready for deployment as part of your existing Microsoft 365 subscription.</span></span>

[<span data-ttu-id="a6839-393">Get it on GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-393">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-quiz)

:::row:::
  :::column span="1":::
    ![Quiz in Teams Ansicht erstellen](../assets/images/quiz-app-template-compose-view.gif)  
:::column-end:::
:::row-end:::

## <a name="rapid-assist"></a><span data-ttu-id="a6839-395">Rapid Assist</span><span class="sxs-lookup"><span data-stu-id="a6839-395">Rapid Assist</span></span>

<span data-ttu-id="a6839-396">Rapid Assist ist eine Microsoft [Power Platform-basierte](https://powerapps.microsoft.com/blog/now-in-preview-customize-teams-with-built-in-power-platform-capabilities/) App, die es Mitarbeitern mit Kunden ermöglicht, sich schnell mit den Experten zu verbinden, um schnelle Antworten zu erhalten, nach Informationen zu suchen, offene Anfragen zu verfolgen und Experten zu ermöglichen, Benachrichtigungen zu erhalten, um schnell einen Anruf zu erhalten, um Fragen zu beantworten.</span><span class="sxs-lookup"><span data-stu-id="a6839-396">Rapid Assist is a Microsoft [Power Platform](https://powerapps.microsoft.com/blog/now-in-preview-customize-teams-with-built-in-power-platform-capabilities/) based app that allows customer facing associates to rapidly connect with the experts to get quick answers, search for information, follow up open requests, and allow experts to receive notifications to quickly get on a call to help answer questions.</span></span> <span data-ttu-id="a6839-397">Die App, die mit Microsoft [Power Apps](/powerapps/powerapps-overview) und [Power Automate](/power-automate/getting-started)erstellt wurde, ist tief in Microsoft Teams integriert, damit Organisationen Mitarbeiter in Service und Produktion problemlos mit Unternehmenskontakten verbinden können, um Kundenabfragen zu lösen und eine hervorragende Kundenerfahrung zu bieten.</span><span class="sxs-lookup"><span data-stu-id="a6839-397">The app built using Microsoft [Power Apps](/powerapps/powerapps-overview) and [Power Automate](/power-automate/getting-started), deeply integrates with Microsoft Teams to enable organizations to easily connect frontline workers with corporate liaisons to resolve customer queries and deliver a great customer experience.</span></span> 

[<span data-ttu-id="a6839-398">Get it on GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-398">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-rapid-assist)

:::row:::
   :::column span="":::
     ![Oberfläche für Endbenutzeranforderungen](../assets/images/EndUserHome.png)
   :::column-end:::
   :::column span="":::
      ![Ansicht der Expertenanfrage](../assets/images/ExpertViewRequests.png)
   :::column-end:::
:::row-end:::

## <a name="reflect"></a><span data-ttu-id="a6839-401">Spiegeln</span><span class="sxs-lookup"><span data-stu-id="a6839-401">Reflect</span></span> 

<span data-ttu-id="a6839-402">Reflect ist eine benutzerdefinierte Microsoft Teams [Messaging-Erweiterungs-App,](../messaging-extensions/what-are-messaging-extensions.md) die ihren Teammitgliedern eine sichere und inklusive Ressource bietet, um den Zustand ihres gefühlsmäßigen Wohlbefindens mit Kollegen oder Gruppenleitern direkt innerhalb Teams zu teilen.</span><span class="sxs-lookup"><span data-stu-id="a6839-402">Reflect is a custom Microsoft Teams [messaging extension](../messaging-extensions/what-are-messaging-extensions.md) app that provides a safe and inclusive resource for your team members to share the state of their emotional well-being with colleagues or group leaders directly within Teams.</span></span> <span data-ttu-id="a6839-403">Die App ist in Kanal-, Gruppen-, Besprechungs- und 1:1-Chats verfügbar, und die Eincheckantwort ist auf öffentliche, private oder vollständig anonyme Chats festgelegt.</span><span class="sxs-lookup"><span data-stu-id="a6839-403">The app is available in channel, group, meeting, and 1:1 chats and the check-in response is set to public, private-to-sender, or fully anonymous.</span></span>

[<span data-ttu-id="a6839-404">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-404">Get it on GitHub</span></span>](https://github.com/OfficeDev/Microsoft-Teams-App-Reflect)

:::row:::
    :::column:::
    <span data-ttu-id="a6839-405">**Umfrage zum Wohlbefinden**</span><span class="sxs-lookup"><span data-stu-id="a6839-405">**Well-being poll**</span></span>
    
    ![Benutzerumfrage der App wiedergeben](../assets/images/reflect-app-user-poll.png)
    :::column-end:::
:::row-end:::

## <a name="remote-support"></a><span data-ttu-id="a6839-407">Remoteunterstützung</span><span class="sxs-lookup"><span data-stu-id="a6839-407">Remote Support</span></span>

<span data-ttu-id="a6839-408">Remote support is a [Microsoft Teams bot](../bots/what-are-bots.md) that provides a focused interface between support requesters throughout your organization and the internal support team.</span><span class="sxs-lookup"><span data-stu-id="a6839-408">Remote Support is a [Microsoft Teams bot](../bots/what-are-bots.md) that provides a focused interface between support requesters throughout your organization and the internal support team.</span></span>  <span data-ttu-id="a6839-409">Endbenutzer können Supportanfragen übermitteln, bearbeiten oder widerrufen, und das Supportteam kann Anfragen innerhalb der Teams Plattform beantworten, verwalten und aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="a6839-409">End-users can submit, edit, or withdraw requests for support and the support team can respond, manage, and update requests all within the Teams platform.</span></span>

[<span data-ttu-id="a6839-410">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-410">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-remotesupport)

:::row:::
  :::column span="2":::
    ![Supportformular anfordern](../assets/images/remote-support-request-form.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Supportdetails anfordern](../assets/images/remote-support-request-details.jpg)
:::column-end:::
:::row-end:::

## <a name="request-a-team"></a><span data-ttu-id="a6839-413">Request-a-team</span><span class="sxs-lookup"><span data-stu-id="a6839-413">Request-a-team</span></span>

<span data-ttu-id="a6839-414">"Request-a-team" ist eine Microsoft Teams-App, die die Erstellung neuer Teams für Ihre Unternehmensorganisation optimiert.</span><span class="sxs-lookup"><span data-stu-id="a6839-414">Request-a-team is a Microsoft Teams app that optimizes new team creation for your enterprise organization.</span></span> <span data-ttu-id="a6839-415">Die App unterstützt Standardisierung und bewährte Methoden beim Erstellen neuer Teaminstanzen durch die Integration eines assistentengeführten Anforderungsformulars, eines eingebetteten Genehmigungsprozesses, eines Anforderungsstatus-Dashboards und automatisierter Teambuilds.</span><span class="sxs-lookup"><span data-stu-id="a6839-415">The app supports standardization and best practices when creating new team instances through the integration of a wizard-guided request form, an embedded approval process, a request status dashboard, and automated team builds.</span></span>

[<span data-ttu-id="a6839-416">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-416">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-requestateam)

:::row:::
  :::column span="2":::
    ![Startseitenansicht für Anforderungs-a-Team](../assets/images/request-a-team-two.jpg)
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Seitenansicht des Assistenten zum Anfordern eines Teams](../assets/images/request-a-team-three.png)
:::column-end:::
:::row-end:::

## <a name="scrums-for-channels"></a><span data-ttu-id="a6839-419">Scrums für Kanäle</span><span class="sxs-lookup"><span data-stu-id="a6839-419">Scrums for Channels</span></span>

<span data-ttu-id="a6839-420">Bei "Scrums for Channels" handelt es sich um eine Assistant-App, mit der Benutzer Innerhalb Microsoft Teams Inserente in Kanälen planen und ausführen können.</span><span class="sxs-lookup"><span data-stu-id="a6839-420">Scrums for Channels is a scrum assistant app that enables users to schedule and run scrums in channels within Microsoft Teams.</span></span> <span data-ttu-id="a6839-421">Die App eignet sich hervorragend für Remoteteams und Teams, die aus Mitgliedern aus unterschiedlichen geografischen Standorten und Zeitzonen bestehen, um tägliche Updates zu teilen und die Teilnahme an Dropdown-Stand-Up-Besprechungen sicherzustellen.</span><span class="sxs-lookup"><span data-stu-id="a6839-421">The app is great for remote teams and teams comprised of members from varied geographical locations and time zones to share daily updates and ensure participation in scrum stand-up meetings.</span></span>

[<span data-ttu-id="a6839-422">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-422">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-scrumsforchannels)

> [!NOTE]
> <span data-ttu-id="a6839-423">Informationen zum Durchführen von Talkbesprechungen in einem Gruppenchat finden Sie in der App-Vorlage [für Chats für Gruppen.](#scrums-for-group-chat)</span><span class="sxs-lookup"><span data-stu-id="a6839-423">To conduct scrum meetings in a group chat, see [Scrums for Group Chat](#scrums-for-group-chat) app template.</span></span>

:::row:::
  :::column span="2":::
    ![Ansicht "Kanälen für Kanäleeinstellungen"](../assets/images/scrum-for-channels-settings.png)
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Scrums for Channels Team Member Status View](../assets/images/scrum-for-channels-status.png)
:::column-end:::
:::row-end:::

## <a name="scrums-for-group-chat"></a><span data-ttu-id="a6839-426">Scrums für Gruppenchat</span><span class="sxs-lookup"><span data-stu-id="a6839-426">Scrums for Group Chat</span></span>

> [!NOTE]
> <span data-ttu-id="a6839-427">Die App-Vorlage Für den Status von Scrums wird aktualisiert und ist jetzt "Scrums" für Den Gruppenchat.</span><span class="sxs-lookup"><span data-stu-id="a6839-427">The Scrums Status app template is updated and is now Scrums for Group Chat.</span></span>

<span data-ttu-id="a6839-428">Bei Der Chat für Gruppenchats handelt es sich um einen unterstützenden Assistenten für Gruppenchats, mit dem Gruppenchatmitglieder asynchrone Stand-Up-Besprechungen ausführen und ihre täglichen Updates problemlos freigeben können.</span><span class="sxs-lookup"><span data-stu-id="a6839-428">Scrums for Group Chat is a supportive scrum assistant that enables group chat members to run asynchronous stand-up meetings and easily share their daily updates.</span></span> <span data-ttu-id="a6839-429">Es ermöglicht allen Mitgliedern des Gruppenchats, einen Beitrag zum Talking zu leisten und die Von anderen im laufenden Talk vorgenommenen Updates anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="a6839-429">It allows all members of the group chat to contribute to the scrum and view the updates made by others in the running scrum.</span></span>

[<span data-ttu-id="a6839-430">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-430">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-scrumsforgroupchat)

![Demo zu Vorführungen für Gruppenchats](https://raw.githubusercontent.com/wiki/OfficeDev/microsoft-teams-app-scrumstatus/images/StartScrum.jpg)

## <a name="share-now"></a><span data-ttu-id="a6839-432">Jetzt freigeben</span><span class="sxs-lookup"><span data-stu-id="a6839-432">Share Now</span></span> 

<span data-ttu-id="a6839-433">Die App "Jetzt freigeben" fördert den positiven Austausch von Informationen zwischen Kollegen, indem sie Es Ihren Benutzern ermöglicht, Inhalte innerhalb der Teams Umgebung einfach freizugeben.</span><span class="sxs-lookup"><span data-stu-id="a6839-433">The Share Now app promotes the positive exchange of information between colleagues by enabling your users to easily share content within the Teams environment.</span></span> <span data-ttu-id="a6839-434">Benutzer binden die App ein, um interessante Elemente mit Teammitgliedern zu teilen, neue freigegebene Inhalte zu entdecken, Einstellungen festzulegen und Lesezeichenfavoriten für späteres Lesen zu markieren.</span><span class="sxs-lookup"><span data-stu-id="a6839-434">Users engage the app to share items of interest with team members, discover new shared content, set preferences, and bookmark favorites for later reading.</span></span>

[<span data-ttu-id="a6839-435">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-435">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-sharenow)

![Inhaltsansicht auswählen](../assets/images/share-now-suggested-content.png)

## <a name="sharepoint-list-search"></a><span data-ttu-id="a6839-437">SharePoint-Listensuche</span><span class="sxs-lookup"><span data-stu-id="a6839-437">SharePoint List Search</span></span>

<span data-ttu-id="a6839-438">Die Zusammenarbeit in Microsoft Teams verweist häufig auf Informationen, die in Elementen in einer SharePoint Liste enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="a6839-438">Collaboration in Microsoft Teams quite often references information contained within items in a SharePoint list.</span></span> <span data-ttu-id="a6839-439">Wenn Sie einen Link zu dem betreffenden Element einfügen, wird jeder gezwungen, den Kontext von der Unterhaltung wegzuwechseln, die erforderlichen Informationen zu finden und dann zu Teams zurückzukehren, um die Unterhaltung fortzusetzen.</span><span class="sxs-lookup"><span data-stu-id="a6839-439">Paste a link to the item in question forces everyone to switch context away from the conversation, find the needed information, then return to Teams to continue the conversation.</span></span> <span data-ttu-id="a6839-440">Während die Unterhaltung fortgesetzt wird, müssen Die Benutzer mehrmals zum Referenzelement wechseln, um neue Kommentare zu überprüfen und ihre Bedeutung der im Element enthaltenen Informationen zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="a6839-440">As the conversation continues  people have to switch back to the reference item multiple times to verify new comments and refresh their memories of the information contained within the item.</span></span> <span data-ttu-id="a6839-441">Dieser Kontextwechsel schafft eine Barriere für eine reibungslose Zusammenarbeit.</span><span class="sxs-lookup"><span data-stu-id="a6839-441">This context switching creates a barrier to smooth collaboration.</span></span>
<span data-ttu-id="a6839-442">Um dieses Problem zu beheben, wird die App-Vorlage für die Listensuche verwendet.</span><span class="sxs-lookup"><span data-stu-id="a6839-442">To resolve this problem, the List Search app template is used.</span></span> <span data-ttu-id="a6839-443">Viele Benutzer verwenden SharePoint, um einige der wichtigsten Workflows in ihren Organisationen zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="a6839-443">Many users use SharePoint to power some of the core workflows in their organizations.</span></span> <span data-ttu-id="a6839-444">Die Zusammenarbeit an Listen ist jedoch schwierig.</span><span class="sxs-lookup"><span data-stu-id="a6839-444">However, collaborating around lists is difficult.</span></span> <span data-ttu-id="a6839-445">Mithilfe der Listensuche-App-Vorlage in Microsoft Teams können Benutzer Informationen aus SharePoint Listenelementen direkt in eine Chatunterhaltung einfügen, um das Kontextwechseln zu verringern, das beim einfachen Einfügen eines Links in einen Chat verursacht wird.</span><span class="sxs-lookup"><span data-stu-id="a6839-445">Using the List Search app template in Microsoft Teams, users can insert information from SharePoint list items directly within a chat conversation to alleviate the context-switching caused when simply inserting a link into a chat.</span></span> <span data-ttu-id="a6839-446">Die Informationen werden als einfach zu lesende, automatisch formatierte Karte eingefügt, die den Benutzern hilft, sich an der Unterhaltung zu beteiligen.</span><span class="sxs-lookup"><span data-stu-id="a6839-446">The information is inserted as an easy-to-read auto-formatted card, helping the users stay engaged in the conversation.</span></span>

[<span data-ttu-id="a6839-447">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-447">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-list-search-app)

![Listensuche-App](../assets/images/list-search-template.png)

## <a name="staff-check-ins"></a><span data-ttu-id="a6839-449">Einchecken von Mitarbeitern</span><span class="sxs-lookup"><span data-stu-id="a6839-449">Staff Check-ins</span></span>

<span data-ttu-id="a6839-450">Bei Mitarbeiter-Eincheckungen handelt es sich um eine [Power Apps-basierte](/powerapps/powerapps-overview) App, die die Kommunikation zwischen Ihrem Unternehmen und Ihrem Außendienst ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="a6839-450">Staff Check-ins is a [Power Apps](/powerapps/powerapps-overview) based app that enables oversight communication between your business and field personnel.</span></span> <span data-ttu-id="a6839-451">Mitarbeiter können zeitkritische Informationen und Statusupdates entweder auf geplanter oder Ad-hoc-Basis direkt über Teams bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="a6839-451">Staff can easily provide time-critical information and status updates on either a scheduled or ad-hoc basis directly from Teams.</span></span> <span data-ttu-id="a6839-452">Die App unterstützt Echtzeitspeicherort, Fotos, Notizen, Erinnerungsbenachrichtigungen und automatisierte Workflows.</span><span class="sxs-lookup"><span data-stu-id="a6839-452">The app supports real-time location, photos, notes, reminder notifications, and automated workflows.</span></span>

[<span data-ttu-id="a6839-453">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-453">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-staffcheckins)

![Erstellen der Eincheckansicht](../assets/images/staff-check-ins-create.png)

## <a name="survey"></a><span data-ttu-id="a6839-455">Umfrage</span><span class="sxs-lookup"><span data-stu-id="a6839-455">Survey</span></span>

<span data-ttu-id="a6839-456">Umfrage ist eine benutzerdefinierte Microsoft Teams [Messaging-Erweiterungs-App,](../messaging-extensions/what-are-messaging-extensions.md) mit der Sie eine Umfrage in einem Chat oder Kanal erstellen können, um Daten zu sammeln und umsetzbare Einblicke zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="a6839-456">Survey is a custom Microsoft Teams [messaging extension](../messaging-extensions/what-are-messaging-extensions.md) app that enables you to create a survey in a chat or a channel to gather data and gain actionable insight.</span></span> <span data-ttu-id="a6839-457">Die App wird auf allen Teams Plattformclients unterstützt, z. B. Desktop, Browser, iOS und Android, und kann als Teil Ihres Microsoft 365-Abonnements bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="a6839-457">The app is supported across all Teams platform clients, such as desktop, browser, iOS, and Android and is ready for deployment as part of your Microsoft 365 subscription.</span></span>  

[<span data-ttu-id="a6839-458">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-458">Get it on GitHub</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Survey-app)

:::row:::
  :::column span="2":::
    ![Umfrage in Teams Ansicht erstellen](../assets/images/survey-app-template-compose-view.gif)
:::column-end:::
:::row-end:::

## <a name="time-tally"></a><span data-ttu-id="a6839-460">Time Tally</span><span class="sxs-lookup"><span data-stu-id="a6839-460">Time Tally</span></span> 

<span data-ttu-id="a6839-461">Ein Projekt kann mehrere Aufgaben umfassen, und mitarbeitern können verschiedene Projekte zugewiesen werden.</span><span class="sxs-lookup"><span data-stu-id="a6839-461">A project can include multiple tasks, and various projects can be assigned to employees.</span></span> <span data-ttu-id="a6839-462">Vorgesetzte müssen den Projektfortschritt während der Zeit verstehen, die die Mitarbeiter für diese Aufgaben aufgewendet haben.</span><span class="sxs-lookup"><span data-stu-id="a6839-462">Managers are required to understand the project progress through the time spent by the employees on these tasks.</span></span> <span data-ttu-id="a6839-463">Dies kann eine umständliche Aktivität sein, da die Mitarbeiter die Arbeitszeittabellen ausfüllen müssen.</span><span class="sxs-lookup"><span data-stu-id="a6839-463">This can be a cumbersome activity, as the employees need to fill in the timesheets.</span></span> <span data-ttu-id="a6839-464">Mit der Time Tally-App können Mitarbeiter ihre Arbeitszeittabellen schnell ausfüllen, indem sie das mobile Gerät verwenden, und Vorgesetzte müssen sich nicht mit Mitarbeitern in der Arbeitszeittabelleneingabe beschäftigen.</span><span class="sxs-lookup"><span data-stu-id="a6839-464">Time Tally app enables employees to fill their timesheets quickly, using the mobile device, and managers do not have to follow up with employees on the timesheet entry.</span></span> <span data-ttu-id="a6839-465">Manager können die Projektauslastung basierend auf Ressourcen anzeigen und die Einträge genehmigen oder ablehnen.</span><span class="sxs-lookup"><span data-stu-id="a6839-465">Managers get to view the project utilization based on resources, and they can approve or reject the entries.</span></span> <span data-ttu-id="a6839-466">Erinnerungsbenachrichtigungen werden gesendet, um die Einhaltung der Arbeitszeittabelle sicherzustellen.</span><span class="sxs-lookup"><span data-stu-id="a6839-466">Reminder notifications are sent to ensure timesheet compliance.</span></span> <span data-ttu-id="a6839-467">Darüber hinaus stehen verlaufsbezogene Daten und Nutzungen für Analysen zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="a6839-467">Also, historical data and utilizations are available for analytics.</span></span>

[<span data-ttu-id="a6839-468">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-468">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-timetally)

![Time Tally](../assets/images/11zon_gif.gif)

## <a name="training--9734"></a><span data-ttu-id="a6839-470">Schulungs-&#9734;</span><span class="sxs-lookup"><span data-stu-id="a6839-470">Training  &#9734;</span></span>

<span data-ttu-id="a6839-471">Die Schulung ist eine benutzerdefinierte [Teams Messaging-Erweiterungs-App,](../messaging-extensions/what-are-messaging-extensions.md) mit der Benutzer eine Schulung innerhalb eines Chats oder Kanals für den Offline-Wissensaustausch und -umschulung veröffentlichen können.</span><span class="sxs-lookup"><span data-stu-id="a6839-471">Training is a custom [Teams messaging extension](../messaging-extensions/what-are-messaging-extensions.md) app that enables users to publish a training within a chat or a channel for offline knowledge sharing and upskilling.</span></span> <span data-ttu-id="a6839-472">Die App wird auf mehreren Teams Plattformclients unterstützt, z. B. Desktop, Browser, iOS und Android.</span><span class="sxs-lookup"><span data-stu-id="a6839-472">The app is supported across multiple Teams platform clients, such as desktop, browser, iOS, and Android.</span></span> <span data-ttu-id="a6839-473">Diese App ist bereit für die Bereitstellung als Teil Ihres Microsoft 365-Abonnements.</span><span class="sxs-lookup"><span data-stu-id="a6839-473">This app is ready for deployment as part of your Microsoft 365 subscription.</span></span>

[<span data-ttu-id="a6839-474">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-474">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-training)

:::row:::
  :::column span="1":::
    ![Erstellen von Schulungen in Teams Ansicht](../assets/images/training-app-template-compose-view.gif)  
:::column-end:::
:::row-end:::

## <a name="virtual-rounding"></a><span data-ttu-id="a6839-476">Virtuelle Rundung</span><span class="sxs-lookup"><span data-stu-id="a6839-476">Virtual Rounding</span></span>

<span data-ttu-id="a6839-477">Anbieter von Krankenhaus- und Notfalldiensten tätigen viele **Runden** pro Tag.</span><span class="sxs-lookup"><span data-stu-id="a6839-477">Hospital and emergency room providers make many **rounds** per day.</span></span> <span data-ttu-id="a6839-478">Diese schnellen Eincheckvorgänge bei Patienten sollen eine Statusüberprüfung der Funktionsweise des Patienten bereitstellen und sicherstellen, dass die Bedenken des Patienten berücksichtigt werden.</span><span class="sxs-lookup"><span data-stu-id="a6839-478">These quick check-ins on patients are intended to provide a status check on how the patient is doing and ensure that the patient’s concerns are addressed.</span></span> <span data-ttu-id="a6839-479">Das Aufrunden ist zwar eine wesentliche Methode, um sicherzustellen, dass Patienten von mehreren Anbietertypen überwacht werden, sie stellen jedoch einen großen Aufwand für PPE dar, da für jeden Besuch von jedem Anbieter eine neue Maske und neue Handgelenke verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="a6839-479">While rounding is an essential practice to ensure patients are being monitored by multiple types of providers, they represent a huge drain on PPE, because for each visit, from each provider, a new mask, and new set of gloves are used.</span></span> <span data-ttu-id="a6839-480">Mit diesen App-Vorlagen können Medizinische Mitarbeiter problemlos virtuelle Runden durch eine Microsoft Teams Besprechung zwischen dem Anbieter und dem Patienten durchführen.</span><span class="sxs-lookup"><span data-stu-id="a6839-480">With this app templates, medical workers can easily conduct rounds virtually, through a Microsoft Teams meeting between the provider and the patient.</span></span>

<span data-ttu-id="a6839-481">Auf die Virtuelle Rundungslösung wird auch im [Blogbeitrag](https://aka.ms/teamsvirtualrounding)Microsoft Health und Life Science verwiesen.</span><span class="sxs-lookup"><span data-stu-id="a6839-481">The Virtual Rounding solution is also referenced in the Microsoft Health and Life Sciences [blog post](https://aka.ms/teamsvirtualrounding).</span></span>

[<span data-ttu-id="a6839-482">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-482">Get it on GitHub</span></span>](https://github.com/SmartterHealth/Virtual-Rounding)

![Virtuelle Rundung](../assets/images/virtual-rounding-overview.png)

## <a name="visitor-management"></a><span data-ttu-id="a6839-484">Besucherverwaltung</span><span class="sxs-lookup"><span data-stu-id="a6839-484">Visitor Management</span></span>

<span data-ttu-id="a6839-485">Die Besucherverwaltungs-App ermöglicht Es Ihrer Organisation und Ihren Mitarbeitern, den Besucherprozess vor Ort direkt von Microsoft Teams aus einfach und effizient zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="a6839-485">The Visitor Management app enables your organization and employees to easily and efficiently manage the on-site visitor process, directly from Microsoft Teams.</span></span> <span data-ttu-id="a6839-486">Die App ermöglicht es Mitarbeitern, Besucheranfragen zu erstellen, den Anforderungsstatus zentral über das Besucherdashboard nachzuverfolgen und Echtzeitbenachrichtigungen zu erhalten, wenn ein Besucher eintrifft.</span><span class="sxs-lookup"><span data-stu-id="a6839-486">The app enables employees to create visitor requests, centrally track a request status through the visitor dashboard, and receive real-time notifications when a visitor arrives.</span></span>

[<span data-ttu-id="a6839-487">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-487">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-app-visitormanagement)

:::row:::
  :::column span="2":::
    ![Erstellen einer Anforderungsansicht](../assets/images/visitor-management-create-request.png)
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Benachrichtigung zur Besucherankunft](../assets/images/visitor-management-notify-host.png)
:::column-end:::
:::row-end:::

## <a name="water-cooler-9734"></a><span data-ttu-id="a6839-490">Wasserlauf&#9734;</span><span class="sxs-lookup"><span data-stu-id="a6839-490">Water Cooler &#9734;</span></span>

<span data-ttu-id="a6839-491">Water Water Ist eine benutzerdefinierte Teams-App, die es Unternehmensteams ermöglicht, ungezwungene Unterhaltungen zwischen Teamkameraden zu erstellen, einzuladen und daran teilzunehmen, z. B. solche, die vom Wasser- oder Pausenraum stattfinden.</span><span class="sxs-lookup"><span data-stu-id="a6839-491">Water Cooler is a custom Teams app that enables corporate teams to create, invite, and join casual conversations among teammates, such as those that take place by the Water Cooler or break room.</span></span> <span data-ttu-id="a6839-492">Verwenden Sie diese Vorlage für mehrere Szenarien, z. B. neue nicht projektbezogene Ankündigungen, interessante Themen, aktuelle Ereignisse oder Unterhaltungen über Hobbys.</span><span class="sxs-lookup"><span data-stu-id="a6839-492">Use this template for multiple scenarios, such as new non project related announcements, topics of interest, current events, or conversations about hobbies.</span></span> <span data-ttu-id="a6839-493">Die App bietet eine einfache Benutzeroberfläche für jeden, um eine vorhandene Unterhaltung zu finden oder eine neue zu starten.</span><span class="sxs-lookup"><span data-stu-id="a6839-493">The app provides an easy interface for anyone to find an existing conversation or start a new one.</span></span> <span data-ttu-id="a6839-494">Es ist eine Grundlage für die Erstellung von benutzerdefinierten, gezielten Kommunikationsfunktionen, die die Interaktion zwischen Kollegen fördern, die andernfalls in Pausen möglicherweise keine Möglichkeit haben, Kontakte zu machen.</span><span class="sxs-lookup"><span data-stu-id="a6839-494">It is a foundation for building custom targeted communication capabilities, promoting interaction amongst coworkers who may otherwise not get a chance to socialize during breaks.</span></span>    

[<span data-ttu-id="a6839-495">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-495">Get it on GitHub</span></span>](https://github.com/microsoft/csapps-msteams-watercooler)     

![Wasserverbraucher-App-Bildschirme](../assets/images/appScreens.gif)    

### <a name="key-features"></a><span data-ttu-id="a6839-497">Hauptmerkmale</span><span class="sxs-lookup"><span data-stu-id="a6839-497">Key features</span></span>

<span data-ttu-id="a6839-498">**Startseite "Wasser" :** Sie können vorhandene Räume durchsuchen, in denen Teammitglieder in vorhandenen Unterhaltungen mit bestimmten Personen oder Themen von Interesse interagieren.</span><span class="sxs-lookup"><span data-stu-id="a6839-498">**Water Cooler Home Page**: You can browse existing rooms where team members are interacting in existing conversations with certain people or topics of interest.</span></span> <span data-ttu-id="a6839-499">Aktive Unterhaltungen auf der **Startseite** zeigen einen Raumnamen, eine kurze Beschreibung, die Anrufdauer und ein Raumbild.</span><span class="sxs-lookup"><span data-stu-id="a6839-499">Active conversations on the **Home Page** show a room name, short description, call duration, and room image.</span></span> 

![Startseite für Wassersenser](../assets/images/home-page.png)

<span data-ttu-id="a6839-501">**Chatroom** beitreten: Verwenden Sie die Funktion **"Chatroom beitreten",** um sofort an einer laufenden Unterhaltung teilzunehmen.</span><span class="sxs-lookup"><span data-stu-id="a6839-501">**Join room**: Use the **Join room** feature to join an ongoing conversation immediately.</span></span> <span data-ttu-id="a6839-502">Wählen Sie **"Teilnehmen"** aus aktiven Unterhaltungen aus, um dem Raum beizutreten.</span><span class="sxs-lookup"><span data-stu-id="a6839-502">Select **Join** from active conversations to join the room.</span></span>

![Chatroom beitreten](../assets/images/joinRoom.gif)

<span data-ttu-id="a6839-504">**Raumerstellung:** Verwenden Sie die **Raumerstellungsfunktion,** um einen Teams Anruf oder Chat für alle Teilnehmer zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="a6839-504">**Room creation**: Use the **Room creation** feature to create a Teams call or chat for all attendees to interact.</span></span> <span data-ttu-id="a6839-505">Erstellen Sie Räume ganz einfach, indem Sie den Raumnamen, eine kurze Beschreibung, bis zu fünf Kollegen als anfängliche Gruppe angeben und aus den bereitgestellten Raumbildern auswählen.</span><span class="sxs-lookup"><span data-stu-id="a6839-505">Create rooms easily by specifying the room name, short description, up to five colleagues as an initial group and selecting from the provided set of room images.</span></span> 

![Raumerstellung](../assets/images/createRoom.gif)

<span data-ttu-id="a6839-507">**Raum suchen:** Verwenden Sie die Funktion **"Raum suchen",** um nach einem Schlüsselwort zu suchen, das mit dem Thema oder kurzen Beschreibungen laufender Unterhaltungen übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="a6839-507">**Find room**: Use the **Find room** feature to search keyword which matches with the topic or short descriptions of ongoing conversations.</span></span>

![Unterhaltung suchen](../assets/images/findConversation.gif)

<span data-ttu-id="a6839-509">**Teilnehmer-Einladung:** Verwenden Sie die **Teilnehmer-Einladungsfunktion,** um weitere Benutzer nach der Raumerstellung einzuladen.</span><span class="sxs-lookup"><span data-stu-id="a6839-509">**Attendee invitation**: Use the **Attendee invitation** feature to invite additional users after room creation.</span></span> <span data-ttu-id="a6839-510">Dies ähnelt Teams Anruf.</span><span class="sxs-lookup"><span data-stu-id="a6839-510">This is similar to Teams call.</span></span>

![Teilnehmer-Einladung](../assets/images/attendeeInvitation.gif)

<span data-ttu-id="a6839-512">**App-Signal:** Das **Wasser-Symbol im** linken Menü zeigt ein Signal mit der Anzahl der aktiven Unterhaltungen an, die von Teams während der Verwendung einer beliebigen App sichtbar sind.</span><span class="sxs-lookup"><span data-stu-id="a6839-512">**App badge**: The **Water Cooler** icon on the left menu shows a badge with the number of active conversations visible from Teams while using any app.</span></span> 

![App-Signal](../assets/images/badge.gif)

## <a name="workplace-awards"></a><span data-ttu-id="a6839-514">Workplace Award</span><span class="sxs-lookup"><span data-stu-id="a6839-514">Workplace Awards</span></span>

<span data-ttu-id="a6839-515">Workplace Award ist eine Teams App-Vorlage, die einen positiven Rahmen bietet, um die Erkennung zu fördern und die Kultur der Mitarbeitermotivation am modernen Arbeitsplatz zu fördern.</span><span class="sxs-lookup"><span data-stu-id="a6839-515">Workplace Awards is a Teams app template that provides a positive framework to foster recognition and encourage the culture of employee appreciation in the modern workplace.</span></span> <span data-ttu-id="a6839-516">Die App ermöglicht es Ihnen, eine Mitarbeiterbezeichnung und -erkennung namens "R&R"-Programm einzurichten und zu verwalten, in dem Mitarbeiter problemlos Kollegen benennen und unterstützen können und Ihr R&R-Leiter übermittelte Ehrungen anzeigen, Preise gewähren und Empfänger ankündigen kann.</span><span class="sxs-lookup"><span data-stu-id="a6839-516">The app enables you to setup and manage an employee rewards and recognition, called R&R program where employees can easily nominate and endorse colleagues and your R&R leader can view submitted nominations, grant awards, and announce recipients.</span></span>

[<span data-ttu-id="a6839-517">Get it on GitHub</span><span class="sxs-lookup"><span data-stu-id="a6839-517">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-workplaceawards)

:::row:::
  :::column span="2":::
    ![<span data-ttu-id="a6839-518">Workplace-Ehrungskarte</span><span class="sxs-lookup"><span data-stu-id="a6839-518">Workplace awards nomination card</span></span> ](../assets/images/workplace-awards-nominate.png)
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Registerkarte "Workplace-Liste"](../assets/images/workplace-awards-champion-tab.png)
:::column-end:::
:::row-end:::

<span data-ttu-id="a6839-520">Weitere Informationen zur App-Vorlage finden Sie unter [App-Vorlage.](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR2_7qFm_lcZAr4eqEhnLsZ9UMVZGT1lCT0FXUDdZMUM0RkpBS1BESTAwWC4u)</span><span class="sxs-lookup"><span data-stu-id="a6839-520">For more information on app template, see [App template](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR2_7qFm_lcZAr4eqEhnLsZ9UMVZGT1lCT0FXUDdZMUM0RkpBS1BESTAwWC4u).</span></span>

## <a name="see-also"></a><span data-ttu-id="a6839-521">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="a6839-521">See also</span></span>

[<span data-ttu-id="a6839-522">Integrieren von Web-Apps</span><span class="sxs-lookup"><span data-stu-id="a6839-522">Integrate web apps</span></span>](~/samples/integrate-web-apps-overview.md)
