---
title: Microsoft Teams-App-Vorlagen
description: Links und Beschreibungen von App-Vorlagen für die Microsoft Teams-Plattform
ms.topic: reference
keywords: Beispielbeispiele für Microsoft Teams-Vorlagen
localization_priority: Normal
ms.author: lajanuar
author: laujan
ms.openlocfilehash: ceec7e05ae08ff147fb87005403ec8264e0ec313
ms.sourcegitcommit: a732789190f59ec1f3699e8ad2f06387e8fe1458
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2021
ms.locfileid: "52058670"
---
# <a name="app-templates-for-microsoft-teams"></a><span data-ttu-id="cf35e-104">App-Vorlagen für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="cf35e-104">App templates for Microsoft Teams</span></span>

<span data-ttu-id="cf35e-105">App-Vorlagen sind Beispiele für vollständige Apps für Microsoft Teams, die open-source sind und auf GitHub verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="cf35e-105">App templates are examples of complete apps for Microsoft Teams that are open-source and available on GitHub.</span></span> <span data-ttu-id="cf35e-106">Jede App-Vorlage enthält ausführliche Anweisungen zum Bereitstellen und Installieren dieser App für Ihre Organisation.</span><span class="sxs-lookup"><span data-stu-id="cf35e-106">Each app template contains detailed instructions for deploying and installing that app for your organization.</span></span> <span data-ttu-id="cf35e-107">Außerdem bietet es eine Beispiel-App, die Sie sofort installieren und verwenden können.</span><span class="sxs-lookup"><span data-stu-id="cf35e-107">It also provides a sample app that you can install and start using immediately.</span></span> <span data-ttu-id="cf35e-108">Der vollständige Quellcode ist ebenfalls verfügbar, mit dem Sie ihn detailliert untersuchen oder den Code forken und an Ihre spezifischen Anforderungen anpassen können.</span><span class="sxs-lookup"><span data-stu-id="cf35e-108">The complete source code is also available, which allows you to explore it in detail or fork the code and alter it to meet your specific requirements.</span></span>
<span data-ttu-id="cf35e-109">Alle App-Vorlagen werden unter den [MIT-Lizenzbedingungen](https://github.com/OfficeDev/microsoft-teams-apps-eprescription/blob/master/LICENSE) bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="cf35e-109">All app templates are provided under the [MIT License](https://github.com/OfficeDev/microsoft-teams-apps-eprescription/blob/master/LICENSE) terms.</span></span>

> [!NOTE] 
> <span data-ttu-id="cf35e-110">Sie müssen Apps, die aus App-Vorlagen für Ihre Benutzer und Organisationen erstellt wurden, lizenz- und unterstützen.</span><span class="sxs-lookup"><span data-stu-id="cf35e-110">You must license and support apps created from app templates for your users and organizations.</span></span>

<span data-ttu-id="cf35e-111">**&#9734; Gibt neu veröffentlichte App-Vorlagen an.**</span><span class="sxs-lookup"><span data-stu-id="cf35e-111">**&#9734; Indicates newly released app templates.**</span></span>

### <a name="key-benefits"></a><span data-ttu-id="cf35e-112">Wichtige Vorteile</span><span class="sxs-lookup"><span data-stu-id="cf35e-112">Key benefits</span></span>

* <span data-ttu-id="cf35e-113">**Direkte Bereitstellung in der Cloud:** Alle App-Vorlagen enthalten Bereitstellungsskripts, mit dem Sie alle erforderlichen Dienste in Microsoft Azure oder der Power Platform hosten können.</span><span class="sxs-lookup"><span data-stu-id="cf35e-113">**Deploy directly to the cloud:** All app templates include deployment scripts that allows you to host all required services in Microsoft Azure or the Power Platform.</span></span> 
* <span data-ttu-id="cf35e-114">**Empfohlener Beispielcode:** Die App-Vorlagen entsprechen den empfohlenen bewährten Methoden für Sicherheit und Infrastruktur.</span><span class="sxs-lookup"><span data-stu-id="cf35e-114">**Recommended sample code:** The app templates conform to recommended best practices around security and infrastructure.</span></span> <span data-ttu-id="cf35e-115">Alle von der Community übermittelten Änderungen an den App-Vorlagen werden überprüft, um die Konformität sicherzustellen.</span><span class="sxs-lookup"><span data-stu-id="cf35e-115">All community submitted changes to the app templates are reviewed to ensure conformance.</span></span>
* <span data-ttu-id="cf35e-116">**Anpassbar und erweiterbar:** Während alle App-Vorlagen mit minimaler Konfiguration bereitgestellt werden, werden die gesamte Codebasis und Bereitstellungsskripts bereitgestellt, sodass Sie sie ganz einfach an Ihre individuellen Anforderungen anpassen oder erweitern können.</span><span class="sxs-lookup"><span data-stu-id="cf35e-116">**Customizable and extensible:** While all app templates are deployed with minimal configuration, the entire code base and deployment scripts are provided, so that you can easily customize or extend them to fit your unique needs.</span></span>
* <span data-ttu-id="cf35e-117">**Ausführliche Dokumentation:** Alle App-Vorlagen werden von einer End-to-End-Dokumentation zu Lösungsarchitektur, Bereitstellung und Konfigurationsschritten begleitet.</span><span class="sxs-lookup"><span data-stu-id="cf35e-117">**Detailed documentation:** All app templates are accompanied by end-to-end documentation on solution architecture, deployment, and configuration steps.</span></span>  

## <a name="adoption-bot"></a><span data-ttu-id="cf35e-118">Adoption Bot</span><span class="sxs-lookup"><span data-stu-id="cf35e-118">Adoption Bot</span></span> 

<span data-ttu-id="cf35e-119">Adoption Bot ist ein Chatbot für die Benutzerpflege, der mit Power Virtual Agent für Teams PVA erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="cf35e-119">Adoption Bot is a user care chat bot built with Power Virtual Agent for Teams PVA.</span></span> <span data-ttu-id="cf35e-120">Es wird als die PVA-Version von FAQ Plus betrachtet.</span><span class="sxs-lookup"><span data-stu-id="cf35e-120">It is considered as the PVA version of FAQ Plus.</span></span> <span data-ttu-id="cf35e-121">Adoption Bot beantwortet mehr als 100 häufig gestellte Fragen zu Microsoft 365 und Teams.</span><span class="sxs-lookup"><span data-stu-id="cf35e-121">Adoption Bot answers 100+ common questions about Microsoft 365 and Teams.</span></span> <span data-ttu-id="cf35e-122">Sie können die vorhandenen Themen bearbeiten, eigene Themen hinzufügen und vorhandene FAQs hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="cf35e-122">You can edit the existing topics, add your own topics, and ingest existing FAQs.</span></span> <span data-ttu-id="cf35e-123">Wenn Benutzer zusätzliche Hilfe benötigen, kann Adoption Bot sie mit Experten verbinden oder sogar auf das Öffnen von Diensttickets mit Premium-Flussconnectors erweitert werden.</span><span class="sxs-lookup"><span data-stu-id="cf35e-123">If users need additional help, Adoption Bot can connect them to experts or even be extended to open service tickets with premium flow connectors.</span></span> <span data-ttu-id="cf35e-124">Dieser Bot ist selbst installiert oder in eine benutzerdefinierte App wie den [Adoption Hub integrierte.](https://github.com/akporzondek/adoption_hub)</span><span class="sxs-lookup"><span data-stu-id="cf35e-124">This bot is self-installed or built into a custom app, such as the [Adoption Hub](https://github.com/akporzondek/adoption_hub).</span></span>

[<span data-ttu-id="cf35e-125">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-125">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-adopt-bot)

## <a name="adoption-tool--champion-management-platform-9734"></a><span data-ttu-id="cf35e-126">Einführungstool – Champion Management Platform &#9734;</span><span class="sxs-lookup"><span data-stu-id="cf35e-126">Adoption Tool- Champion Management Platform &#9734;</span></span>

<span data-ttu-id="cf35e-127">Mit der #A0 (Champion Management Platform) können Sie Ihre Teamarbeits-Champions verwalten, skalieren und inspirieren, um mehr zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="cf35e-127">The Champion Management Platform (CMP) app template helps you manage, scale, and inspire your teamwork champions to achieve more.</span></span> <span data-ttu-id="cf35e-128">Diese App-Vorlage basiert auf dem SharePoint Framework und wird in eine Registerkarte innerhalb eines Teams geladen.</span><span class="sxs-lookup"><span data-stu-id="cf35e-128">This app template is built on the SharePoint Framework and loaded into a tab within a team.</span></span> <span data-ttu-id="cf35e-129">Gruppen können dieses Tool nutzen, um die Programmmitgliedschaft zu verwalten, eine Bestenliste und Ereignistypen für die Protokollierung sowie Tools zum Überlagern digitaler Badges für Programmteilnehmer zur Verfügung zu stellen.</span><span class="sxs-lookup"><span data-stu-id="cf35e-129">Groups can leverage this tool to help manage program membership, provide a leaderboard and event types for logging, and tools to overlay digital badges to program participants.</span></span>

[<span data-ttu-id="cf35e-130">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-130">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-champion-management)

## <a name="adoption-tool--microsoft-365-learning-pathways-get-started-9734"></a><span data-ttu-id="cf35e-131">Einführungstool – Microsoft 365 Learning Pathways (Get Started) &#9734;</span><span class="sxs-lookup"><span data-stu-id="cf35e-131">Adoption Tool- Microsoft 365 Learning Pathways (Get Started) &#9734;</span></span>

<span data-ttu-id="cf35e-132">Mit der App-Vorlage Erste Schritte können Sie die Leistung von Microsoft 365-Lernpfaden in Microsoft Teams nutzen.</span><span class="sxs-lookup"><span data-stu-id="cf35e-132">The Get Started app template allows you to bring the power of Microsoft 365 learning pathways inside of Microsoft Teams.</span></span> <span data-ttu-id="cf35e-133">Mit dieser App-Vorlage können Sie einfachen Zugriff auf bestimmte Schulungsseiten oder andere Intranetressourcen gewähren und die Inhalte direkt in Teams laden.</span><span class="sxs-lookup"><span data-stu-id="cf35e-133">This app template allows you to grant easy access to specific training pages or other intranet assets and load the content directly within Teams.</span></span> <span data-ttu-id="cf35e-134">Sie können den Namen oder das Logo der App auch so ändern, dass sie Ihrem Unternehmensbranding entsprechen.</span><span class="sxs-lookup"><span data-stu-id="cf35e-134">You can also change the app name or logo to match your company branding.</span></span>

[<span data-ttu-id="cf35e-135">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-135">Get it on GitHub</span></span>](https://github.com/msft-teams/tools/tree/master/M365%20Learning%20Pathways)

## <a name="appointment-manager"></a><span data-ttu-id="cf35e-136">Appointment Manager</span><span class="sxs-lookup"><span data-stu-id="cf35e-136">Appointment Manager</span></span> 

<span data-ttu-id="cf35e-137">Appointment Manager ist eine Teams-App-Vorlage, mit der Unternehmen virtuelle Termine mit Kunden über Teams erstellen, verwalten und durchführen können.</span><span class="sxs-lookup"><span data-stu-id="cf35e-137">Appointment Manager is a Teams app template to help businesses create, manage, and conduct virtual appointments with consumers through Teams.</span></span> <span data-ttu-id="cf35e-138">Neue Terminanfragen von Kunden sind in Teams-Kanälen sichtbar, in denen sie schnell zugewiesen und mitarbeitern in einem Team zugewiesen werden.</span><span class="sxs-lookup"><span data-stu-id="cf35e-138">New appointment requests from consumers are visible in Teams channels, where they are quickly assigned and reassigned to staff in a team.</span></span> <span data-ttu-id="cf35e-139">Terminanfragen werden auf Team- oder persönlichen Ebenen über benutzerdefinierte Registerkarten angezeigt.</span><span class="sxs-lookup"><span data-stu-id="cf35e-139">Appointment requests are viewed at team or personal levels through custom tabs.</span></span> <span data-ttu-id="cf35e-140">Jeder Termin ist einer Teams-Onlinebetreff zugeordnet, daher können Mitarbeiter und Verbraucher problemlos zur geplanten Zeit an der Besprechung teilnehmen.</span><span class="sxs-lookup"><span data-stu-id="cf35e-140">Every appointment is associated with a Teams online meeting, hence the staff and consumers can easily join the meeting at the scheduled time.</span></span>

<span data-ttu-id="cf35e-141">Die App-Vorlage wird in Microsoft Bookings integriert, um die Terminverwaltung zu einfach zu machen.</span><span class="sxs-lookup"><span data-stu-id="cf35e-141">The app template integrates with Microsoft Bookings for easy appointment management.</span></span> <span data-ttu-id="cf35e-142">Geplante Termine werden automatisch in den Kalendern der zugewiesenen Mitarbeiter angezeigt, und Verbraucher erhalten anpassbare E-Mail-Benachrichtigungen und Erinnerungen mit eingebetteten Besprechungslinks.</span><span class="sxs-lookup"><span data-stu-id="cf35e-142">Scheduled appointments automatically appear on assigned staff members' calendars, and consumers receive customizable email notifications and reminders with embedded meeting links.</span></span>

[<span data-ttu-id="cf35e-143">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-143">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-appointment-manager)

<span data-ttu-id="cf35e-144">![Appointment Manager Overview ](../assets/images/appointment-manager-overview.png)
 ![ Appointment Manager in Teams](../assets/images/appointment-manager-2.png)</span><span class="sxs-lookup"><span data-stu-id="cf35e-144">![Appointment Manager Overview](../assets/images/appointment-manager-overview.png)
![Appointment Manager in Teams](../assets/images/appointment-manager-2.png)</span></span>

## <a name="ask-away"></a><span data-ttu-id="cf35e-145">Ask Away</span><span class="sxs-lookup"><span data-stu-id="cf35e-145">Ask Away</span></span>

<span data-ttu-id="cf35e-146">Ask Away ist ein [Microsoft Teams-Bot,](../bots/what-are-bots.md) der Benutzern die Durchführung von Fragen und Antworten ermöglicht, die als Fragen-&A-Sitzungen in Teams bezeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="cf35e-146">Ask Away is a [Microsoft Teams bot](../bots/what-are-bots.md) that enables users to conduct Question and Answer, called Q&A sessions within Teams.</span></span> <span data-ttu-id="cf35e-147">Mithilfe des Bots "Weg fragen" können Teammitglieder Fragen übermitteln und fragen, die von Kollegen gemeinsam genutzt werden, sodass Fragen und Antworten&Einem Host problemlos in einem Kanal oder Chat gesammelt werden können.</span><span class="sxs-lookup"><span data-stu-id="cf35e-147">Using the Ask Away bot, team members can submit and up-vote questions shared by colleagues allowing Q&A hosts to easily gather top-of-mind questions within a channel or chat.</span></span> <span data-ttu-id="cf35e-148">Der Bot wird verwendet, um eine Echtzeit-Frage&einer Sitzung in einer Teams-Besprechung zu leiten und ermöglicht Teilnehmern, Fragen live über Chat zu übermitteln.</span><span class="sxs-lookup"><span data-stu-id="cf35e-148">The bot is used to conduct a real-time Q&A session in a Teams meeting and allows attendees to submit questions live through chat.</span></span>

[<span data-ttu-id="cf35e-149">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-149">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-askaway)

:::row:::
  :::column span="2":::
    ![Ansicht des Popupdialogfelds für das Leaderboard, in dem Benutzer über Fragen abstimmen können](../assets/images/ask-away-app.png)  
:::column-end:::
:::row-end:::

## <a name="associate-insights"></a><span data-ttu-id="cf35e-151">Assoziierte Einblicke</span><span class="sxs-lookup"><span data-stu-id="cf35e-151">Associate Insights</span></span>

<span data-ttu-id="cf35e-152">Associate Insights ist eine [Power Apps-Vorlage,](/powerapps/maker/canvas-apps/embed-teams-app) mit der FirstLine-Mitarbeiter Kundenmeinungen, -stimmungen und -wahrnehmungen direkt erfassen und übermitteln können.</span><span class="sxs-lookup"><span data-stu-id="cf35e-152">Associate Insights is a [Power Apps](/powerapps/maker/canvas-apps/embed-teams-app) template that empowers firstline workers to directly capture and submit customer opinion, sentiment, and perception.</span></span> <span data-ttu-id="cf35e-153">Firstline-Mitarbeiter sind häufig der erste Unternehmensvertreter, der sich mit Kunden an einem 1:1-Kontaktpunkt beschäftigt.</span><span class="sxs-lookup"><span data-stu-id="cf35e-153">Firstline workers are often the first company representative to engage with customers in a one-to-one point-of contact.</span></span> <span data-ttu-id="cf35e-154">Die gesammelten Daten werden gemeinsam von Geschäftsteams freigegeben und verwendet, z. B. über eine Power BI Teams-Registerkarte, um die Produktverbesserung zu verbessern und die Kundenerfahrung zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="cf35e-154">The collected data are shared and used collaboratively by business teams, such as through a Power BI Teams tab, for product improvement and enhancing the customer experience.</span></span>

[<span data-ttu-id="cf35e-155">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-155">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-associateinsights)

:::row:::
  :::column span="2":::
    ![Feedbackansicht der von der App generierten Einblicke](../assets/images/associate-insights-app.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Power BI-Ansicht von app generierten Einblicken](../assets/images/associate-insights-app2.png)
:::column-end:::
:::row-end:::

## <a name="attendance"></a><span data-ttu-id="cf35e-158">Anwesenheit</span><span class="sxs-lookup"><span data-stu-id="cf35e-158">Attendance</span></span>

<span data-ttu-id="cf35e-159">Die Anwesenheits-App ist eine [Power Apps-Registerkarte,](/powerapps/maker/canvas-apps/embed-teams-app) die in einem Team angeheftet ist.</span><span class="sxs-lookup"><span data-stu-id="cf35e-159">The Attendance app is a [Power Apps](/powerapps/maker/canvas-apps/embed-teams-app) tab that are pinned in a team.</span></span> <span data-ttu-id="cf35e-160">Es ist so konzipiert, dass Anwesenheit in Einstellungen aufgezeichnet wird, z. B. in Lern- und Schulungsumgebungen.</span><span class="sxs-lookup"><span data-stu-id="cf35e-160">It is designed to record presence in settings, such as learning and training environments.</span></span> <span data-ttu-id="cf35e-161">Benutzer können die Teilnahme in der Vergangenheit bis zu 30 Tage lang markieren oder bearbeiten und zusammenfassende Anwesenheitsberichte für eine gesamte Gruppe oder einzelne Teilnehmer anzeigen.</span><span class="sxs-lookup"><span data-stu-id="cf35e-161">Users can mark or edit attendance for up to 30 days in the past and view summarized attendance reports for an entire group or individual attendees.</span></span> <span data-ttu-id="cf35e-162">Weitere Informationen zur Teilnahme an Teams finden Sie [unter Get it on GitHub](https://github.com/OfficeDev/microsoft-teams-apps-attendance).</span><span class="sxs-lookup"><span data-stu-id="cf35e-162">For more information on teams attendance, see [Get it on GitHub](https://github.com/OfficeDev/microsoft-teams-apps-attendance).</span></span>

<span data-ttu-id="cf35e-163">In der folgenden Abbildung wird die Teilnahme-App-Demo angezeigt:</span><span class="sxs-lookup"><span data-stu-id="cf35e-163">The following image displays the attendance app demo:</span></span>  

![Teilnahme-App-Demo](../assets/images/attendance-app.png)

## <a name="book-a-room"></a><span data-ttu-id="cf35e-165">Book-a-room</span><span class="sxs-lookup"><span data-stu-id="cf35e-165">Book-a-room</span></span>

<span data-ttu-id="cf35e-166">Book-a-room ist ein [Microsoft Teams-Bot,](../bots/what-are-bots.md) mit dem Benutzer einen Besprechungsraum für 30, 60 oder 90 Minuten ab der aktuellen Uhrzeit schnell finden und reservieren können.</span><span class="sxs-lookup"><span data-stu-id="cf35e-166">Book-a-room is a [Microsoft Teams bot](../bots/what-are-bots.md) that allows users quickly to find and reserve a meeting room for 30, 60, or 90 minutes starting from the current time.</span></span> <span data-ttu-id="cf35e-167">Die Standardzeit beträgt 30 Minuten.</span><span class="sxs-lookup"><span data-stu-id="cf35e-167">The default time is 30 minutes.</span></span> <span data-ttu-id="cf35e-168">Der Book-a-room-Bot bietet Bereiche für persönliche oder 1:1-Unterhaltungen.</span><span class="sxs-lookup"><span data-stu-id="cf35e-168">The Book-a-room bot scopes to personal or 1:1 conversations.</span></span> <span data-ttu-id="cf35e-169">Weitere Informationen zur Book-a-room-App finden Sie unter [Get it on GitHub](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom).</span><span class="sxs-lookup"><span data-stu-id="cf35e-169">For more information on Book-a-room app, see [Get it on GitHub](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom).</span></span>  
<span data-ttu-id="cf35e-170">Die folgende Abbildung zeigt die Book-a-room-Demo:</span><span class="sxs-lookup"><span data-stu-id="cf35e-170">The following image displays the Book-a-room demo:</span></span>

![Book-a-room-Demo](../assets/images/book-a-room.png)

## <a name="building-access"></a><span data-ttu-id="cf35e-172">Erstellen von Zugriff</span><span class="sxs-lookup"><span data-stu-id="cf35e-172">Building Access</span></span>

<span data-ttu-id="cf35e-173">Building Access ist eine Microsoft [Power Platform-basierte](https://powerapps.microsoft.com/blog/now-in-preview-customize-teams-with-built-in-power-platform-capabilities/) App, die die Verwaltung von Belegungsschwellenwerte und Normen für die soziale Distanzierung unterstützt, indem es Den Verantwortlichen von Einrichtungen ermöglicht wird, die Anwesenheit von Mitarbeitern vor Ort zu verwalten, nachzuververwalten und zu melden.</span><span class="sxs-lookup"><span data-stu-id="cf35e-173">Building Access is a Microsoft [Power Platform](https://powerapps.microsoft.com/blog/now-in-preview-customize-teams-with-built-in-power-platform-capabilities/) based app that supports the administration of building occupancy thresholds and social distancing norms by enabling facilities directors to manage, track, and report employee on-site presence.</span></span> <span data-ttu-id="cf35e-174">Die app, die mithilfe von Microsoft [Power Apps](/powerapps/powerapps-overview)und [Power Automate](/power-automate/getting-started)erstellt wurde, integriert sich tief in Microsoft Teams und ermöglicht Es Organisationen, die Erstellungsbereitschaft zu bestimmen, Berechtigungskriterien für den Zugriff vor Ort festzulegen und Einblicke für die zukünftige Planung zu sammeln.</span><span class="sxs-lookup"><span data-stu-id="cf35e-174">The app, built using Microsoft [Power Apps](/powerapps/powerapps-overview), and [Power Automate](/power-automate/getting-started), deeply integrates with Microsoft Teams and enables organizations to determine building readiness, establish eligibility criteria for on-site access, and gather insights for future planning.</span></span>

[<span data-ttu-id="cf35e-175">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-175">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-buildingaccess)

:::row:::
   :::column span="":::
     ![Erstellen einer Zugriffsreservierungskarte](../assets/images/building-access-reservation.png)
   :::column-end:::
   :::column span="":::
      ![Erstellen der Zugriffstastenansicht](../assets/images/building-access-access-key.png)
   :::column-end:::
:::row-end:::

## <a name="celebrations"></a><span data-ttu-id="cf35e-178">Feiern</span><span class="sxs-lookup"><span data-stu-id="cf35e-178">Celebrations</span></span>

<span data-ttu-id="cf35e-179">"Festlichkeiten" ist eine Teams-App, die Teammitgliedern dabei hilft, geburtstage, Jubiläen und andere wiederkehrende Ereignisse zu zelebrieren.</span><span class="sxs-lookup"><span data-stu-id="cf35e-179">Celebrations is a Teams app that helps team members to celebrate each others' birthdays, anniversaries, and other recurring events.</span></span> <span data-ttu-id="cf35e-180">Er erinnert sich an besondere Anlässe aller Teammitglieder und sendet eine freundliche Nachricht in allen teams, die zum Zeitpunkt der Ereigniserstellung ausgewählt wurden, um den Teammitgliedern ein besonderes Gefühl an ihrem Tag zu machen.</span><span class="sxs-lookup"><span data-stu-id="cf35e-180">It remembers special occasions of all the team members and sends a friendly message in all the teams selected at the time of event creation, to make the team members feel special on their day.</span></span>

<span data-ttu-id="cf35e-181">Die App bietet allen Teammitgliedern eine einfache Schnittstelle zum persönlichen Hinzufügen und Anzeigen ihrer Ereignisse und ermöglicht es dem Benutzer, die Teams auszuwählen, in denen die Ereignisse freigegeben werden.</span><span class="sxs-lookup"><span data-stu-id="cf35e-181">The app provides an easy interface for all the team members to personally add and view their events and also allows the user to select the teams in which the events gets shared.</span></span>

[<span data-ttu-id="cf35e-182">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-182">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-celebrations-app)

## <a name="checklist"></a><span data-ttu-id="cf35e-183">Prüfliste</span><span class="sxs-lookup"><span data-stu-id="cf35e-183">Checklist</span></span>

<span data-ttu-id="cf35e-184">Prüfliste ist eine [](../messaging-extensions/what-are-messaging-extensions.md) benutzerdefinierte Microsoft Teams-Messaging-Erweiterungs-App, mit der Sie mit Ihrem Team zusammenarbeiten können, indem Sie eine freigegebene Prüfliste in einem Chat oder Kanal erstellen.</span><span class="sxs-lookup"><span data-stu-id="cf35e-184">Checklist is a custom Microsoft Teams [messaging extension](../messaging-extensions/what-are-messaging-extensions.md) app that enables you to collaborate with your team by creating a shared checklist in a chat or channel.</span></span> <span data-ttu-id="cf35e-185">Die App wird auf allen Teams-Plattformclients unterstützt, z. B. Desktopbrowser, iOS und Android.</span><span class="sxs-lookup"><span data-stu-id="cf35e-185">The app is supported across all Teams platform clients, such as desktop browser, iOS, and Android.</span></span> <span data-ttu-id="cf35e-186">Die App ist für die Bereitstellung im Rahmen Ihres Microsoft 365-Abonnements bereit.</span><span class="sxs-lookup"><span data-stu-id="cf35e-186">The app is ready for deployment as part of your Microsoft 365 subscription.</span></span>  

[<span data-ttu-id="cf35e-187">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-187">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-checklist-app)

:::row:::
:::column span="2":::
    ![Erstellen einer Prüfliste in der Teams-Ansicht](../assets/images/checklist-app-template-compose-view.gif)  
:::column-end:::
:::row-end:::

## <a name="classroom-drop-in"></a><span data-ttu-id="cf35e-189">Classroom-Drop-In</span><span class="sxs-lookup"><span data-stu-id="cf35e-189">Classroom Drop-in</span></span> 

<span data-ttu-id="cf35e-190">Das Classroom-Drop-In ist eine Microsoft [Power Platform-basierte](https://powerapps.microsoft.com/blog/now-in-preview-customize-teams-with-built-in-power-platform-capabilities/)App, mit der Systemleiter Klassenteams finden, virtuelle Kursräume finden und sich selbst oder andere zu diesen Kursteams für einen bestimmten Drop-In-Zeitraum hinzufügen können, je nach Bedarf.</span><span class="sxs-lookup"><span data-stu-id="cf35e-190">Classroom Drop-in is a Microsoft [Power Platform](https://powerapps.microsoft.com/blog/now-in-preview-customize-teams-with-built-in-power-platform-capabilities/)-based app that enables system leaders to find class teams, means virtual classrooms and add themselves or others to these class teams for a specified drop-in period, as needed.</span></span> <span data-ttu-id="cf35e-191">Die app built using Microsoft [Power Apps](/powerapps/powerapps-overview) and [Power Automate](/power-automate/getting-started), deeply integration in Microsoft Teams to ensure educational institute can optimize their operations in a hybrid learning environment by providing access to relevant stakeholders for class teams per business requirements.</span><span class="sxs-lookup"><span data-stu-id="cf35e-191">The app built using Microsoft [Power Apps](/powerapps/powerapps-overview) and [Power Automate](/power-automate/getting-started), deeply integrates with Microsoft Teams to ensure educational institutes can optimize their operations in a hybrid learning environment by providing access to relevant stakeholders for class teams per business requirements.</span></span>

[<span data-ttu-id="cf35e-192">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-192">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-classroom-dropin)

![Classroom-Drop-In-Anforderung](../assets/images/classroom-drop-in-request.png)

## <a name="company-communicator"></a><span data-ttu-id="cf35e-194">Unternehmens-Communicator</span><span class="sxs-lookup"><span data-stu-id="cf35e-194">Company Communicator</span></span>

<span data-ttu-id="cf35e-195">Die App Communicator ermöglicht Unternehmensteams das Erstellen und Senden von Nachrichten, die für mehrere Teams oder eine große Anzahl von Mitarbeitern im Chat vorgesehen sind, sodass die Organisation mitarbeiter direkt dort erreichen kann, wo sie zusammenarbeiten.</span><span class="sxs-lookup"><span data-stu-id="cf35e-195">The Company Communicator app enables corporate teams to create and send messages intended for multiple teams or large number of employees over chat allowing organization to reach employees right where they collaborate.</span></span> <span data-ttu-id="cf35e-196">Verwenden Sie diese Vorlage für mehrere Szenarien, z. B. Ankündigungen neuer Initiativen, Mitarbeiter-Onboarding, modernes Lernen und Entwickeln oder organisationsweite Übertragungen.</span><span class="sxs-lookup"><span data-stu-id="cf35e-196">Utilize this template for multiple scenarios such as new initiative announcements, employee onboarding, modern learning and development or organization-wide broadcasts.</span></span>

<span data-ttu-id="cf35e-197">Die App bietet eine einfache Schnittstelle für designierte Benutzer zum Erstellen, Anzeigen, Zusammenarbeiten und Senden von Nachrichten.</span><span class="sxs-lookup"><span data-stu-id="cf35e-197">The app provides an easy interface for designated users to create, preview, collaborate and send messages.</span></span>

<span data-ttu-id="cf35e-198">Es bietet eine Grundlage zum Erstellen benutzerdefinierter gezielter Kommunikationsfunktionen wie benutzerdefinierte Telemetrie, um zu erfahren, wie viele Benutzer eine Nachricht bestätigt oder mit dieser interagiert haben.</span><span class="sxs-lookup"><span data-stu-id="cf35e-198">It provides a foundation to build custom targeted communication capabilities such as custom telemetry on how many users acknowledged or interacted with a message.</span></span>

[<span data-ttu-id="cf35e-199">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-199">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-company-communicator-app)

![jCompany Communicator Verfassenfeldansicht](../assets/images/CompanyCommunicatorCompose.png)

## <a name="contact-group-lookup"></a><span data-ttu-id="cf35e-201">Nachschlageaktion für Kontaktgruppen</span><span class="sxs-lookup"><span data-stu-id="cf35e-201">Contact Group Lookup</span></span>

<span data-ttu-id="cf35e-202">Die App Contact Group Lookup bietet einen praktischen und nützlichen Ansatz zum Erstellen, Zugreifen auf und Verwalten der Kontaktgruppen Ihrer Organisation, die früher als Verteilerlisten oder Kommunikationsgruppen bezeichnet wurden.</span><span class="sxs-lookup"><span data-stu-id="cf35e-202">The Contact Group Lookup app provides a convenient and useful approach to creating, accessing, and managing your organization's contact groups, formerly known as distribution lists or communication groups.</span></span> <span data-ttu-id="cf35e-203">Benutzer können schnell Gruppenmitglieder anzeigen und chatten, den Mitgliederstatus anzeigen und einen Gruppenchat mit ausgewählten Mitgliedern in der Kontaktgruppe erstellen, und dies alles in der Teams-Umgebung.</span><span class="sxs-lookup"><span data-stu-id="cf35e-203">Users can quickly view and chat with group members, view member status, and create a group chat with selected members in the contact group, all within the Teams environment.</span></span>

[<span data-ttu-id="cf35e-204">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-204">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-app-contactgrouplookup)

:::row:::
:::column span="2":::
    ![Kontaktgruppen-Nachschlageansicht mit angehefteten Favoriten](../assets/images/contact-group-lookup-favorites.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Demo zum Starten des Chats mit der Kontaktgruppe suchen](../assets/images/contact-group-lookup-chat.png)
:::column-end:::
:::row-end:::

## <a name="co-worker-appreciation"></a><span data-ttu-id="cf35e-207">Kollegen danken</span><span class="sxs-lookup"><span data-stu-id="cf35e-207">Co-worker Appreciation</span></span> 

<span data-ttu-id="cf35e-208">Mithilfe der Vorlage "Kollegen-Bewertung" in Microsoft Teams können Benutzer die Erfolge ihrer Kollegen im Kontext von Teams erkennen.</span><span class="sxs-lookup"><span data-stu-id="cf35e-208">Using the co-worker appreciation template in Microsoft Teams, users can recognize their colleagues' achievements within the Teams’ context.</span></span> <span data-ttu-id="cf35e-209">Wenn Kollegen einen Kollegen belohnen, werden Empfänger und andere Teammitglieder in einer Kanalgespräch markiert und erhalten eine Benachrichtigung über die Preisdetails des Kanals.</span><span class="sxs-lookup"><span data-stu-id="cf35e-209">When co-workers select to reward a colleague, recipients and other team members are tagged in a channel conversation and they receive a notification about the channel's award details.</span></span> <span data-ttu-id="cf35e-210">Die Preise werden in der Teams-App aufgezeichnet, die sicher, portabel und einfach gemeinsam verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="cf35e-210">The awards are recorded in the Teams app, which is secure, portable, and easily shareable.</span></span> <span data-ttu-id="cf35e-211">Dies wird als powerApps-basierte Version der Open Badges-App-Vorlage mit einer Bestenliste betrachtet.</span><span class="sxs-lookup"><span data-stu-id="cf35e-211">This is considered as the PowerApps based version of the Open Badges app template, with a leaderboard.</span></span>

[<span data-ttu-id="cf35e-212">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-212">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-coworker-appreciation)

![Insgesamt](../assets/images/coworker-appreciation-1.png)

## <a name="crowdsourcer"></a><span data-ttu-id="cf35e-214">CrowdSourcer</span><span class="sxs-lookup"><span data-stu-id="cf35e-214">CrowdSourcer</span></span>

<span data-ttu-id="cf35e-215">CrowdSourcer ist ein [Microsoft Teams-Bot,](../bots/what-are-bots.md) der teams abgefragte Informationen zur Verfügung stellt, die gemeinsam von Gruppenmitgliedern stammen.</span><span class="sxs-lookup"><span data-stu-id="cf35e-215">CrowdSourcer is a [Microsoft Teams bot](../bots/what-are-bots.md) that gives teams queried information sourced collaboratively from group members.</span></span> <span data-ttu-id="cf35e-216">Es hilft dabei, häufig gestellte Fragen zu beantworten, während teilnehmer aktiv an einer unterhaltsamen und hilfreichen Informationsressource beteiligt werden können.</span><span class="sxs-lookup"><span data-stu-id="cf35e-216">It helps to answer frequently asked questions while enabling participants to actively engage in and contribute to a fun and helpful information resource.</span></span>

[<span data-ttu-id="cf35e-217">Abrufen auf Github</span><span class="sxs-lookup"><span data-stu-id="cf35e-217">Get it on Github</span></span>](https://github.com/OfficeDev/microsoft-teams-crowdsourcer-app)

![Crowdsource-Endbenutzerinteraktion](../assets/images/crowdsourcer.png)

## <a name="custom-stickers"></a><span data-ttu-id="cf35e-219">Custom Stickers</span><span class="sxs-lookup"><span data-stu-id="cf35e-219">Custom Stickers</span></span>

<span data-ttu-id="cf35e-220">Selbstausdruck ist der Kern einer gesunden Teamkultur.</span><span class="sxs-lookup"><span data-stu-id="cf35e-220">Self-expression is core to a healthy team culture.</span></span> <span data-ttu-id="cf35e-221">Diese App-Vorlage ist eine [Messagingerweiterung,](~/messaging-extensions/what-are-messaging-extensions.md) mit der Ihre Benutzer benutzerdefinierte Aufkleber und GIFs in Microsoft Teams verwenden können.</span><span class="sxs-lookup"><span data-stu-id="cf35e-221">This app template is a [messaging extension](~/messaging-extensions/what-are-messaging-extensions.md) that enables your users to use custom stickers and GIFs within Microsoft Teams.</span></span> <span data-ttu-id="cf35e-222">Diese Vorlage bietet eine einfache webbasierte Konfigurationserfahrung, bei der jeder benutzer mit Konfigurationszugriff die GIFs, Aufkleber und Bilder hochladen kann, die seine Benutzer haben möchten, sodass Ihr gesamtes Team alle von Ihnen festgelegten Aufkleber verwenden kann.</span><span class="sxs-lookup"><span data-stu-id="cf35e-222">This template provides an easy web-based configuration experience where anyone with configuration access can upload the GIFs, stickers, and images they want their users to have, allowing your entire team to use any set of stickers you choose.</span></span>

<span data-ttu-id="cf35e-223">Diese App ermöglicht auch die einfache Freigabe von Bildern, GIFs, Aufklebern in Teams ohne Zugriff auf SharePoint-Websites oder einzelne Kanäle als Speicher- und Freigabemechanismen.</span><span class="sxs-lookup"><span data-stu-id="cf35e-223">This app also enables easy sharing of images, GIFs, stickers across teams without needing access to SharePoint sites or individual channels as storage and sharing mechanisms.</span></span> <span data-ttu-id="cf35e-224">Beispielsweise können Produktteams Produktbilder und GIFs problemlos programmgesteuert für soziale Medien, Marketing- und Vertriebsteams freigeben.</span><span class="sxs-lookup"><span data-stu-id="cf35e-224">For example, product teams can easily share product images and GIFs to social media, marketing and sales teams programmatically.</span></span> <span data-ttu-id="cf35e-225">Sie können diese App auch erweitern, indem sie einen Benachrichtigungsfluss für bestimmte Teams oder Einzelpersonen auslöst, wenn neue Bilder und GIFs verfügbar gemacht werden.</span><span class="sxs-lookup"><span data-stu-id="cf35e-225">One can also extend this app by triggering a notification flow to specific teams or individuals when new images, and GIFs are made available.</span></span>

[<span data-ttu-id="cf35e-226">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-226">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-stickers-app)

![Aufkleber-App](../assets/images/stickers.png)

## <a name="employee-ideas"></a><span data-ttu-id="cf35e-228">Mitarbeiterideen</span><span class="sxs-lookup"><span data-stu-id="cf35e-228">Employee Ideas</span></span>

<span data-ttu-id="cf35e-229">Die Employee Ideas-App ist die PowerApps-Version der Azure-basierten App-Vorlage für großartige Ideen.</span><span class="sxs-lookup"><span data-stu-id="cf35e-229">The Employee Ideas app is the PowerApps version of the Azure based Great Ideas app template.</span></span> <span data-ttu-id="cf35e-230">Die App ermöglicht den Teams-Benutzern das Einrichten und Konfigurieren einer Ideenkampagne.</span><span class="sxs-lookup"><span data-stu-id="cf35e-230">The app enables the Teams users to set up and configure an idea campaign.</span></span> <span data-ttu-id="cf35e-231">Eine Ideenkampagne ist eine Kategorie zum Gruppieren von Ideen zu allgemeinen Designs.</span><span class="sxs-lookup"><span data-stu-id="cf35e-231">An idea campaign is a category for grouping ideas around common themes.</span></span>

<span data-ttu-id="cf35e-232">Teams-Benutzer können auch die folgenden Aktivitäten ausführen:</span><span class="sxs-lookup"><span data-stu-id="cf35e-232">Teams users can also perform the following activities:</span></span>

* <span data-ttu-id="cf35e-233">Konfigurieren Sie ein Standardübermittlungsformular, das Mitarbeiter für jede Idee übermitteln müssen.</span><span class="sxs-lookup"><span data-stu-id="cf35e-233">Configure a standard submission form that employees must submit for each idea.</span></span> 
* <span data-ttu-id="cf35e-234">Überprüfen und verwalten Sie die Ideen und die Liste der Kampagnen.</span><span class="sxs-lookup"><span data-stu-id="cf35e-234">Review and manage the ideas and list of campaigns.</span></span>
* <span data-ttu-id="cf35e-235">Ändern und Löschen von Kampagnen.</span><span class="sxs-lookup"><span data-stu-id="cf35e-235">Modify and delete campaigns.</span></span>
* <span data-ttu-id="cf35e-236">Überprüfen Sie Die Bestenlisten von Ideen.</span><span class="sxs-lookup"><span data-stu-id="cf35e-236">Review leader boards of ideas.</span></span>
* <span data-ttu-id="cf35e-237">Stimmen Sie für priorisierte Ideen ab, und teilen Sie sie.</span><span class="sxs-lookup"><span data-stu-id="cf35e-237">Vote for and share prioritized ideas.</span></span>
* <span data-ttu-id="cf35e-238">Übermitteln Sie Ideen für eine Kampagne.</span><span class="sxs-lookup"><span data-stu-id="cf35e-238">Submit ideas for a campaign.</span></span>
* <span data-ttu-id="cf35e-239">Sehen Sie sich die Idee eines anderen Teammitglieds an.</span><span class="sxs-lookup"><span data-stu-id="cf35e-239">View other team member's idea.</span></span>
* <span data-ttu-id="cf35e-240">Stimmen Sie über die am häufigsten gefallenen Ideen ab.</span><span class="sxs-lookup"><span data-stu-id="cf35e-240">Vote on most liked ideas.</span></span>
* <span data-ttu-id="cf35e-241">Überprüfen Sie die Leistung ihrer Ideen im Vergleich mit anderen innerhalb einer Kampagne.</span><span class="sxs-lookup"><span data-stu-id="cf35e-241">Review the performance of their ideas compared with others within a campaign.</span></span>

[<span data-ttu-id="cf35e-242">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-242">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-employeeideas)

![Verwalten der Kampagnenansicht](../assets/images/employee-ideas-manage-campaigns.png) 

## <a name="e-prescriptions"></a><span data-ttu-id="cf35e-244">E-Prescriptions</span><span class="sxs-lookup"><span data-stu-id="cf35e-244">E-Prescriptions</span></span> 

<span data-ttu-id="cf35e-245">E-Prescriptions ist eine [Power Apps-basierte](/powerapps/maker/canvas-apps/embed-teams-app) App, die die Telemedikierung und virtuelle Behandlung verbessert, indem der Prozess der Ausgabe von E-Rezepten für Patienten automatisiert wird.</span><span class="sxs-lookup"><span data-stu-id="cf35e-245">E-Prescriptions is a [Power Apps](/powerapps/maker/canvas-apps/embed-teams-app) based app that enhances telemedicine and virtual care by automating the process of issuing e-prescriptions to patients.</span></span> <span data-ttu-id="cf35e-246">Medizinische Experten können Termine schnell überprüfen, E-Rezepte generieren und E-Mails mit E-Rezept-Anlagen direkt innerhalb der Teams-Plattform an Patienten senden.</span><span class="sxs-lookup"><span data-stu-id="cf35e-246">Medical professionals can quickly review appointments, generate e-prescriptions, and send emails with e-prescription attachments to patients directly within the Teams platform.</span></span>

[<span data-ttu-id="cf35e-247">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-247">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-eprescription) 

:::row:::
:::column span="2":::
    ![Screenshot der E-Prescriptions-App.](../assets/images/e-prescriptions-app-template.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Screenshot der E-Prescriptions-App.](../assets/images/e-prescriptions-app-template-admin.png)
:::column-end:::
:::row-end:::

## <a name="employee-training"></a><span data-ttu-id="cf35e-252">Mitarbeiterschulungen</span><span class="sxs-lookup"><span data-stu-id="cf35e-252">Employee Training</span></span> 

<span data-ttu-id="cf35e-253">Mitarbeiterschulung ist eine Microsoft Teams-App, mit der Organisatoren Lern- und Schulungsereignisse für Ihre Organisation einfach veröffentlichen, nachverfolgen und bewerben können.</span><span class="sxs-lookup"><span data-stu-id="cf35e-253">Employee training is a Microsoft Teams app that enables organizers to easily publish, track, and promote learning and training events for your organization.</span></span>  <span data-ttu-id="cf35e-254">Mit der App können Ereignisplaner Erinnerungen und Benachrichtigungen an Ereignisregistranten senden, und Mitarbeiter können Interesse an bevorstehenden Ereignissen anzeigen, über die Teams-Messagingerweiterung aktuelle Ereignisse aktualisieren und Ereignisdetails mit Kollegen teilen.</span><span class="sxs-lookup"><span data-stu-id="cf35e-254">With the app, event planners can send reminders and notifications to event registrants and employees can indicate interest in upcoming events, stay updated on current events, and share event details with colleagues through the Teams messaging extension.</span></span>

[<span data-ttu-id="cf35e-255">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-255">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-employeetraining)

:::row:::
:::column span="2":::
    <span data-ttu-id="cf35e-256">**Anzeigen von Schulungsereignissen für Mitarbeiter** ![ Registerkartenbild für Mitarbeiterschulungen](../assets/images/employee-training-discover-tab.png)</span><span class="sxs-lookup"><span data-stu-id="cf35e-256">**View employee training events** ![Employee training tab image](../assets/images/employee-training-discover-tab.png)</span></span>  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    <span data-ttu-id="cf35e-257">**Erstellen eines Schulungsereigniss für Mitarbeiter** ![ Formular zum Erstellen eines Ereignisformulars für Mitarbeiterschulungen](../assets/images/employee-training-create-event.jpg)</span><span class="sxs-lookup"><span data-stu-id="cf35e-257">**Create employee training event** ![Employee training create event form](../assets/images/employee-training-create-event.jpg)</span></span>
:::column-end:::
:::row-end:::

## <a name="expert-finder"></a><span data-ttu-id="cf35e-258">Experten-Finder</span><span class="sxs-lookup"><span data-stu-id="cf35e-258">Expert Finder</span></span>

<span data-ttu-id="cf35e-259">Der Experten-Finder ist ein [Microsoft Teams-Bot,](../bots/what-are-bots.md) der bestimmte Organisationsmitglieder basierend auf ihren Fähigkeiten, Interessen und Bildungsattributen identifiziert.</span><span class="sxs-lookup"><span data-stu-id="cf35e-259">Expert Finder is a [Microsoft Teams bot](../bots/what-are-bots.md) that identifies specific organization members based on their skills, interests, and education attributes.</span></span> <span data-ttu-id="cf35e-260">Mitglieder finden Experten in einer Organisation, die einer Stichwortsuche von Azure Active Directory-Benutzerprofilen entsprechen.</span><span class="sxs-lookup"><span data-stu-id="cf35e-260">Members find experts within an organization that match a keyword search of Azure Active Directory user profiles.</span></span>

[<span data-ttu-id="cf35e-261">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-261">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-expertfinder)

![Demo zu Suchergebnissen der Expertensuche](../assets/images/expert-finder.png)

## <a name="faq-plus"></a><span data-ttu-id="cf35e-263">FAQ Plus</span><span class="sxs-lookup"><span data-stu-id="cf35e-263">FAQ Plus</span></span>

<span data-ttu-id="cf35e-264">Conversational Q&A bots sind eine einfache Möglichkeit, Antworten auf häufig gestellte Fragen von Benutzern zu geben.</span><span class="sxs-lookup"><span data-stu-id="cf35e-264">Conversational Q&A bots are an easy way to provide answers to frequently asked questions by users.</span></span> <span data-ttu-id="cf35e-265">Die meisten Bots können jedoch nicht sinnvoll mit Benutzern interagieren, da kein Mensch in der Schleife ist, wenn der Bot ausfällt.</span><span class="sxs-lookup"><span data-stu-id="cf35e-265">But, most bots fail to engage with users in meaningful way because there is no human in the loop when the bot fails.</span></span> <span data-ttu-id="cf35e-266">Der FAQ-Bot ist ein&Ein Bot, der einen Menschen in die Schleife bringt, wenn er nicht helfen kann.</span><span class="sxs-lookup"><span data-stu-id="cf35e-266">FAQ bot is a friendly Q&A bot that brings a human in the loop when it is unable to help.</span></span> <span data-ttu-id="cf35e-267">Man kann dem Bot eine Frage stellen, und der Bot antwortet mit einer Antwort, wenn er in der Wissensdatenbank enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="cf35e-267">One can ask the bot a question and the bot responds with an answer if it is contained in the knowledge base.</span></span> <span data-ttu-id="cf35e-268">Andern falls nicht, ermöglicht der Bot dem Benutzer das Senden einer Abfrage, die dann an ein vorkonfiguriertes Expertenteam gesendet wird, das bei der Unterstützung hilft, indem er auf die Benachrichtigungen innerhalb des Teams selbst einwirken kann.</span><span class="sxs-lookup"><span data-stu-id="cf35e-268">If not, the bot allows the user to submit a query which then gets posted to a pre-configured team of experts who help to provide support by acting upon the notifications from within the team itself.</span></span>

> [!NOTE]
> <span data-ttu-id="cf35e-269">Die neueste Version von **FAQ Plus** unterstützt verbesserte Lösungen&Fragen und Antworten, da ein Expertenteam folgendes abschließen kann:</span><span class="sxs-lookup"><span data-stu-id="cf35e-269">The latest release of **FAQ Plus** supports improved Q&A resolutions by enabling a team of experts to complete the following:</span></span>
>
> <span data-ttu-id="cf35e-270">&#x2714; Hinzufügen neuer Fragen&Direkt zur Wissensdatenbank mithilfe von Nachrichtenerweiterungen.</span><span class="sxs-lookup"><span data-stu-id="cf35e-270">&#x2714; Add new Q&As directly to the knowledge base using message extensions.</span></span>
>
> <span data-ttu-id="cf35e-271">&#x2714; Bearbeiten und Löschen von&Ein Paar, das von einem Bot hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="cf35e-271">&#x2714; Edit and delete Q&A pairs added by a bot.</span></span>
>
> <span data-ttu-id="cf35e-272">&#x2714; Verfolgen des Überarbeitungsverlaufs von Q&As.</span><span class="sxs-lookup"><span data-stu-id="cf35e-272">&#x2714; Track the revision history of Q&As.</span></span>
>
> <span data-ttu-id="cf35e-273">&#x2714; Konfigurieren sie eine Antwort mit zusätzlichen Details, die als adaptive [Karte angezeigt werden.](../task-modules-and-cards/cards/cards-reference.md#adaptive-card)</span><span class="sxs-lookup"><span data-stu-id="cf35e-273">&#x2714; Configure an answer with additional details to display as an [Adaptive Card](../task-modules-and-cards/cards/cards-reference.md#adaptive-card).</span></span>
>
[<span data-ttu-id="cf35e-274">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-274">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-faqplusv2)

![FAQ Plus GIF](../assets/images/FAQPlusEndUser.gif)

## <a name="get-support-app"></a><span data-ttu-id="cf35e-276">Support-App erhalten</span><span class="sxs-lookup"><span data-stu-id="cf35e-276">Get Support App</span></span>

<span data-ttu-id="cf35e-277">Die App Support anfordern wird von Organisationen verwendet, die Microsoft Teams verwenden, um allen Benutzern die Möglichkeit zu ermöglichen, Unterstützung von Vorgesetzten an zu fordern.</span><span class="sxs-lookup"><span data-stu-id="cf35e-277">The Get Support app is used by organizations that are using Microsoft Teams, to enable any set of users to request assistance from supervisors.</span></span> <span data-ttu-id="cf35e-278">Diese App umfasst die folgenden Features:</span><span class="sxs-lookup"><span data-stu-id="cf35e-278">This app includes the following features:</span></span>
* <span data-ttu-id="cf35e-279">Anfordern von Unterstützung für verschiedene Kategorien von einer Power App.</span><span class="sxs-lookup"><span data-stu-id="cf35e-279">Requesting assistance on different categories from a Power App.</span></span>
* <span data-ttu-id="cf35e-280">Benachrichtigungen, die an Ansenden gesendet werden, die sie darüber informieren, wem der Hase zugewiesen ist.</span><span class="sxs-lookup"><span data-stu-id="cf35e-280">Notifications sent to requestors informing them of who hare assigned.</span></span>
* <span data-ttu-id="cf35e-281">Benachrichtigungen, die an zugewiesene Vorgesetzte gesendet werden und sie darüber informieren, wer Unterstützung benötigt.</span><span class="sxs-lookup"><span data-stu-id="cf35e-281">Notifications sent to assigned supervisors informing them of who needs assistance.</span></span> 
* <span data-ttu-id="cf35e-282">Analysieren von Eskalationen und Mustern in SharePoint und PowerBI.S</span><span class="sxs-lookup"><span data-stu-id="cf35e-282">Analyzing escalations and patterns in SharePoint and PowerBI.S</span></span>

[<span data-ttu-id="cf35e-283">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-283">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-app-get-support/)

![Support gif erhalten](../assets/images/get-support.gif)

## <a name="goal-tracker"></a><span data-ttu-id="cf35e-285">Zielverfolgung</span><span class="sxs-lookup"><span data-stu-id="cf35e-285">Goal Tracker</span></span>

<span data-ttu-id="cf35e-286">Die Zielverfolgungs-App ist eine umfassende Lösung für Ihre Organisation, um das Einrichten von Zielen, die Beobachtung des Fortschritts und den Erfolg in Microsoft Teams zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="cf35e-286">The Goal Tracker app is a comprehensive solution for your organization to support establishing goals, observing progress, and acknowledging success within Microsoft Teams.</span></span> <span data-ttu-id="cf35e-287">Die App ermöglicht Benutzern das Festlegen, Nachverfolgen und Aktualisieren von Zielen auf professioneller, persönlicher und Teamebene.</span><span class="sxs-lookup"><span data-stu-id="cf35e-287">The app enables users to set, track, and update objectives on a professional, personal, and team level.</span></span> <span data-ttu-id="cf35e-288">Teammitglieder erhalten außerdem rechtzeitige Erinnerungen und Statusupdates, um konzentriert zu bleiben und auf dem richtigen Weg zu bleiben.</span><span class="sxs-lookup"><span data-stu-id="cf35e-288">Team members also receive timely reminders and status updates to remain focused and stay on track.</span></span>

[<span data-ttu-id="cf35e-289">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-289">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-app-goaltracker)

:::row:::
  :::column span="2":::
    ![Festlegen von Zielen](../assets/images/goal-tracker-set-goals-view.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Anzeigen von Festgelegten Zielen](../assets/images/goal-tracker-your-goals-view.png)
:::column-end:::
:::row-end:::

## <a name="great-ideas"></a><span data-ttu-id="cf35e-292">Großartige Ideen</span><span class="sxs-lookup"><span data-stu-id="cf35e-292">Great Ideas</span></span>

<span data-ttu-id="cf35e-293">Die Great Ideas-App unterstützt und fördert Innovation und Kreativität in Ihrer Organisation.</span><span class="sxs-lookup"><span data-stu-id="cf35e-293">The Great Ideas app supports and empowers innovation and creativity within your organization.</span></span> <span data-ttu-id="cf35e-294">Die App ermöglicht Es Ihren Mitarbeitern, Ideen mit Kollegen und Führungskräften auszutauschen, neue Übermittlungen zu entdecken, Beiträge zur Peer-Überlegung ins Rampenlicht zu stellen und ihre Stimme für die besten Vorschläge in Microsoft Teams zu geben.</span><span class="sxs-lookup"><span data-stu-id="cf35e-294">The app enables your employees to share ideas with colleagues and leadership, discover new submissions, spotlight contributions for peer consideration, and cast their vote for the best proposals within Microsoft Teams.</span></span>

[<span data-ttu-id="cf35e-295">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-295">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-greatideas)

:::row:::
  :::column span="2":::
    ![Anzeigen übermittelter Ideen](../assets/images/great-ideas-all-view.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Anzeigen von Ideen](../assets/images/great-ideas-digest-view.png)
:::column-end:::
:::row-end:::

## <a name="group-activities"></a><span data-ttu-id="cf35e-298">Gruppenaktivitäten</span><span class="sxs-lookup"><span data-stu-id="cf35e-298">Group Activities</span></span>

<span data-ttu-id="cf35e-299">Gruppenaktivitäten ist eine Microsoft Teams-App, mit der Teambesitzer schnell Aktivitätsgruppen erstellen und Workflows für die Zusammenarbeit im Kontext von Microsoft Teams verwalten können.</span><span class="sxs-lookup"><span data-stu-id="cf35e-299">Group Activities is a Microsoft Teams app that makes it easy for team owners to quickly create activity groups and manage collaboration workflows within the context of Microsoft Teams.</span></span> <span data-ttu-id="cf35e-300">Aktivitätsautoren können Aktivitäten erstellen, Teammitglieder zufällig in Gruppen verteilen und optional vom Bot Erinnerungen senden, bis die Aktivitäten abgeschlossen sind.</span><span class="sxs-lookup"><span data-stu-id="cf35e-300">Activity authors are enabled to create activities, randomly distribute team members in groups, and optionally have the bot send reminders until activities are complete.</span></span>

[<span data-ttu-id="cf35e-301">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-301">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-groupactivities)

:::row:::
  :::column span="2":::
    ![Liste der Gruppenaktivitäten in Teams](../assets/images/group-activities-1.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Gruppenaktivitätsbenachrichtigung in einem Kanal](../assets/images/group-activities-2.png)
:::column-end:::
:::row-end:::

## <a name="grow-your-skills"></a><span data-ttu-id="cf35e-304">Erweitern Sie Ihre Fähigkeiten</span><span class="sxs-lookup"><span data-stu-id="cf35e-304">Grow Your Skills</span></span>

<span data-ttu-id="cf35e-305">Die App Grow Your Skills unterstützt professionelles Wachstum und Entwicklung, indem Mitarbeiter an ergänzenden Projekten für Ihre Organisation beitragen und gleichzeitig neue Fähigkeiten erlernen können.</span><span class="sxs-lookup"><span data-stu-id="cf35e-305">The Grow Your Skills app supports professional growth and development by enabling employees to contribute to supplemental projects for your organization while simultaneously learning new skills.</span></span> <span data-ttu-id="cf35e-306">Mitarbeiter können die App verwenden, um Möglichkeiten zu finden, die ihren Interessen entsprechen, eine sinnvolle Zusammenarbeit mit Kollegen zu genießen und neue Kompetenz- und Funktionenstufen zu erwerben, und dies alles in der Teams-Umgebung.</span><span class="sxs-lookup"><span data-stu-id="cf35e-306">Employees can use the app to locate opportunities that meet their interests, enjoy meaningful collaboration with peers, and acquire new levels of expertise and capabilities, all within the Teams environment.</span></span>

[<span data-ttu-id="cf35e-307">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-307">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-growyourskills)

:::row:::
  :::column span="2":::
    ![Ansicht "Verfügbare Projekte"](../assets/images/grow-your-skills-all-projects-view.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Ansicht der erworbenen Fähigkeiten des Betrachters](../assets/images/grow-your-skills-acquired-skills-view.png)
:::column-end:::
:::row-end:::

## <a name="hr-support"></a><span data-ttu-id="cf35e-310">HR Support</span><span class="sxs-lookup"><span data-stu-id="cf35e-310">HR Support</span></span>

<span data-ttu-id="cf35e-311">Hr Support bot ist ein benutzerfreundlicher Q&Ein Bot, der einen Supportexperten oder Experten aus dem Personalteam in die Schleife bringt, wenn er nicht helfen kann.</span><span class="sxs-lookup"><span data-stu-id="cf35e-311">HR Support bot is a friendly Q&A bot that brings a support professional or expert from the HR team in the loop when it is unable to help.</span></span> <span data-ttu-id="cf35e-312">Man kann dem Bot eine Frage stellen, und der Bot antwortet mit einer Antwort, wenn er in der Wissensdatenbank enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="cf35e-312">One can ask the bot a question and the bot responds with an answer if it is contained in the knowledge base.</span></span> <span data-ttu-id="cf35e-313">Andern falls nicht, ermöglicht der Bot dem Benutzer das Senden einer Abfrage, die dann in einem vorkonfigurierten Expertenteam veröffentlicht wird, das unterstützungshilfen kann, indem er auf die Benachrichtigungen innerhalb des Teams selbst einwirken kann.</span><span class="sxs-lookup"><span data-stu-id="cf35e-313">If not, the bot allows the user to submit a query which then gets posted in a pre-configured team of experts who are help to provide support by acting upon the notifications from within their team itself.</span></span> <span data-ttu-id="cf35e-314">Darüber hinaus schlägt der Bot Links zu empfohlenen Personalrichtlinien oder Fragen vor, indem er nach vorkonfigurierten Tags in der Frage sucht.</span><span class="sxs-lookup"><span data-stu-id="cf35e-314">Additionally, the bot suggests links to recommended HR policies or questions by searching for pre-configured tags in the question.</span></span> <span data-ttu-id="cf35e-315">Diese Kacheln finden Sie auf der zugeordneten Registerkarte als Kurzübersicht.</span><span class="sxs-lookup"><span data-stu-id="cf35e-315">These tiles are found in the associated tab as a quick reference.</span></span> <span data-ttu-id="cf35e-316">Der Personalsupport funktioniert gut für einfache Fragen&A und schnelle Unterstützung beim Starten neuer Projekte oder Initiativen in der Organisation.</span><span class="sxs-lookup"><span data-stu-id="cf35e-316">HR Support works well for light weight Q&A and to provide quick support when launching new projects or initiatives in the organization.</span></span>

[<span data-ttu-id="cf35e-317">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-317">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-hrsupport-app)

![HR Support](../assets/images/expert-user.png)

## <a name="icebreaker"></a><span data-ttu-id="cf35e-319">Icebreaker</span><span class="sxs-lookup"><span data-stu-id="cf35e-319">Icebreaker</span></span>

<span data-ttu-id="cf35e-320">Icebreaker ist ein [Microsoft Teams-Bot,](../bots/what-are-bots.md) der Ihrem Team dabei hilft, sich näher zu kommen, indem jede Woche zwei zufällige Teammitglieder zusammengekoppelt werden, um sich zu treffen.</span><span class="sxs-lookup"><span data-stu-id="cf35e-320">Icebreaker is a [Microsoft Teams bot](../bots/what-are-bots.md) that helps your team get closer by pairing two random team members up every week to meet.</span></span> <span data-ttu-id="cf35e-321">Der Bot vereinfacht die Planung, indem er automatisch kostenlose Zeiten vor schlägt, die für beide Mitglieder funktionieren.</span><span class="sxs-lookup"><span data-stu-id="cf35e-321">The bot makes scheduling easy by automatically suggesting free times that work for both members.</span></span> <span data-ttu-id="cf35e-322">Stärken Sie persönliche Verbindungen, und erstellen Sie mit dieser App eine engmaschige Community.</span><span class="sxs-lookup"><span data-stu-id="cf35e-322">Strengthen personal connections and build a tightly knit community with this app.</span></span>

<span data-ttu-id="cf35e-323">Die Icebreaker-App fördert nicht nur persönliche Verbindungen im gesamten Team, sondern kann auch dazu beitragen, interessenbasierte Communitys in Ihrer Organisation zu pflegen.</span><span class="sxs-lookup"><span data-stu-id="cf35e-323">In addition to encouraging personal connections across your entire team, the Icebreaker app can help cultivate interest-based communities within your organization.</span></span> <span data-ttu-id="cf35e-324">Sie können diese App beispielsweise für eine DevOps-Interessengruppe verwenden, um Ideen und bewährte Methoden zu unterstützen, die organisch in Ihrer Organisation verteilt werden.</span><span class="sxs-lookup"><span data-stu-id="cf35e-324">For example, you can use this app for a DevOps interest group to help ideas and best practices organically spread across your organization.</span></span>

[<span data-ttu-id="cf35e-325">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-325">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-icebreaker-app)

![Icebreaker-App](../assets/images/icebreaker.png)

## <a name="incentives"></a><span data-ttu-id="cf35e-327">Incentives</span><span class="sxs-lookup"><span data-stu-id="cf35e-327">Incentives</span></span>

<span data-ttu-id="cf35e-328">Incentives ist eine [Power Apps-Vorlage,](/powerapps/maker/canvas-apps/embed-teams-app) die die incentivierte Beteiligung von Mitarbeitern an bestimmten Aktivitäten wie Schulungen und Änderungsmanagement-Initiativen verwaltet und verfolgt.</span><span class="sxs-lookup"><span data-stu-id="cf35e-328">Incentives is a [Power Apps](/powerapps/maker/canvas-apps/embed-teams-app) template that manages and tracks incentivized employee participation in designated activities, such as trainings and change management initiatives.</span></span> <span data-ttu-id="cf35e-329">Administratoren verwenden die App, um bestimmte Aktivitäten festzulegen, Punkte für den Abschluss zuzuordnen und erforderliche Berechtigungspunktstufen für Prämien anzugeben.</span><span class="sxs-lookup"><span data-stu-id="cf35e-329">Admins use the app to establish designated activities, assign points for completion, and specify required eligibility point levels for rewards.</span></span> <span data-ttu-id="cf35e-330">Mitarbeiter verwenden die App, um ihre gesammelten Punkte zu anzeigen und nach Erreichen der Berechtigung einlösbare Prämien anfordern und beanspruchen.</span><span class="sxs-lookup"><span data-stu-id="cf35e-330">Employees use the app to view their accumulated points and, upon reaching eligibility, request and claim redeemable rewards.</span></span>

[<span data-ttu-id="cf35e-331">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-331">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-incentives)

![Incentives-App-Demo](../assets/images/incentives-app.png)

## <a name="incident-reporter"></a><span data-ttu-id="cf35e-333">Incident Reporter</span><span class="sxs-lookup"><span data-stu-id="cf35e-333">Incident Reporter</span></span>

<span data-ttu-id="cf35e-334">Incident Reporter ist ein [Microsoft Teams-Bot,](../bots/what-are-bots.md)  der die Verwaltung von Vorfällen in Ihrer Organisation optimiert.</span><span class="sxs-lookup"><span data-stu-id="cf35e-334">Incident Reporter is a [Microsoft Teams bot](../bots/what-are-bots.md)  that optimizes the management of incidents in your organization.</span></span> <span data-ttu-id="cf35e-335">Der Bot vereinfacht die automatisierte Erfassung von Vorfalldaten, angepasste Vorfallberichte, relevante Benachrichtigungen von Betroffenen und die End-to-End-Nachverfolgung von Vorfällen.</span><span class="sxs-lookup"><span data-stu-id="cf35e-335">The bot facilitates automated incident data collection, customized incident reports, relevant stakeholder notifications, and end-to-end incident tracking.</span></span>

[<span data-ttu-id="cf35e-336">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-336">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-incidentreport)

:::row:::
  :::column span="2":::
    ![Vorfallberichts-Gruppenbereichsansicht](../assets/images/incident-reporter-02.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Persönliche Bereichsansicht des Incident Reporters](../assets/images/incident-reporter-01.jpg)
:::column-end:::
:::row-end:::

## <a name="inspection"></a><span data-ttu-id="cf35e-339">Inspektion</span><span class="sxs-lookup"><span data-stu-id="cf35e-339">Inspection</span></span> 

 <span data-ttu-id="cf35e-340">Bei der Überprüfung handelt es sich um eine Microsoft Teams-App, mit der Mitarbeiter an der Frontlinie alles von Standorten bis hin zu Ressourcen und Geräten überprüfen können.</span><span class="sxs-lookup"><span data-stu-id="cf35e-340">Inspection is a Microsoft Teams app that enables front line workers to inspect anything from  locations to assets and equipments.</span></span> <span data-ttu-id="cf35e-341">Beispielsweise ein Einzelhandelsgeschäft, eine Produktionsanlage oder Fahrzeuge und Maschinen.</span><span class="sxs-lookup"><span data-stu-id="cf35e-341">For example, a retail store, manufacturing plant, or vehicles and machines.</span></span> <span data-ttu-id="cf35e-342">Diese Lösung bietet zwei Apps, die jeweils für verschiedene Benutzertypen vorgesehen sind.</span><span class="sxs-lookup"><span data-stu-id="cf35e-342">There are two apps in this solution, each intended for different types of users.</span></span>

<span data-ttu-id="cf35e-343">Die App ermöglicht es den Front-Line-Mitarbeitern, eine Ressource oder einen Bereich zu prüfen, die Qualität von Produkten und Diensten zu verwalten oder die Sicherheit am Arbeitsplatz zu gewährleisten.</span><span class="sxs-lookup"><span data-stu-id="cf35e-343">The app empowers the front line workers to inspect an asset or area, to manage quality of products and services, or maintain safety at workplace.</span></span> <span data-ttu-id="cf35e-344">Es erleichtert die Kommunikation zwischen Teammitgliedern, um Probleme zu beheben, die während der Überprüfung gefunden wurden.</span><span class="sxs-lookup"><span data-stu-id="cf35e-344">It facilitates communication between team members to address issues found during inspection.</span></span> <span data-ttu-id="cf35e-345">Die App bietet einfachen Berichten für Manager, um die Problembe beheben zu beschleunigen und Trends zu markieren.</span><span class="sxs-lookup"><span data-stu-id="cf35e-345">The app provides simple reports for managers to expedite issue resolution and highlight trends.</span></span>

[<span data-ttu-id="cf35e-346">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-346">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-inspection)

 ![Übersicht über die Überprüfung](../assets/images/inspection-app.png)  


## <a name="issue-reporting"></a><span data-ttu-id="cf35e-348">Problemberichterstattung</span><span class="sxs-lookup"><span data-stu-id="cf35e-348">Issue Reporting</span></span>

<span data-ttu-id="cf35e-349">Die Problemberichts-App ermöglicht es Den Mitarbeitern und Vorgesetzten, Probleme auf- und zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="cf35e-349">The Issue Reporting app empowers the employees and managers to raise and manage issues.</span></span> <span data-ttu-id="cf35e-350">Es besteht aus zwei Apps: Issue reporting app for reporting issues und Manage Issues app for managing issues.</span><span class="sxs-lookup"><span data-stu-id="cf35e-350">It consists of two apps, Issue reporting app for reporting issues and Manage Issues app for managing issues.</span></span>

<span data-ttu-id="cf35e-351">Die Teammanager verwenden die App Probleme verwalten, um die App zu konfigurieren, einschließlich des Kanals, in dem Microsoft Teams-Nachrichten und Planner-Aufgaben von der App erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="cf35e-351">The team managers use the Manage Issues app to configure the app experience, including the channel in which Microsoft Teams messages and Planner tasks are created by the app.</span></span> <span data-ttu-id="cf35e-352">Manager verwenden die App auch, um Vorlagenformulare zu erstellen, um Details zu sammeln, wenn ein Benutzer ein Problem meldet.</span><span class="sxs-lookup"><span data-stu-id="cf35e-352">Managers also use the app to create template forms to collect details when a user reports an issue.</span></span> <span data-ttu-id="cf35e-353">Beispiel: Überprüfen, Bearbeiten oder Löschen von Formularen für Problemvorlagen.</span><span class="sxs-lookup"><span data-stu-id="cf35e-353">For example, review, edit, or delete issue template forms.</span></span> <span data-ttu-id="cf35e-354">Die App wird auch verwendet, um Teamprobleme zu überprüfen, über den Problemverlauf zu berichten und die Problemlösung effizient zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="cf35e-354">The app is also used to review team issues, report on issue history, and efficiently manage issue resolution.</span></span>

<span data-ttu-id="cf35e-355">Die Mitarbeiter verwenden die Problemberichts-App, um Probleme und Details zu protokollieren, die zur Behebung dieser Probleme erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="cf35e-355">The employees use the Issue reporting app to log issues and details required to resolve them.</span></span> <span data-ttu-id="cf35e-356">Die App wird auch verwendet, um vorhandene Probleme zu ändern und zu beheben und eine hohe Ansicht von individuellen oder Teamproblemen zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="cf35e-356">The app is also used to modify and resolve existing issues and get a high-level view of individual or team issues.</span></span>

[<span data-ttu-id="cf35e-357">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-357">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-issuereporting)

![Teamansicht für die Problemberichterstattung](../assets/images/issue-reporting-team-view.png)  

## <a name="new-employee-onboarding"></a><span data-ttu-id="cf35e-359">Onboarding neuer Mitarbeiter</span><span class="sxs-lookup"><span data-stu-id="cf35e-359">New Employee Onboarding</span></span> 

<span data-ttu-id="cf35e-360">Das Onboarding neuer Mitarbeiter ist eine integrierte Microsoft Teams- und [SharePoint New Employee Onboarding-Lösung,](https://lookbook.microsoft.com/details/75e60a32-9849-4ed4-b83e-b2b08983ad19) mit der Ihre Organisation eine konsistente, qualitativ hochwertige Onboardingerfahrung für Mitarbeiter auf ihrer Neueinstellungen-Reise bereitstellen kann.</span><span class="sxs-lookup"><span data-stu-id="cf35e-360">New Employee Onboarding is an integrated Microsoft Teams and [SharePoint New Employee Onboarding Solution](https://lookbook.microsoft.com/details/75e60a32-9849-4ed4-b83e-b2b08983ad19) that enables your organization to provide a consistent, high-quality onboarding experience for employees on their new-hire journey.</span></span> <span data-ttu-id="cf35e-361">Die App wird von Personalteams und Einstellungsmanagern verwendet, um während des gesamten Orientierungs- und Einführungsprozesses relevante Informationen zur Verfügung zu stellen, sowie von Neueinstellungen, um Feedback zu teilen, Einführungen zu geben und Onboardingaufgaben auszuführen.</span><span class="sxs-lookup"><span data-stu-id="cf35e-361">The app is used by human resource teams and hiring managers to provide relevant information throughout the orientation and induction process and by new hires to share feedback, provide introductions, and complete onboarding tasks.</span></span>

[<span data-ttu-id="cf35e-362">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-362">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-newemployeeonboarding)

:::row:::
  :::column span="2":::
    <span data-ttu-id="cf35e-363">**Willkommenskarte für neue Mitarbeiter** ![ Abbildung der Willkommenskarte für neue Mitarbeiter](../assets/images/new-employee-welcome-card.png)</span><span class="sxs-lookup"><span data-stu-id="cf35e-363">**New employee welcome card** ![Image of new employee welcome card](../assets/images/new-employee-welcome-card.png)</span></span>
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    <span data-ttu-id="cf35e-364">**Prüfliste für neue Mitarbeiter** ![ Abbildung der Prüfliste für neue Mitarbeiter](../assets/images/new-employee-checklist.png)</span><span class="sxs-lookup"><span data-stu-id="cf35e-364">**New employee checklist** ![Image of new employee checklist](../assets/images/new-employee-checklist.png)</span></span>  
:::column-end:::
:::row-end:::

## <a name="open-badges"></a><span data-ttu-id="cf35e-365">Öffnen von Signalen</span><span class="sxs-lookup"><span data-stu-id="cf35e-365">Open Badges</span></span>

<span data-ttu-id="cf35e-366">Open Badges ist eine Microsoft Teams-App, mit der Einzelpersonen digitale Lernanmeldeinformationen innerhalb des Teams-Kontexts erwerben und überall freigeben können.</span><span class="sxs-lookup"><span data-stu-id="cf35e-366">Open Badges is a Microsoft Teams app that enables individuals to earn digital learning credential badges within the Teams context and share them everywhere.</span></span> <span data-ttu-id="cf35e-367">Mithilfe von Funktionen der Drittanbieter-Zertifizierungsstelle für digitale Badges, [Badgr](https://badgr.org/), werden die ausgezeichneten Badges im Badgr-Profil eines Empfängers aufgezeichnet und können ein umfassendes Bild von Lebenserfahrungen erstellen und freigeben.</span><span class="sxs-lookup"><span data-stu-id="cf35e-367">Using capabilities from the third-party digital badge issuing authority, [Badgr](https://badgr.org/), awarded badges are recorded in a recipient's Badgr profile and available to build and share a rich picture of lifetime learning journeys.</span></span>

[<span data-ttu-id="cf35e-368">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-368">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-openbadges)

:::row:::
  :::column span="2":::
    ![Abbildung der verfügbaren Signalen](../assets/images/open-badges-1.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Ansicht "Vergebene Badges"](../assets/images/open-badges-2.png)
:::column-end:::
:::row-end:::

## <a name="poll"></a><span data-ttu-id="cf35e-371">Umfrage</span><span class="sxs-lookup"><span data-stu-id="cf35e-371">Poll</span></span> 

<span data-ttu-id="cf35e-372">Poll ist eine [](../messaging-extensions/what-are-messaging-extensions.md) benutzerdefinierte Microsoft Teams-Messaging-Erweiterungs-App, mit der Sie in einem Chat oder kanal schnell Umfragen erstellen und senden können, um Teammeinungen und -einstellungen zu sammeln.</span><span class="sxs-lookup"><span data-stu-id="cf35e-372">Poll is a custom Microsoft Teams [messaging extension](../messaging-extensions/what-are-messaging-extensions.md) app that enables you to quickly create and send polls in a chat or a channel to gather team opinions and preferences.</span></span> <span data-ttu-id="cf35e-373">Die App wird auf allen Microsoft Teams-Plattformclients unterstützt, z. B. Desktop, Browser, iOS und Android, und ist für die Bereitstellung im Rahmen Ihres Microsoft 365-Abonnements bereit.</span><span class="sxs-lookup"><span data-stu-id="cf35e-373">The app is supported across all Teams platform clients, such as desktop, browser, iOS, and Android and is ready for deployment as part of your Microsoft 365 subscription.</span></span>

[<span data-ttu-id="cf35e-374">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-374">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-poll-app)

:::row:::
  :::column span="1":::
    ![Erstellen von Umfragen in der Teams-Ansicht](../assets/images/poll-app-template-compose-view.gif)  
:::column-end:::
:::row-end:::

## <a name="quick-responses"></a><span data-ttu-id="cf35e-376">Schnelle Antworten</span><span class="sxs-lookup"><span data-stu-id="cf35e-376">Quick Responses</span></span>

<span data-ttu-id="cf35e-377">Quick Responses ist eine Microsoft Teams-App, die eine stabile Lösung für die effektive Beantwortung häufig gestellter Fragen von Benutzern bietet.</span><span class="sxs-lookup"><span data-stu-id="cf35e-377">Quick Responses is a Microsoft Teams app that delivers a robust solution for effectively answering users' commonly asked questions FAQs.</span></span> <span data-ttu-id="cf35e-378">Anstatt jede Abfrage manuell und kontinuierlich wiederholte Informationen zu beantworten, erstellt die App eine Bibliothek mit Antworten für eine interaktive Benutzeroberfläche über [Teams-Messagingerweiterungen.](../messaging-extensions/what-are-messaging-extensions.md)</span><span class="sxs-lookup"><span data-stu-id="cf35e-378">Instead of answering each query manually and continuously repeating information, the app builds a library of responses for an interactive user experience through Teams [messaging extensions](../messaging-extensions/what-are-messaging-extensions.md).</span></span>

[<span data-ttu-id="cf35e-379">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-379">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-quickresponses)

![Beispielansicht von Antworten](../assets/images/quick-responses.png)

## <a name="quiz--9734"></a><span data-ttu-id="cf35e-381">Quiz &#9734;</span><span class="sxs-lookup"><span data-stu-id="cf35e-381">Quiz  &#9734;</span></span>

<span data-ttu-id="cf35e-382">Quiz ist [](../messaging-extensions/what-are-messaging-extensions.md) eine benutzerdefinierte Teams-Messaging-Erweiterungs-App, mit der Sie ein Quiz in einem Chat oder einem Kanal für Wissensüberprüfung und sofortige Ergebnisse erstellen können.</span><span class="sxs-lookup"><span data-stu-id="cf35e-382">Quiz is a custom [Teams messaging extension](../messaging-extensions/what-are-messaging-extensions.md) app that enables you to create a quiz within a chat or a channel for knowledge check and instantaneous results.</span></span> <span data-ttu-id="cf35e-383">Sie können Quiz für, Klassen- und Offlineprüfungen, Wissensprüfungen innerhalb des Teams und für lustige Quizfragen innerhalb eines Teams verwenden.</span><span class="sxs-lookup"><span data-stu-id="cf35e-383">You can use Quiz for, In-class and offline exams, Knowledge check within team, and for fun quizzes within a team.</span></span> <span data-ttu-id="cf35e-384">Quiz-App wird auf mehreren Plattformen unterstützt, z. B. Teams-Desktop-, Browser-, iOS- und Android-Clients.</span><span class="sxs-lookup"><span data-stu-id="cf35e-384">Quiz app is supported across multiple platforms, such as Teams desktop, browser, iOS, and Android clients.</span></span> <span data-ttu-id="cf35e-385">Diese App ist bereit für die Bereitstellung als Teil Ihres vorhandenen Microsoft 365-Abonnements.</span><span class="sxs-lookup"><span data-stu-id="cf35e-385">This app is ready for deployment as part of your existing Microsoft 365 subscription.</span></span>

[<span data-ttu-id="cf35e-386">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-386">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-quiz)

:::row:::
  :::column span="1":::
    ![Erstellen von Quiz in der Teams-Ansicht](../assets/images/quiz-app-template-compose-view.gif)  
:::column-end:::
:::row-end:::

## <a name="rapid-assist"></a><span data-ttu-id="cf35e-388">Rapid Assist</span><span class="sxs-lookup"><span data-stu-id="cf35e-388">Rapid Assist</span></span>

<span data-ttu-id="cf35e-389">Rapid Assist ist eine Microsoft [Power Platform-basierte](https://powerapps.microsoft.com/blog/now-in-preview-customize-teams-with-built-in-power-platform-capabilities/) App, mit der kundenorientierte Mitarbeiter schnell eine Verbindung mit den Experten herstellen können, um schnelle Antworten zu erhalten, nach Informationen zu suchen, offene Anfragen zu verfolgen und Experten zu ermöglichen, Benachrichtigungen zu erhalten, um schnell einen Anruf zu erhalten, um Fragen zu beantworten.</span><span class="sxs-lookup"><span data-stu-id="cf35e-389">Rapid Assist is a Microsoft [Power Platform](https://powerapps.microsoft.com/blog/now-in-preview-customize-teams-with-built-in-power-platform-capabilities/) based app that allows customer facing associates to rapidly connect with the experts to get quick answers, search for information, follow up open requests, and allow experts to receive notifications to quickly get on a call to help answer questions.</span></span> <span data-ttu-id="cf35e-390">Die app, die mit Microsoft [Power Apps](/powerapps/powerapps-overview) und [Power Automate](/power-automate/getting-started)erstellt wurde, integriert sich tief in Microsoft Teams, damit Organisationen problemlos Mitarbeiter an der Front mit Unternehmenskontakten verbinden können, um Kundenanfragen zu lösen und eine großartige Kundenerfahrung zu bieten.</span><span class="sxs-lookup"><span data-stu-id="cf35e-390">The app built using Microsoft [Power Apps](/powerapps/powerapps-overview) and [Power Automate](/power-automate/getting-started), deeply integrates with Microsoft Teams to enable organizations to easily connect frontline workers with corporate liaisons to resolve customer queries and deliver a great customer experience.</span></span> 

[<span data-ttu-id="cf35e-391">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-391">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-rapid-assist)

:::row:::
   :::column span="":::
     ![Benutzeroberfläche für Endbenutzeranforderung](../assets/images/EndUserHome.png)
   :::column-end:::
   :::column span="":::
      ![Expertenanforderungsansicht](../assets/images/ExpertViewRequests.png)
   :::column-end:::
:::row-end:::

## <a name="reflect"></a><span data-ttu-id="cf35e-394">Reflect</span><span class="sxs-lookup"><span data-stu-id="cf35e-394">Reflect</span></span> 

<span data-ttu-id="cf35e-395">Reflect ist eine [](../messaging-extensions/what-are-messaging-extensions.md) benutzerdefinierte Microsoft Teams-Messaging-Erweiterungs-App, die eine sichere und inklusive Ressource für Ihre Teammitglieder bietet, um den Zustand ihres gefühlsmäßigen Wohlbefindens mit Kollegen oder Gruppenleitern direkt in Teams zu teilen.</span><span class="sxs-lookup"><span data-stu-id="cf35e-395">Reflect is a custom Microsoft Teams [messaging extension](../messaging-extensions/what-are-messaging-extensions.md) app that provides a safe and inclusive resource for your team members to share the state of their emotional well-being with colleagues or group leaders directly within Teams.</span></span> <span data-ttu-id="cf35e-396">Die App ist in Kanal-, Gruppen-, Besprechungs- und 1:1-Chats verfügbar, und die Eincheckantwort ist auf öffentlich, privat-zu-absender oder vollständig anonym festgelegt.</span><span class="sxs-lookup"><span data-stu-id="cf35e-396">The app is available in channel, group, meeting, and 1:1 chats and the check-in response is set to public, private-to-sender, or fully anonymous.</span></span>

[<span data-ttu-id="cf35e-397">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-397">Get it on GitHub</span></span>](https://github.com/OfficeDev/Microsoft-Teams-App-Reflect)

:::row:::
    :::column:::
    <span data-ttu-id="cf35e-398">**Well-being-Umfrage**</span><span class="sxs-lookup"><span data-stu-id="cf35e-398">**Well-being poll**</span></span>
    
    ![Spiegeln der Benutzerumfrage für Apps](../assets/images/reflect-app-user-poll.png)
    :::column-end:::
:::row-end:::

## <a name="remote-support"></a><span data-ttu-id="cf35e-400">Remoteunterstützung</span><span class="sxs-lookup"><span data-stu-id="cf35e-400">Remote Support</span></span>

<span data-ttu-id="cf35e-401">Remotesupport ist ein [Microsoft Teams-Bot,](../bots/what-are-bots.md) der eine fokussierte Schnittstelle zwischen Supportanfragern in Ihrer gesamten Organisation und dem internen Supportteam bietet.</span><span class="sxs-lookup"><span data-stu-id="cf35e-401">Remote Support is a [Microsoft Teams bot](../bots/what-are-bots.md) that provides a focused interface between support requesters throughout your organization and the internal support team.</span></span>  <span data-ttu-id="cf35e-402">Endbenutzer können Supportanfragen übermitteln, bearbeiten oder zurückziehen, und das Supportteam kann Anfragen innerhalb der Teams-Plattform beantworten, verwalten und aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="cf35e-402">End-users can submit, edit, or withdraw requests for support and the support team can respond, manage, and update requests all within the Teams platform.</span></span>

[<span data-ttu-id="cf35e-403">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-403">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-remotesupport)

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

## <a name="request-a-team"></a><span data-ttu-id="cf35e-406">Request-a-team</span><span class="sxs-lookup"><span data-stu-id="cf35e-406">Request-a-team</span></span>

<span data-ttu-id="cf35e-407">Request-a-team ist eine Microsoft Teams-App, die die Neue Teamerstellung für Ihre Unternehmensorganisation optimiert.</span><span class="sxs-lookup"><span data-stu-id="cf35e-407">Request-a-team is a Microsoft Teams app that optimizes new team creation for your enterprise organization.</span></span> <span data-ttu-id="cf35e-408">Die App unterstützt Standardisierung und bewährte Methoden beim Erstellen neuer Teaminstanzen durch die Integration eines assistentengesteuerten Anforderungsformulars, eines eingebetteten Genehmigungsprozesses, eines Anforderungsstatusdashboards und automatisierter Teambuilds.</span><span class="sxs-lookup"><span data-stu-id="cf35e-408">The app supports standardization and best practices when creating new team instances through the integration of a wizard-guided request form, an embedded approval process, a request status dashboard, and automated team builds.</span></span>

[<span data-ttu-id="cf35e-409">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-409">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-requestateam)

:::row:::
  :::column span="2":::
    ![Startseitenansicht "Anforderungs-a-Team"](../assets/images/request-a-team-two.jpg)
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Seitenansicht des Assistenten zum Anfordern eines Teams](../assets/images/request-a-team-three.png)
:::column-end:::
:::row-end:::

## <a name="scrums-for-channels"></a><span data-ttu-id="cf35e-412">Scrums für Kanäle</span><span class="sxs-lookup"><span data-stu-id="cf35e-412">Scrums for Channels</span></span>

<span data-ttu-id="cf35e-413">Scrums for Channels ist eine Scrum-Assistenten-App, mit der Benutzer Scrums in Kanälen in Microsoft Teams planen und ausführen können.</span><span class="sxs-lookup"><span data-stu-id="cf35e-413">Scrums for Channels is a scrum assistant app that enables users to schedule and run scrums in channels within Microsoft Teams.</span></span> <span data-ttu-id="cf35e-414">Die App ist ideal für Remoteteams und Teams, die aus Mitgliedern unterschiedlicher geografischer Standorte und Zeitzonen bestehen, um tägliche Updates zu teilen und die Teilnahme an scrum-Stand-up-Besprechungen sicherzustellen.</span><span class="sxs-lookup"><span data-stu-id="cf35e-414">The app is great for remote teams and teams comprised of members from varied geographical locations and time zones to share daily updates and ensure participation in scrum stand-up meetings.</span></span>

[<span data-ttu-id="cf35e-415">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-415">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-scrumsforchannels)

> [!NOTE]
> <span data-ttu-id="cf35e-416">Informationen zum Durchführen von Scrum-Besprechungen in einem Gruppenchat finden Sie unter [Scrums for Group Chat](#scrums-for-group-chat) app template.</span><span class="sxs-lookup"><span data-stu-id="cf35e-416">To conduct scrum meetings in a group chat, see [Scrums for Group Chat](#scrums-for-group-chat) app template.</span></span>

:::row:::
  :::column span="2":::
    ![Ansicht "Scrums for channels settings"](../assets/images/scrum-for-channels-settings.png)
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Scrums for channels team member status view](../assets/images/scrum-for-channels-status.png)
:::column-end:::
:::row-end:::

## <a name="scrums-for-group-chat"></a><span data-ttu-id="cf35e-419">Scrums für Gruppenchat</span><span class="sxs-lookup"><span data-stu-id="cf35e-419">Scrums for Group Chat</span></span>

> [!NOTE]
> <span data-ttu-id="cf35e-420">Die Vorlage scrums Status app template is updated and is now Scrums for Group Chat.</span><span class="sxs-lookup"><span data-stu-id="cf35e-420">The Scrums Status app template is updated and is now Scrums for Group Chat.</span></span>

<span data-ttu-id="cf35e-421">Scrums for Group Chat ist ein unterstützender Scrum-Assistent, mit dem Gruppenchatmitglieder asynchrone Stand-up-Besprechungen ausführen und ihre täglichen Updates problemlos freigeben können.</span><span class="sxs-lookup"><span data-stu-id="cf35e-421">Scrums for Group Chat is a supportive scrum assistant that enables group chat members to run asynchronous stand-up meetings and easily share their daily updates.</span></span> <span data-ttu-id="cf35e-422">Es ermöglicht allen Mitgliedern des Gruppenchats, zum Scrum beizutragen und die Von anderen im ausgeführten Scrum vorgenommenen Updates anzeigen.</span><span class="sxs-lookup"><span data-stu-id="cf35e-422">It allows all members of the group chat to contribute to the scrum and view the updates made by others in the running scrum.</span></span>

[<span data-ttu-id="cf35e-423">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-423">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-scrumsforgroupchat)

![Scrums for Group Chat demo](https://raw.githubusercontent.com/wiki/OfficeDev/microsoft-teams-app-scrumstatus/images/StartScrum.jpg)

## <a name="share-now"></a><span data-ttu-id="cf35e-425">Jetzt freigeben</span><span class="sxs-lookup"><span data-stu-id="cf35e-425">Share Now</span></span> 

<span data-ttu-id="cf35e-426">Die Share Now-App fördert den positiven Austausch von Informationen zwischen Kollegen, indem Sie Ihren Benutzern die einfache Freigabe von Inhalten in der Teams-Umgebung ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="cf35e-426">The Share Now app promotes the positive exchange of information between colleagues by enabling your users to easily share content within the Teams environment.</span></span> <span data-ttu-id="cf35e-427">Benutzer engagieren die App, um Elemente von Interesse für Teammitglieder zu teilen, neue freigegebene Inhalte zu entdecken, Einstellungen zu festlegen und Favoriten für das spätere Lesen als Lesezeichen zu markieren.</span><span class="sxs-lookup"><span data-stu-id="cf35e-427">Users engage the app to share items of interest with team members, discover new shared content, set preferences, and bookmark favorites for later reading.</span></span>

[<span data-ttu-id="cf35e-428">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-428">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-sharenow)

![Auswählen der Inhaltsansicht](../assets/images/share-now-suggested-content.png)

## <a name="sharepoint-list-search"></a><span data-ttu-id="cf35e-430">SharePoint-Listensuche</span><span class="sxs-lookup"><span data-stu-id="cf35e-430">SharePoint List Search</span></span>

<span data-ttu-id="cf35e-431">Die Zusammenarbeit in Microsoft Teams verweist häufig auf Informationen, die in Elementen in einer SharePoint-Liste enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="cf35e-431">Collaboration in Microsoft Teams quite often references information contained within items in a SharePoint list.</span></span> <span data-ttu-id="cf35e-432">Wenn Sie einen Link zu dem in Frage stehenden Element einfügen, müssen alle Beteiligten den Kontext von der Unterhaltung wegschalten, die erforderlichen Informationen finden und dann zu Teams zurückkehren, um die Unterhaltung fortzufahren.</span><span class="sxs-lookup"><span data-stu-id="cf35e-432">Paste a link to the item in question forces everyone to switch context away from the conversation, find the needed information, then return to Teams to continue the conversation.</span></span> <span data-ttu-id="cf35e-433">Wenn die Unterhaltung fortgesetzt wird, müssen Die Benutzer mehrmals zum Referenzelement wechseln, um neue Kommentare zu überprüfen und ihre Erinnerungen an die im Element enthaltenen Informationen zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="cf35e-433">As the conversation continues  people have to switch back to the reference item multiple times to verify new comments and refresh their memories of the information contained within the item.</span></span> <span data-ttu-id="cf35e-434">Dieser Kontextwechsel stellt eine Barriere für eine reibungslose Zusammenarbeit dar.</span><span class="sxs-lookup"><span data-stu-id="cf35e-434">This context switching creates a barrier to smooth collaboration.</span></span>
<span data-ttu-id="cf35e-435">Um dieses Problem zu beheben, wird die App-Vorlage Listensuche verwendet.</span><span class="sxs-lookup"><span data-stu-id="cf35e-435">To resolve this problem, the List Search app template is used.</span></span> <span data-ttu-id="cf35e-436">Viele Benutzer verwenden SharePoint, um einige der wichtigsten Workflows in ihren Organisationen zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="cf35e-436">Many users use SharePoint to power some of the core workflows in their organizations.</span></span> <span data-ttu-id="cf35e-437">Die Zusammenarbeit an Listen ist jedoch schwierig.</span><span class="sxs-lookup"><span data-stu-id="cf35e-437">However, collaborating around lists is difficult.</span></span> <span data-ttu-id="cf35e-438">Mithilfe der App-Vorlage Listensuche in Microsoft Teams können Benutzer Informationen aus SharePoint-Listenelementen direkt in eine Chat unterhaltung einfügen, um den Kontextwechsel zu mindern, der beim einfachen Einfügen eines Links in einen Chat verursacht wird.</span><span class="sxs-lookup"><span data-stu-id="cf35e-438">Using the List Search app template in Microsoft Teams, users can insert information from SharePoint list items directly within a chat conversation to alleviate the context-switching caused when simply inserting a link into a chat.</span></span> <span data-ttu-id="cf35e-439">Die Informationen werden als leicht lesbare, automatisch formatierte Karte eingefügt, die den Benutzern dabei hilft, an der Unterhaltung zu bleiben.</span><span class="sxs-lookup"><span data-stu-id="cf35e-439">The information is inserted as an easy-to-read auto-formatted card, helping the users stay engaged in the conversation.</span></span>

[<span data-ttu-id="cf35e-440">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-440">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-list-search-app)

![Such-App auflisten](../assets/images/list-search-template.png)

## <a name="staff-check-ins"></a><span data-ttu-id="cf35e-442">Einchecken von Mitarbeitern</span><span class="sxs-lookup"><span data-stu-id="cf35e-442">Staff Check-ins</span></span>

<span data-ttu-id="cf35e-443">Check-Ins für Mitarbeiter ist eine [Power Apps-basierte](/powerapps/powerapps-overview) App, die die Aufsichtskommunikation zwischen Ihrem Unternehmen und Ihrem Außendienstpersonal ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="cf35e-443">Staff Check-ins is a [Power Apps](/powerapps/powerapps-overview) based app that enables oversight communication between your business and field personnel.</span></span> <span data-ttu-id="cf35e-444">Mitarbeiter können zeitkritische Informationen und Statusupdates entweder planmäßig oder ad-hoc direkt von Teams bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="cf35e-444">Staff can easily provide time-critical information and status updates on either a scheduled or ad-hoc basis directly from Teams.</span></span> <span data-ttu-id="cf35e-445">Die App unterstützt Echtzeitspeicherort, Fotos, Notizen, Erinnerungsbenachrichtigungen und automatisierte Workflows.</span><span class="sxs-lookup"><span data-stu-id="cf35e-445">The app supports real-time location, photos, notes, reminder notifications and automated workflows.</span></span>

[<span data-ttu-id="cf35e-446">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-446">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-staffcheckins)

![Erstellen der Eincheckansicht](../assets/images/staff-check-ins-create.png)

## <a name="survey"></a><span data-ttu-id="cf35e-448">Umfrage</span><span class="sxs-lookup"><span data-stu-id="cf35e-448">Survey</span></span>

<span data-ttu-id="cf35e-449">Survey ist eine [](../messaging-extensions/what-are-messaging-extensions.md) benutzerdefinierte Microsoft Teams-Messaging-Erweiterungs-App, mit der Sie eine Umfrage in einem Chat oder kanal erstellen können, um Daten zu sammeln und einblicke zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="cf35e-449">Survey is a custom Microsoft Teams [messaging extension](../messaging-extensions/what-are-messaging-extensions.md) app that enables you to create a survey in a chat or a channel to gather data and gain actionable insight.</span></span> <span data-ttu-id="cf35e-450">Die App wird auf allen Microsoft Teams-Plattformclients unterstützt, z. B. Desktop, Browser, iOS und Android, und ist für die Bereitstellung im Rahmen Ihres Microsoft 365-Abonnements bereit.</span><span class="sxs-lookup"><span data-stu-id="cf35e-450">The app is supported across all Teams platform clients, such as desktop, browser, iOS, and Android and is ready for deployment as part of your Microsoft 365 subscription.</span></span>  

[<span data-ttu-id="cf35e-451">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-451">Get it on GitHub</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Survey-app)

:::row:::
  :::column span="2":::
    ![Erstellen einer Umfrage in der Teams-Ansicht](../assets/images/survey-app-template-compose-view.gif)
:::column-end:::
:::row-end:::

## <a name="time-tally"></a><span data-ttu-id="cf35e-453">Zeit als Tally</span><span class="sxs-lookup"><span data-stu-id="cf35e-453">Time Tally</span></span> 

<span data-ttu-id="cf35e-454">Ein Projekt kann mehrere Aufgaben enthalten, und mitarbeitern können verschiedene Projekte zugewiesen werden.</span><span class="sxs-lookup"><span data-stu-id="cf35e-454">A project can include multiple tasks, and various projects can be assigned to employees.</span></span> <span data-ttu-id="cf35e-455">Manager müssen den Projektfortschritt durch die Zeit verstehen, die die Mitarbeiter für diese Aufgaben auf sich haben.</span><span class="sxs-lookup"><span data-stu-id="cf35e-455">Managers are required to understand the project progress through the time spent by the employees on these tasks.</span></span> <span data-ttu-id="cf35e-456">Dies kann eine umständliche Aktivität sein, da die Mitarbeiter die Arbeitszeittabellen ausfüllen müssen.</span><span class="sxs-lookup"><span data-stu-id="cf35e-456">This can be a cumbersome activity, as the employees need to fill in the timesheets.</span></span> <span data-ttu-id="cf35e-457">Die Time -Tally-App ermöglicht Mitarbeitern, ihre Arbeitszeittabellen schnell mit dem mobilen Gerät zu füllen, und Manager müssen mitarbeiter beim Eintrag in der Arbeitszeittabelle nicht weiter verfolgen.</span><span class="sxs-lookup"><span data-stu-id="cf35e-457">Time Tally app enables employees to fill their timesheets quickly, using the mobile device, and managers do not have to follow up with employees on the timesheet entry.</span></span> <span data-ttu-id="cf35e-458">Manager können die Projektauslastung basierend auf Ressourcen anzeigen und die Einträge genehmigen oder ablehnen.</span><span class="sxs-lookup"><span data-stu-id="cf35e-458">Managers get to view the project utilization based on resources, and they can approve or reject the entries.</span></span> <span data-ttu-id="cf35e-459">Erinnerungsbenachrichtigungen werden gesendet, um die Einhaltung der Arbeitszeittabelle sicherzustellen.</span><span class="sxs-lookup"><span data-stu-id="cf35e-459">Reminder notifications are sent to ensure timesheet compliance.</span></span> <span data-ttu-id="cf35e-460">Außerdem stehen verlaufshistorische Daten und Auslastungen für analysen zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="cf35e-460">Also, historical data and utilizations are available for analytics.</span></span>

[<span data-ttu-id="cf35e-461">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-461">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-timetally)

![Zeit als Tally](../assets/images/11zon_gif.gif)

## <a name="training--9734"></a><span data-ttu-id="cf35e-463">Schulungs&#9734;</span><span class="sxs-lookup"><span data-stu-id="cf35e-463">Training  &#9734;</span></span>

<span data-ttu-id="cf35e-464">Schulung ist [](../messaging-extensions/what-are-messaging-extensions.md) eine benutzerdefinierte Teams-Messaging-Erweiterungs-App, mit der Benutzer eine Schulung in einem Chat oder einem Kanal für die Freigabe von Offlinewissen und Upskilling veröffentlichen können.</span><span class="sxs-lookup"><span data-stu-id="cf35e-464">Training is a custom [Teams messaging extension](../messaging-extensions/what-are-messaging-extensions.md) app that enables users to publish a training within a chat or a channel for offline knowledge sharing and upskilling.</span></span> <span data-ttu-id="cf35e-465">Die App wird auf mehreren Teams-Plattformclients unterstützt, z. B. Desktop, Browser, iOS und Android.</span><span class="sxs-lookup"><span data-stu-id="cf35e-465">The app is supported across multiple Teams platform clients, such as desktop, browser, iOS, and Android.</span></span> <span data-ttu-id="cf35e-466">Diese App ist bereit für die Bereitstellung im Rahmen Ihres Microsoft 365-Abonnements.</span><span class="sxs-lookup"><span data-stu-id="cf35e-466">This app is ready for deployment as part of your Microsoft 365 subscription.</span></span>

[<span data-ttu-id="cf35e-467">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-467">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-training)

:::row:::
  :::column span="1":::
    ![Erstellen der Ansicht "Schulungen in Teams"](../assets/images/training-app-template-compose-view.gif)  
:::column-end:::
:::row-end:::

## <a name="virtual-rounding"></a><span data-ttu-id="cf35e-469">Virtuelle Rundung</span><span class="sxs-lookup"><span data-stu-id="cf35e-469">Virtual Rounding</span></span>

<span data-ttu-id="cf35e-470">Krankenhaus- und Notaufnahmeanbieter machen viele **Runden** pro Tag.</span><span class="sxs-lookup"><span data-stu-id="cf35e-470">Hospital and emergency room providers make many **rounds** per day.</span></span> <span data-ttu-id="cf35e-471">Diese schnellen Check-Ins für Patienten sollen eine Statusüberprüfung darüber ermöglichen, wie der Patient handelt, und sicherstellen, dass die Bedenken des Patienten behoben werden.</span><span class="sxs-lookup"><span data-stu-id="cf35e-471">These quick check-ins on patients are intended to provide a status check on how the patient is doing and ensure that the patient’s concerns are addressed.</span></span> <span data-ttu-id="cf35e-472">Die Rundung ist zwar eine wesentliche Methode, um sicherzustellen, dass Patienten von mehreren Arten von Anbietern überwacht werden, sie stellen jedoch einen enormen Nstropfen für EVP dar, da für jeden Besuch von jedem Anbieter eine neue Maske und neue Handschuhe verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="cf35e-472">While rounding is an essential practice to ensure patients are being monitored by multiple types of providers, they represent a huge drain on PPE, because for each visit, from each provider, a new mask, and new set of gloves are used.</span></span> <span data-ttu-id="cf35e-473">Mit diesen App-Vorlagen können Medizinische Mitarbeiter runden einfach virtuell durchführen, über eine Microsoft Teams-Besprechung zwischen dem Anbieter und dem Patienten.</span><span class="sxs-lookup"><span data-stu-id="cf35e-473">With this app templates, medical workers can easily conduct rounds virtually, through a Microsoft Teams meeting between the provider and the patient.</span></span>

<span data-ttu-id="cf35e-474">Auf die virtuelle Rundungslösung wird auch im Microsoft Health and Life Sciences-Blogbeitrag [verwiesen.](https://aka.ms/teamsvirtualrounding)</span><span class="sxs-lookup"><span data-stu-id="cf35e-474">The Virtual Rounding solution is also referenced in the Microsoft Health and Life Sciences [blog post](https://aka.ms/teamsvirtualrounding).</span></span>

[<span data-ttu-id="cf35e-475">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-475">Get it on GitHub</span></span>](https://github.com/SmartterHealth/Virtual-Rounding)

![Virtuelle Rundung](../assets/images/virtual-rounding-overview.png)

## <a name="visitor-management"></a><span data-ttu-id="cf35e-477">Besucherverwaltung</span><span class="sxs-lookup"><span data-stu-id="cf35e-477">Visitor Management</span></span>

<span data-ttu-id="cf35e-478">Die Besucherverwaltungs-App ermöglicht Es Ihrer Organisation und Ihren Mitarbeitern, den Besucherprozess vor Ort einfach und effizient direkt von Microsoft Teams aus zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="cf35e-478">The Visitor Management app enables your organization and employees to easily and efficiently manage the on-site visitor process, directly from Microsoft Teams.</span></span> <span data-ttu-id="cf35e-479">Die App ermöglicht Mitarbeitern das Erstellen von Besucheranfragen, die zentrale Nachverfolgung eines Anforderungsstatus über das Besucherdashboard und den Empfang von Echtzeitbenachrichtigungen, wenn ein Besucher eintrifft.</span><span class="sxs-lookup"><span data-stu-id="cf35e-479">The app enables employees to create visitor requests, centrally track a request status through the visitor dashboard, and receive real-time notifications when a visitor arrives.</span></span>

[<span data-ttu-id="cf35e-480">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-480">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-app-visitormanagement)

:::row:::
  :::column span="2":::
    ![Erstellen einer Anforderungsansicht](../assets/images/visitor-management-create-request.png)
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Benachrichtigung über die Besucherankömmlinge](../assets/images/visitor-management-notify-host.png)
:::column-end:::
:::row-end:::

## <a name="workplace-awards"></a><span data-ttu-id="cf35e-483">Workplace Awards</span><span class="sxs-lookup"><span data-stu-id="cf35e-483">Workplace Awards</span></span>

<span data-ttu-id="cf35e-484">Workplace Awards ist eine Teams-App-Vorlage, die einen positiven Rahmen bietet, um die Anerkennung zu fördern und die Kultur der Mitarbeiteraufwertung am modernen Arbeitsplatz zu fördern.</span><span class="sxs-lookup"><span data-stu-id="cf35e-484">Workplace Awards is a Teams app template that provides a positive framework to foster recognition and encourage the culture of employee appreciation in the modern workplace.</span></span> <span data-ttu-id="cf35e-485">Mit der App können Sie eine Mitarbeiterbelohnung und -anerkennung einrichten und verwalten, das R&R-Programm, in dem Mitarbeiter Kollegen problemlos nominieren und unterstützen können, und Ihr R&R-Leiter kann eingereichte Benennungen anzeigen, Preise gewähren und Empfänger ankündigen.</span><span class="sxs-lookup"><span data-stu-id="cf35e-485">The app enables you to setup and manage an employee rewards and recognition, called R&R program where employees can easily nominate and endorse colleagues and your R&R leader can view submitted nominations, grant awards, and announce recipients.</span></span>

[<span data-ttu-id="cf35e-486">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="cf35e-486">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-workplaceawards)

:::row:::
  :::column span="2":::
    ![<span data-ttu-id="cf35e-487">Workplace award nomination card</span><span class="sxs-lookup"><span data-stu-id="cf35e-487">Workplace awards nomination card</span></span> ](../assets/images/workplace-awards-nominate.png)
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Registerkarte "Workplace Awards"-Liste](../assets/images/workplace-awards-champion-tab.png)
:::column-end:::
:::row-end:::

<span data-ttu-id="cf35e-489">Weitere Informationen zur App-Vorlage finden Sie unter [App-Vorlage](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR2_7qFm_lcZAr4eqEhnLsZ9UMVZGT1lCT0FXUDdZMUM0RkpBS1BESTAwWC4u).</span><span class="sxs-lookup"><span data-stu-id="cf35e-489">For more information on app template, see [App template](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR2_7qFm_lcZAr4eqEhnLsZ9UMVZGT1lCT0FXUDdZMUM0RkpBS1BESTAwWC4u).</span></span>

## <a name="see-also"></a><span data-ttu-id="cf35e-490">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="cf35e-490">See also</span></span>

- [<span data-ttu-id="cf35e-491">Integrieren von Web-Apps</span><span class="sxs-lookup"><span data-stu-id="cf35e-491">Integrate web apps</span></span>](~/samples/integrate-web-apps-overview.md)
