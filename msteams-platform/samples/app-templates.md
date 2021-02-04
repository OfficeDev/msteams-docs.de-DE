---
title: Microsoft Teams-App-Vorlagen
description: Links und Beschreibungen von App-Vorlagen für die Microsoft Teams-Plattform
ms.topic: reference
keywords: Demo zu Microsoft Teams-Vorlagenbeispielen
ms.author: lajanuar
author: laujan
ms.openlocfilehash: 401d1e5878a026b2ff066114e4d41a0a54c0cf09
ms.sourcegitcommit: 55a4246e62d69d631a63bdd33de34f1b62cc0132
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2021
ms.locfileid: "50093964"
---
# <a name="app-templates-for-microsoft-teams"></a><span data-ttu-id="c808b-104">App-Vorlagen für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="c808b-104">App Templates for Microsoft Teams</span></span>

<span data-ttu-id="c808b-105">Bei den App-Vorlagen handelt es sich um produktionsbereite Apps für Microsoft Teams, die communitygesteuert, Open Source und auf GitHub verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="c808b-105">App templates are production-ready apps for Microsoft Teams that are community driven, open-source, and available on GitHub.</span></span> <span data-ttu-id="c808b-106">Jede enthält ausführliche Anweisungen zum Bereitstellen und Installieren dieser App für Ihre Organisation, die eine einsatzbereite App zur Verfügung stellt, die Sie sofort installieren und verwenden können.</span><span class="sxs-lookup"><span data-stu-id="c808b-106">Each contains detailed instructions for deploying and installing that app for your organization, providing a ready-to-use app that you can install and begin using immediately.</span></span> <span data-ttu-id="c808b-107">Der vollständige Quellcode steht ebenfalls zur Verfügung, sodass Sie ihn im Detail untersuchen oder den Code ver forken und an Ihre spezifischen Anforderungen anpassen können.</span><span class="sxs-lookup"><span data-stu-id="c808b-107">The complete source code is available as well, so you can explore it in detail, or fork the code and alter it to meet your specific needs.</span></span>

<span data-ttu-id="c808b-108">**&#9734; Gibt neu veröffentlichte App-Vorlagen an.**</span><span class="sxs-lookup"><span data-stu-id="c808b-108">**&#9734; Indicates newly released app templates.**</span></span>

### <a name="key-benefits"></a><span data-ttu-id="c808b-109">Wichtige Vorteile</span><span class="sxs-lookup"><span data-stu-id="c808b-109">Key benefits</span></span>

* <span data-ttu-id="c808b-110">**Plug -and-Play-Erfahrung:** Alle App-Vorlagen enthalten Bereitstellungsskripts, mit denen Sie alle erforderlichen Dienste in Microsoft Azure hosten können.</span><span class="sxs-lookup"><span data-stu-id="c808b-110">**Plug and play experience:** All app templates include deployments scripts that will allow you to host all necessary services in Microsoft Azure.</span></span> <span data-ttu-id="c808b-111">Für die Bereitstellung der Apps ist kein Code erforderlich.</span><span class="sxs-lookup"><span data-stu-id="c808b-111">No coding is required to deploy the apps.</span></span>
* <span data-ttu-id="c808b-112">**Produktionsbereiter Code:** Die App-Vorlagen entsprechen den empfohlenen bewährten Methoden für Sicherheit und Infrastruktur, und alle von der Community übermittelten Änderungen werden überprüft, um eine kontinuierliche Konformität sicherzustellen.</span><span class="sxs-lookup"><span data-stu-id="c808b-112">**Production-ready code:** The app templates conform to recommended best practices around security and infrastructure, and all community submitted changes to them are reviewed to ensure continued conformance.</span></span>
* <span data-ttu-id="c808b-113">**Anpassbar und erweiterbar:** Obwohl alle App-Vorlagen bereit für die Bereitstellung sind, stellen wir die gesamte Codebasis und Bereitstellungsskripts bereit, sodass Sie sie ganz einfach an Ihre individuellen Anforderungen anpassen oder erweitern können.</span><span class="sxs-lookup"><span data-stu-id="c808b-113">**Customizable and extensible:** While all app templates are ready to deploy as they are, we provide the entire code base and deployment scripts so that you can easily customize or extend them to fit your unique needs.</span></span>
* <span data-ttu-id="c808b-114">**Ausführliche Dokumentation & Support:** Alle App-Vorlagen werden von einer End-to-End-Dokumentation zu Lösungsarchitektur, Bereitstellung und Konfigurationsschritten begleitet.</span><span class="sxs-lookup"><span data-stu-id="c808b-114">**Detailed documentation & support:** All app templates are accompanied by end-to-end documentation on solution architecture, deployment, and configuration steps.</span></span> <span data-ttu-id="c808b-115">Die Repositorys werden ebenfalls überwacht. Melden Sie daher alle Probleme, die auftreten, indem Sie ein Problem auf GitHub lösen.</span><span class="sxs-lookup"><span data-stu-id="c808b-115">The repositories are monitored as well, so please report any issues you encounter by raising an Issue on GitHub.</span></span>

## <a name="adoption-bot-9734"></a><span data-ttu-id="c808b-116">Einführungsbot-&#9734;</span><span class="sxs-lookup"><span data-stu-id="c808b-116">Adoption Bot &#9734;</span></span>

<span data-ttu-id="c808b-117">Der Einführungsbot ist ein Chat-Bot, der mit Power Virtual Agent für Teams (PVA) erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="c808b-117">Adoption Bot is a user care chat bot built with Power Virtual Agent for Teams (PVA).</span></span> <span data-ttu-id="c808b-118">Sie kann als die PVA-Version von FAQPlus betrachtet werden.</span><span class="sxs-lookup"><span data-stu-id="c808b-118">It can be considered as the PVA version of FAQPlus.</span></span> <span data-ttu-id="c808b-119">Der Einführungsbot beantwortet mehr als 100 allgemeine Fragen zu Microsoft 365 und Teams.</span><span class="sxs-lookup"><span data-stu-id="c808b-119">Adoption Bot answers 100+ common questions about Microsoft 365 and Teams.</span></span> <span data-ttu-id="c808b-120">Sie können die enthaltenen Themen bearbeiten, eigene Themen hinzufügen und vorhandene häufig gestellte Fragen (FAQs) eingesten.</span><span class="sxs-lookup"><span data-stu-id="c808b-120">You can edit the included topics, add your own topics, and ingest existing FAQs.</span></span> <span data-ttu-id="c808b-121">Wenn Benutzer zusätzliche Hilfe benötigen, kann der Einführungsbot sie mit Experten verbinden oder sogar auf offene Servicetickets mit Premium-Flow-Connectors erweitert werden.</span><span class="sxs-lookup"><span data-stu-id="c808b-121">If users need additional help, Adoption Bot can connect them to experts or even be extended to open service tickets with premium flow connectors.</span></span>

[<span data-ttu-id="c808b-122">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-122">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-adopt-bot)

## <a name="appointment-manager-9734"></a><span data-ttu-id="c808b-123">Termin-Manager-&#9734;</span><span class="sxs-lookup"><span data-stu-id="c808b-123">Appointment Manager &#9734;</span></span>

<span data-ttu-id="c808b-124">Der Terminmanager ist eine Teams-App-Vorlage, mit der Unternehmen virtuelle Termine mit Kunden über Teams erstellen, verwalten und durchführen können.</span><span class="sxs-lookup"><span data-stu-id="c808b-124">Appointment Manager is a Teams app template to help businesses create, manage, and conduct virtual appointments with consumers through Teams.</span></span> <span data-ttu-id="c808b-125">Neue Terminanfragen von Kunden sind in den Teams-Kanälen sichtbar, in denen sie schnell zugewiesen und Mitarbeitern in einem Team neu zugewiesen werden können.</span><span class="sxs-lookup"><span data-stu-id="c808b-125">New appointment requests from consumers are visible in Teams channels, where they can quickly be assigned and reassigned to staff in a team.</span></span> <span data-ttu-id="c808b-126">Terminanfragen können auf Team- oder persönlichen Ebenen über benutzerdefinierte Registerkarten angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="c808b-126">Appointment requests can be viewed at team or personal levels through custom tabs.</span></span> <span data-ttu-id="c808b-127">Jeder Termin ist einer Onlinebe besprechung in Teams zugeordnet, daher können mitarbeiter und Verbraucher einfach zur geplanten Zeit an der Besprechung teilnehmen.</span><span class="sxs-lookup"><span data-stu-id="c808b-127">Every appointment is associated with a Teams online meeting, hence the staff and consumers can easily join the meeting at the scheduled time.</span></span>

<span data-ttu-id="c808b-128">Die App-Vorlage wird zur einfachen Terminverwaltung in Microsoft Bookings integriert.</span><span class="sxs-lookup"><span data-stu-id="c808b-128">The app template integrates with Microsoft Bookings for easy appointment management.</span></span> <span data-ttu-id="c808b-129">Geplante Termine werden automatisch in den Kalendern der zugewiesenen Mitarbeiter angezeigt, und Benutzer erhalten anpassbare E-Mail-Benachrichtigungen und Erinnerungen mit eingebetteten Besprechungslinks.</span><span class="sxs-lookup"><span data-stu-id="c808b-129">Scheduled appointments automatically appear on assigned staff members' calendars, and consumers receive customizable email notifications and reminders with embedded meeting links.</span></span>

[<span data-ttu-id="c808b-130">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-130">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-appointment-manager)

<span data-ttu-id="c808b-131">![Appointment Manager Overview ](../assets/images/appointment-manager-overview.png)
 ![ Appointment Manager in Teams](../assets/images/appointment-manager-2.png)</span><span class="sxs-lookup"><span data-stu-id="c808b-131">![Appointment Manager Overview](../assets/images/appointment-manager-overview.png)
![Appointment Manager in Teams](../assets/images/appointment-manager-2.png)</span></span>

## <a name="ask-away"></a><span data-ttu-id="c808b-132">Ask Away</span><span class="sxs-lookup"><span data-stu-id="c808b-132">Ask Away</span></span>

<span data-ttu-id="c808b-133">"Abfragen" ist [ein Microsoft Teams-Bot,](../bots/what-are-bots.md) mit dem Benutzer Fragen und antworten&Fragen und Antworten in Teams durchführen können.</span><span class="sxs-lookup"><span data-stu-id="c808b-133">Ask Away is a [Microsoft Teams bot](../bots/what-are-bots.md) that enables users to conduct Q&A (Question and Answer) sessions within Teams.</span></span> <span data-ttu-id="c808b-134">Mit dem Bot "Abfragen" können Teammitglieder Von Kollegen geteilte Fragen übermitteln und abstimmen, sodass Q&A-Hosts ganz einfach die wichtigsten Fragen in einem Kanal oder Chat sammeln können.</span><span class="sxs-lookup"><span data-stu-id="c808b-134">Using the Ask Away bot, team members can submit and up-vote questions shared by colleagues allowing Q&A hosts to easily gather top-of-mind questions within a channel or chat.</span></span> <span data-ttu-id="c808b-135">Der Bot kann verwendet werden, um eine Echtzeit-Q-&einer Sitzung in einer Teams-Besprechung zu führen, und ermöglicht Teilnehmern, Fragen per Chat live zu übermitteln.</span><span class="sxs-lookup"><span data-stu-id="c808b-135">The bot can be used to conduct a real-time Q&A session in a Teams meeting and allows attendees to submit questions live via chat.</span></span>

[<span data-ttu-id="c808b-136">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-136">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-askaway)

:::row:::
  :::column span="2":::
    ![Ansicht des Popupdialogfelds "Bestenliste", in dem Benutzer über Fragen abstimmen können](../assets/images/ask-away-app.png)  
:::column-end:::
:::row-end:::

## <a name="associate-insights"></a><span data-ttu-id="c808b-138">Assoziierte Einblicke</span><span class="sxs-lookup"><span data-stu-id="c808b-138">Associate Insights</span></span>

<span data-ttu-id="c808b-139">Associate Insights ist eine [Power Apps-Vorlage,](/powerapps/maker/canvas-apps/embed-teams-app) mit der Mitarbeiter in Service und Service mitarbeiter direkt Kundenmeinungen, -stimmungen und -wahrnehmungen erfassen und übermitteln können.</span><span class="sxs-lookup"><span data-stu-id="c808b-139">Associate Insights is a [Power Apps](/powerapps/maker/canvas-apps/embed-teams-app) template that empowers firstline workers to directly capture and submit customer opinion, sentiment, and perception.</span></span> <span data-ttu-id="c808b-140">Mitarbeiter in Erstunternehmen sind häufig der erste Unternehmensmitarbeiter, der sich an einer 1:1-Kontaktstelle mit Kunden in Verbindung setzt.</span><span class="sxs-lookup"><span data-stu-id="c808b-140">Firstline workers are often the first company representative to engage with customers in a one-to-one point-of contact.</span></span> <span data-ttu-id="c808b-141">Die gesammelten Daten können gemeinsam von Geschäftsteams freigegeben und verwendet werden, z. B. über eine Power BI Teams-Registerkarte, um die Produktverbesserung zu verbessern und die Kundenerfahrung zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="c808b-141">The collected data can be shared and used collaboratively by business teams, e.g., via a Power BI Teams tab, for product improvement and enhancing the customer experience.</span></span>

[<span data-ttu-id="c808b-142">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-142">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-associateinsights)

:::row:::
  :::column span="2":::
    ![Feedbackansicht der von der App generierten Einblicke](../assets/images/associate-insights-app.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Power BI-Ansicht der von der App generierten Einblicke](../assets/images/associate-insights-app2.png)
:::column-end:::
:::row-end:::

## <a name="attendance"></a><span data-ttu-id="c808b-145">Anwesenheit</span><span class="sxs-lookup"><span data-stu-id="c808b-145">Attendance</span></span>

<span data-ttu-id="c808b-146">Die Anwesenheits-App ist [eine Power Apps-Registerkarte,](/powerapps/maker/canvas-apps/embed-teams-app) die in einem Team angeheftet werden kann.</span><span class="sxs-lookup"><span data-stu-id="c808b-146">The Attendance app is a [Power Apps](/powerapps/maker/canvas-apps/embed-teams-app) tab that can be pinned in a team.</span></span> <span data-ttu-id="c808b-147">Es ist so konzipiert, dass Anwesenheitsdaten aufgezeichnet werden, in der Regel in Einstellungen wie z. B. Lern- und Schulungsumgebungen.</span><span class="sxs-lookup"><span data-stu-id="c808b-147">It is designed to record presence, typically in settings such as learning and training environments.</span></span> <span data-ttu-id="c808b-148">Benutzer können die Teilnahme in der Vergangenheit bis zu 30 Tage lang markieren oder bearbeiten und zusammenfassende Anwesenheitsberichte für eine ganze Gruppe oder einzelne Teilnehmer anzeigen.</span><span class="sxs-lookup"><span data-stu-id="c808b-148">Users can mark or edit attendance for up to 30 days in the past and view summarized attendance reports for an entire group or individual attendees.</span></span>

[<span data-ttu-id="c808b-149">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-149">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-attendance)

![Demo zur Teilnahme-App](../assets/images/attendance-app.png)

## <a name="book-a-room"></a><span data-ttu-id="c808b-151">Buch-a-Raum</span><span class="sxs-lookup"><span data-stu-id="c808b-151">Book-a-room</span></span>

<span data-ttu-id="c808b-152">Book-a-room ist ein [Microsoft Teams-Bot,](../bots/what-are-bots.md) mit dem Benutzer schnell einen Besprechungsraum für 30 (Standard), 60 oder 90 Minuten ab der aktuellen Uhrzeit finden und reservieren können.</span><span class="sxs-lookup"><span data-stu-id="c808b-152">Book-a-room is a [Microsoft Teams bot](../bots/what-are-bots.md) that lets users quickly find and reserve a meeting room for 30 (default), 60, or 90 minutes starting from the current  time.</span></span> <span data-ttu-id="c808b-153">Der Bot "Buch-a-Raum" ist auf persönliche Unterhaltungen oder 1:1-Unterhaltungen begrenzt.</span><span class="sxs-lookup"><span data-stu-id="c808b-153">The Book-a-room bot scopes to personal or 1:1 conversations.</span></span>

[<span data-ttu-id="c808b-154">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-154">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom)

![Demo "Buch-a-Raum"](../assets/images/book-a-room.png)

## <a name="building-access"></a><span data-ttu-id="c808b-156">Gebäudezugriff</span><span class="sxs-lookup"><span data-stu-id="c808b-156">Building Access</span></span>

<span data-ttu-id="c808b-157">Building Access ist eine Microsoft [Power Platform-basierte](https://powerapps.microsoft.com/blog/now-in-preview-customize-teams-with-built-in-power-platform-capabilities/)App, die die Verwaltung von Schwellenwerten für die Belegung von Belegungen und sozialen Distancing-Normen unterstützt, indem es Einrichtungsleitern ermöglicht wird, die Anwesenheit von Mitarbeitern vor Ort zu verwalten, nachzuververwalten und zu melden.</span><span class="sxs-lookup"><span data-stu-id="c808b-157">Building Access is a Microsoft [Power Platform](https://powerapps.microsoft.com/blog/now-in-preview-customize-teams-with-built-in-power-platform-capabilities/)-based app that supports the administration of building occupancy thresholds and social distancing norms by enabling facilities directors to manage, track, and report employee on-site presence.</span></span> <span data-ttu-id="c808b-158">Die App, die mit Microsoft [Power Apps](/powerapps/powerapps-overview)und [Power Automate](/power-automate/getting-started)erstellt wurde, ist tief in Microsoft Teams integriert und ermöglicht Es Organisationen, die Erstellungsbereitschaft zu bestimmen, Berechtigungskriterien für den Zugriff auf die Website festzulegen und Erkenntnisse für die zukünftige Planung zu sammeln.</span><span class="sxs-lookup"><span data-stu-id="c808b-158">The app, built using Microsoft [Power Apps](/powerapps/powerapps-overview), and [Power Automate](/power-automate/getting-started), deeply integrates with Microsoft Teams and enables organizations to determine building readiness, establish eligibility criteria for on-site access, and gather insights for future planning.</span></span>

[<span data-ttu-id="c808b-159">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-159">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-buildingaccess)

:::row:::
   :::column span="":::
     ![Erstellen einer Zugriffsreservierungskarte](../assets/images/building-access-reservation.png)
   :::column-end:::
   :::column span="":::
      ![Zugriffstastenansicht erstellen](../assets/images/building-access-access-key.png)
   :::column-end:::
:::row-end:::

## <a name="celebrations"></a><span data-ttu-id="c808b-162">Feiern</span><span class="sxs-lookup"><span data-stu-id="c808b-162">Celebrations</span></span>

<span data-ttu-id="c808b-163">Bei Geburtstagen handelt es sich um eine Teams-App, die Teammitgliedern dabei hilft, ihre Geburtstage, Jubiläen und anderen wiederkehrenden Ereignisse miteinander zu vermischen.</span><span class="sxs-lookup"><span data-stu-id="c808b-163">Celebrations is a Teams app that helps team members celebrate each others' birthdays, anniversaries, and other recurring events.</span></span> <span data-ttu-id="c808b-164">Er erinnert sich an besondere Anlässe aller Teammitglieder und sendet eine benutzerfreundliche Nachricht in allen Teams, die zum Zeitpunkt der Ereigniserstellung ausgewählt wurden, damit sich die Teammitglieder an ihrem Tag besonders fühlen.</span><span class="sxs-lookup"><span data-stu-id="c808b-164">It remembers special occasions of all the team members and sends a friendly message in all the teams selected at the time of event creation, to make the team members feel special on their day.</span></span>

<span data-ttu-id="c808b-165">Die App bietet eine einfache Schnittstelle für alle Teammitglieder zum persönlichen Hinzufügen und Anzeigen ihrer Ereignisse und ermöglicht es dem Benutzer, die Teams auszuwählen, in denen die Ereignisse freigegeben werden.</span><span class="sxs-lookup"><span data-stu-id="c808b-165">The app provides an easy interface for all the team members to personally add and view their events and also allows the user to select the teams in which the events gets shared.</span></span>

[<span data-ttu-id="c808b-166">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-166">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-celebrations-app)

## <a name="checklist"></a><span data-ttu-id="c808b-167">Prüfliste</span><span class="sxs-lookup"><span data-stu-id="c808b-167">Checklist</span></span>

<span data-ttu-id="c808b-168">Die Prüfliste ist [](../messaging-extensions/what-are-messaging-extensions.md) eine benutzerdefinierte Microsoft Teams-Messaging-Erweiterungs-App, mit der Sie mit Ihrem Team zusammenarbeiten können, indem Sie eine freigegebene Prüfliste in einem Chat oder Kanal erstellen.</span><span class="sxs-lookup"><span data-stu-id="c808b-168">Checklist is a custom Microsoft Teams [messaging extension](../messaging-extensions/what-are-messaging-extensions.md) app that enables you to collaborate with your team by creating a shared checklist in a chat or channel.</span></span> <span data-ttu-id="c808b-169">Die App wird auf allen Microsoft Teams-Plattformclients unterstützt – Desktop, Browser, iOS und Android – und kann im Rahmen Ihres Microsoft 365-Abonnements zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="c808b-169">The app is supported across all Teams platform clients —  desktop, browser, iOS, and Android — and is ready for deployment as part of your Microsoft 365 subscription.</span></span>  

[<span data-ttu-id="c808b-170">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-170">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-checklist-app )

:::row:::
:::column span="2":::
    ![Erstellen einer Prüfliste in der Ansicht "Teams"](../assets/images/checklist-app-template-compose-view.gif)  
:::column-end:::
:::row-end:::

## <a name="classroom-drop-in-9734"></a><span data-ttu-id="c808b-172">Drop-In-&#9734;</span><span class="sxs-lookup"><span data-stu-id="c808b-172">Classroom Drop-in &#9734;</span></span>

<span data-ttu-id="c808b-173">Classroom Drop-in ist eine Microsoft [Power Platform-basierte](https://powerapps.microsoft.com/blog/now-in-preview-customize-teams-with-built-in-power-platform-capabilities/)App, mit der Systemleiter Kursteams (virtuelle Kursräume) finden und sich selbst oder andere zu diesen Kursteams für einen bestimmten Drop-In-Zeitraum hinzufügen können, je nach Bedarf.</span><span class="sxs-lookup"><span data-stu-id="c808b-173">Classroom Drop-in is a Microsoft [Power Platform](https://powerapps.microsoft.com/blog/now-in-preview-customize-teams-with-built-in-power-platform-capabilities/)-based app that enables system leaders to find class teams (virtual classrooms) and add themselves or others to these class teams for a specified drop-in period, as needed.</span></span> <span data-ttu-id="c808b-174">Die App, die mit Microsoft [Power Apps](/powerapps/powerapps-overview) und [Power Automate](/power-automate/getting-started)erstellt wurde, ist tief in Microsoft Teams integriert, um sicherzustellen, dass Bildungseinrichtungen ihre Vorgänge in einer hybriden Lernumgebung optimieren können, indem sie den relevanten Beteiligten Zugriff für Kursteams nach Geschäftlichen Anforderungen bietet.</span><span class="sxs-lookup"><span data-stu-id="c808b-174">The app built using Microsoft [Power Apps](/powerapps/powerapps-overview) and [Power Automate](/power-automate/getting-started), deeply integrates with Microsoft Teams to ensure educational institutes can optimize their operations in a hybrid learning environment by providing access to relevant stakeholders for class teams per business requirements.</span></span>

[<span data-ttu-id="c808b-175">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-175">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-classroom-dropin)

![Drop-In-Anforderung für Kursraum](../assets/images/classroom-drop-in-request.png)

## <a name="company-communicator"></a><span data-ttu-id="c808b-177">Unternehmens-Communicator</span><span class="sxs-lookup"><span data-stu-id="c808b-177">Company Communicator</span></span>

<span data-ttu-id="c808b-178">Die Unternehmens-Communicator-App ermöglicht Unternehmensteams das Erstellen und Senden von Nachrichten, die für mehrere Teams oder eine große Anzahl von Mitarbeitern im Chat vorgesehen sind, sodass die Organisation mitarbeiter direkt dort erreichen kann, wo sie zusammenarbeiten.</span><span class="sxs-lookup"><span data-stu-id="c808b-178">The Company Communicator app enables corporate teams to create and send messages intended for multiple teams or large number of employees over chat allowing organization to reach employees right where they collaborate.</span></span> <span data-ttu-id="c808b-179">Verwenden Sie diese Vorlage für mehrere Szenarien, z. B. Ankündigungen neuer Initiativen, Mitarbeiter-Onboarding, modernes Lernen und Entwicklung oder organisationsweite Übertragungen.</span><span class="sxs-lookup"><span data-stu-id="c808b-179">Utilize this template for multiple scenarios such as new initiative announcements, employee onboarding, modern learning and development or organization-wide broadcasts.</span></span>

<span data-ttu-id="c808b-180">Die App bietet eine einfache Schnittstelle für designierte Benutzer zum Erstellen, Anzeigen einer Vorschau, Zusammenarbeit und Senden von Nachrichten.</span><span class="sxs-lookup"><span data-stu-id="c808b-180">The app provides an easy interface for designated users to create, preview, collaborate and send messages.</span></span>

<span data-ttu-id="c808b-181">Es bietet eine Grundlage für die Erstellung benutzerdefinierter gezielter Kommunikationsfunktionen wie benutzerdefinierte Telemetrie darüber, wie viele Benutzer eine Nachricht bestätigt oder mit dieser interagiert haben.</span><span class="sxs-lookup"><span data-stu-id="c808b-181">It provides a foundation to build custom targeted communication capabilities such as custom telemetry on how many users acknowledged or interacted with a message.</span></span>

[<span data-ttu-id="c808b-182">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-182">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-company-communicator-app)

![jCompany Communicator Verfassenfeldansicht](../assets/images/CompanyCommunicatorCompose.png)

## <a name="contact-group-lookup"></a><span data-ttu-id="c808b-184">Kontaktgruppen-Nachschlage</span><span class="sxs-lookup"><span data-stu-id="c808b-184">Contact Group Lookup</span></span>

<span data-ttu-id="c808b-185">Die Kontaktgruppen-Nachschlage-App bietet einen praktischen und nützlichen Ansatz zum Erstellen, Zugreifen auf und Verwalten der Kontaktgruppen Ihrer Organisation (früher als Verteilerlisten oder Kommunikationsgruppen bekannt).</span><span class="sxs-lookup"><span data-stu-id="c808b-185">The Contact Group Lookup app provides a convenient and useful approach to creating, accessing, and managing your organization's contact groups (formerly known as distribution lists or communication groups).</span></span> <span data-ttu-id="c808b-186">Benutzer können schnell Gruppenmitglieder anzeigen und chatten, den Mitgliederstatus anzeigen und einen Gruppenchat mit ausgewählten Mitgliedern in der Kontaktgruppe erstellen, und dies alles innerhalb der Teams-Umgebung.</span><span class="sxs-lookup"><span data-stu-id="c808b-186">Users can quickly view and chat with group members, view member status, and create a group chat with selected members in the contact group, all within the Teams environment.</span></span>

[<span data-ttu-id="c808b-187">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-187">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-app-contactgrouplookup)

:::row:::
:::column span="2":::
    ![Kontaktgruppen-Nachschlageansicht für angeheftierte Favoriten](../assets/images/contact-group-lookup-favorites.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Demo zum Starten des Chats durch die Kontaktgruppen-Suche](../assets/images/contact-group-lookup-chat.png)
:::column-end:::
:::row-end:::

## <a name="co-worker-appreciation-9734"></a><span data-ttu-id="c808b-190">Arbeitsverdingungs-&#9734;</span><span class="sxs-lookup"><span data-stu-id="c808b-190">Co-worker Appreciation &#9734;</span></span>

<span data-ttu-id="c808b-191">Mithilfe der Vorlage "Arbeitskollegen" in Microsoft Teams können Benutzer die Erfolge ihrer Kollegen im Kontext von Teams erkennen.</span><span class="sxs-lookup"><span data-stu-id="c808b-191">Using the co-worker appreciation template in Microsoft Teams, users can recognize their colleagues' achievements within the Teams’ context.</span></span> <span data-ttu-id="c808b-192">Wenn Kollegen einen Kollegen belohnen, werden Empfänger und andere Teammitglieder in einer Kanalgespräch gekennzeichnet und erhalten eine Benachrichtigung über die Preisdetails des Kanals.</span><span class="sxs-lookup"><span data-stu-id="c808b-192">When co-workers select to reward a colleague, recipients and other team members are tagged in a channel conversation and they receive a notification about the channel's award details.</span></span> <span data-ttu-id="c808b-193">Die Preise werden in der Teams-App aufgezeichnet, die sicher, portabel und einfach freigabefähig ist.</span><span class="sxs-lookup"><span data-stu-id="c808b-193">The awards are recorded in the Teams app, which is secure, portable, and easily shareable.</span></span> <span data-ttu-id="c808b-194">Dies kann als powerApps-basierte Version der Open Badges-App-Vorlage mit einer Bestenliste betrachtet werden.</span><span class="sxs-lookup"><span data-stu-id="c808b-194">This can be considered as the PowerApps based version of the Open Badges app template, with a leaderboard.</span></span>

[<span data-ttu-id="c808b-195">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-195">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-coworker-appreciation)

![Gesamt](../assets/images/coworker-appreciation-1.png)

## <a name="crowdsourcer"></a><span data-ttu-id="c808b-197">CrowdSourcer</span><span class="sxs-lookup"><span data-stu-id="c808b-197">CrowdSourcer</span></span>

<span data-ttu-id="c808b-198">CrowdSourcer ist ein [Microsoft Teams-Bot,](../bots/what-are-bots.md) der teams abgefragte Informationen liefert, die gemeinsam von Gruppenmitgliedern stammen.</span><span class="sxs-lookup"><span data-stu-id="c808b-198">CrowdSourcer is a [Microsoft Teams bot](../bots/what-are-bots.md) that gives teams queried information sourced collaboratively from group members.</span></span> <span data-ttu-id="c808b-199">Es ist eine hervorragende Möglichkeit, häufig gestellte Fragen zu beantworten, während teilnehmer aktiv an einer unterhaltungs- und hilfreichen Informationsressource mitwirken können.</span><span class="sxs-lookup"><span data-stu-id="c808b-199">It's a great way to answer frequently asked questions while enabling participants to actively engage in and contribute to a fun and helpful information resource.</span></span>

[<span data-ttu-id="c808b-200">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-200">Get it on Github</span></span>](https://github.com/OfficeDev/microsoft-teams-crowdsourcer-app)

![Interaktion von Endbenutzern mit Crowdsource](../assets/images/crowdsourcer.png)

## <a name="custom-stickers"></a><span data-ttu-id="c808b-202">Custom Stickers</span><span class="sxs-lookup"><span data-stu-id="c808b-202">Custom Stickers</span></span>

<span data-ttu-id="c808b-203">Selbstausdruck ist der Kern einer gesunden Teamkultur.</span><span class="sxs-lookup"><span data-stu-id="c808b-203">Self-expression is core to a healthy team culture.</span></span> <span data-ttu-id="c808b-204">Diese App-Vorlage ist eine [Messaging-Erweiterung,](~/messaging-extensions/what-are-messaging-extensions.md) mit der Ihre Benutzer benutzerdefinierte Aufkleber und GIFs in Microsoft Teams verwenden können.</span><span class="sxs-lookup"><span data-stu-id="c808b-204">This app template is a [messaging extension](~/messaging-extensions/what-are-messaging-extensions.md) that enables your users to use custom stickers and GIFs within Microsoft Teams.</span></span> <span data-ttu-id="c808b-205">Diese Vorlage bietet eine einfache webbasierte Konfigurationserfahrung, bei der jeder Benutzer mit Konfigurationszugriff die GIFs/Aufkleber/Bilder hochladen kann, die die Endbenutzer haben möchten, sodass Ihr gesamtes Team alle von Ihnen gewählten Aufkleber verwenden kann.</span><span class="sxs-lookup"><span data-stu-id="c808b-205">This template provides an easy web-based configuration experience where anyone with configuration access can upload the GIFs/stickers/images they want their end-users to have, allowing your entire team to use any set of stickers you chose.</span></span>

<span data-ttu-id="c808b-206">Diese App ermöglicht auch die einfache Freigabe von Bildern/GIFs/Aufklebern in Teams, ohne zugriff auf SharePoint-Websites oder einzelne Kanäle als Speicher- und Freigabemechanismen zu benötigen.</span><span class="sxs-lookup"><span data-stu-id="c808b-206">This app also enables easy sharing of images/GIFs/stickers across teams without needing access to SharePoint sites or individual channels as storage and sharing mechanisms.</span></span> <span data-ttu-id="c808b-207">Beispielsweise können Produktteams Produktbilder und GIFs ganz einfach programmgesteuert für soziale Medien, Marketing- und Vertriebsteams freigeben.</span><span class="sxs-lookup"><span data-stu-id="c808b-207">For example, product teams can easily share product images and GIFs to social media, marketing and sales teams programmatically.</span></span> <span data-ttu-id="c808b-208">Sie können diese App auch erweitern, indem sie einen Benachrichtigungsfluss für bestimmte Teams/Einzelpersonen auslöst, wenn neue Bilder/GIFs verfügbar gemacht werden.</span><span class="sxs-lookup"><span data-stu-id="c808b-208">One can also extend this app by triggering a notification flow to specific teams/individuals when new images/GIFs are made available.</span></span>

[<span data-ttu-id="c808b-209">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-209">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-stickers-app)

![Aufkleber-App](../assets/images/stickers.png)

## <a name="employee-ideas-9734"></a><span data-ttu-id="c808b-211">Mitarbeiterideen &#9734;</span><span class="sxs-lookup"><span data-stu-id="c808b-211">Employee Ideas &#9734;</span></span>

<span data-ttu-id="c808b-212">Die App "Mitarbeiterideen" ist die PowerApps-Version der Azure-basierten App-Vorlage "Großartige Ideen".</span><span class="sxs-lookup"><span data-stu-id="c808b-212">The Employee Ideas app is the PowerApps version of the Azure based Great Ideas app template.</span></span> <span data-ttu-id="c808b-213">Mit der App können die Benutzer von Teams eine Ideenkampagne einrichten und konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="c808b-213">The app enables the Teams users to set up and configure an idea campaign.</span></span> <span data-ttu-id="c808b-214">Eine Ideenkampagne ist eine Kategorie zum Gruppieren von Ideen zu gängigen Designs.</span><span class="sxs-lookup"><span data-stu-id="c808b-214">An idea campaign is a category for grouping ideas around common themes.</span></span>

<span data-ttu-id="c808b-215">Benutzer von Teams können auch folgende Aktivitäten ausführen:</span><span class="sxs-lookup"><span data-stu-id="c808b-215">Teams users can also perform following activities:</span></span>
* <span data-ttu-id="c808b-216">Konfigurieren Sie ein Standardübermittlungsformular, das Mitarbeiter für jede Idee übermitteln müssen.</span><span class="sxs-lookup"><span data-stu-id="c808b-216">Configure a standard submission form that employees need to submit for each idea.</span></span> 
* <span data-ttu-id="c808b-217">Überprüfen und verwalten Sie die Ideen und die Liste der Kampagnen.</span><span class="sxs-lookup"><span data-stu-id="c808b-217">Review and manage the ideas and list of campaigns.</span></span>
* <span data-ttu-id="c808b-218">Ändern und Löschen von Kampagnen.</span><span class="sxs-lookup"><span data-stu-id="c808b-218">Modify and delete campaigns.</span></span>
* <span data-ttu-id="c808b-219">Überprüfen Sie Die Bestenlisten mit Ideen.</span><span class="sxs-lookup"><span data-stu-id="c808b-219">Review leader boards of ideas.</span></span>
* <span data-ttu-id="c808b-220">Stimmen Sie für priorisierte Ideen, und teilen Sie sie mit.</span><span class="sxs-lookup"><span data-stu-id="c808b-220">Vote for and share prioritized ideas.</span></span>
* <span data-ttu-id="c808b-221">Übermitteln Sie Ideen für eine Kampagne.</span><span class="sxs-lookup"><span data-stu-id="c808b-221">Submit ideas for a campaign.</span></span>
* <span data-ttu-id="c808b-222">Zeigen Sie die Idee eines anderen Teammitglieds an.</span><span class="sxs-lookup"><span data-stu-id="c808b-222">View other team member's idea.</span></span>
* <span data-ttu-id="c808b-223">Stimmen Sie über die meisten "Gefällt mir"-Ideen ab.</span><span class="sxs-lookup"><span data-stu-id="c808b-223">Vote on most liked ideas.</span></span>
* <span data-ttu-id="c808b-224">Überprüfen Sie die Leistung ihrer Ideen im Vergleich zu anderen in einer Kampagne.</span><span class="sxs-lookup"><span data-stu-id="c808b-224">Review the performance of their ideas compared with others within a campaign.</span></span>

[<span data-ttu-id="c808b-225">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-225">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-employeeideas)

![Verwalten der Kampagnenansicht](../assets/images/employee-ideas-manage-campaigns.png) 

## <a name="e-prescriptions"></a><span data-ttu-id="c808b-227">E-Prescriptions</span><span class="sxs-lookup"><span data-stu-id="c808b-227">E-Prescriptions</span></span> 

<span data-ttu-id="c808b-228">E-Prescriptions ist eine [Power Apps-basierte](/powerapps/maker/canvas-apps/embed-teams-app)App, die die Telemedikierung und die virtuelle Behandlung verbessert, indem der Prozess der Ausgabe von E-Rezepten für Patienten automatisiert wird.</span><span class="sxs-lookup"><span data-stu-id="c808b-228">E-Prescriptions is a [Power Apps](/powerapps/maker/canvas-apps/embed-teams-app)-based app that enhances telemedicine and virtual care by automating the process of issuing e-prescriptions to patients.</span></span> <span data-ttu-id="c808b-229">Medical professionals can quickly review appointments, generate e-prescriptions, and send emails with e-prescription attachments to patients directly within the Teams platform.</span><span class="sxs-lookup"><span data-stu-id="c808b-229">Medical professionals can quickly review appointments, generate e-prescriptions, and send emails with e-prescription attachments to patients directly within the Teams platform.</span></span>

[<span data-ttu-id="c808b-230">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-230">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-eprescription) 

:::row:::
:::column span="2":::
    ![Screenshot der App "E-Prescriptions".](../assets/images/e-prescriptions-app-template.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Screenshot der App "E-Prescriptions".](../assets/images/e-prescriptions-app-template-admin.png)
:::column-end:::
:::row-end:::


## <a name="emergency-button-power-9734"></a><span data-ttu-id="c808b-235">Notruftasten-&#9734;</span><span class="sxs-lookup"><span data-stu-id="c808b-235">Emergency Button Power &#9734;</span></span>

<span data-ttu-id="c808b-236">Die Notfalltasten-Power-App kann von Organisationen verwendet werden, die Microsoft Teams verwenden, um es allen Benutzern zu ermöglichen, Unterstützung von Vorgesetzten an zu fordern.</span><span class="sxs-lookup"><span data-stu-id="c808b-236">The Emergency Button Power app can be used by organizations that are using Microsoft Teams, to enable any set of users to request assistance from supervisors.</span></span> <span data-ttu-id="c808b-237">Diese App enthält verschiedene Features, z. B.:</span><span class="sxs-lookup"><span data-stu-id="c808b-237">This app includes various features, such as:</span></span>
-   <span data-ttu-id="c808b-238">Anfordern von Unterstützung für verschiedene Kategorien von einer Power App</span><span class="sxs-lookup"><span data-stu-id="c808b-238">Requesting assistance on different categories from a Power App</span></span>
-   <span data-ttu-id="c808b-239">Benachrichtigungen, die an Ansgeber gesendet werden und sie darüber informieren, wer zugewiesen wurde</span><span class="sxs-lookup"><span data-stu-id="c808b-239">Notifications sent to requestors informing them of who has been assigned</span></span> 
-   <span data-ttu-id="c808b-240">Benachrichtigungen, die an zugewiesene Vorgesetzte gesendet werden und sie darüber informieren, wer Unterstützung benötigt</span><span class="sxs-lookup"><span data-stu-id="c808b-240">Notifications sent to assigned supervisors informing them of who needs assistance</span></span> 
-   <span data-ttu-id="c808b-241">Anzeigen von Überwachungsprotokollen in SharePoint</span><span class="sxs-lookup"><span data-stu-id="c808b-241">Viewing audit trails held in SharePoint</span></span>

[<span data-ttu-id="c808b-242">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-242">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-emergency-button-app)


## <a name="employee-training"></a><span data-ttu-id="c808b-243">Mitarbeiterschulung</span><span class="sxs-lookup"><span data-stu-id="c808b-243">Employee Training</span></span> 

<span data-ttu-id="c808b-244">Mitarbeiterschulungen sind eine Microsoft Teams-App, die es Organisatoren ermöglicht, Lern- und Schulungsereignisse für Ihre Organisation einfach zu veröffentlichen, nachverfolgt und zu fördern.</span><span class="sxs-lookup"><span data-stu-id="c808b-244">Employee training is a Microsoft Teams app that enables organizers to easily publish,  track, and promote learning and training events for your organization.</span></span>  <span data-ttu-id="c808b-245">Mit der App können Ereignisplaner Erinnerungen und Benachrichtigungen an Ereignisregistranten senden, und Mitarbeiter können Interesse an bevorstehenden Ereignissen anzeigen, über die Messagingerweiterung Teams über aktuelle Ereignisse auf dem Laufenden bleiben und Ereignisdetails mit Kollegen teilen.</span><span class="sxs-lookup"><span data-stu-id="c808b-245">With the app, event planners can send reminders and notifications to event registrants and employees can indicate interest in upcoming events, stay updated on current events, and share event details with colleagues via the Teams messaging extension.</span></span>

[<span data-ttu-id="c808b-246">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-246">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-employeetraining)

:::row:::
:::column span="2":::
    <span data-ttu-id="c808b-247">**Anzeigen von Schulungsereignissen für Mitarbeiter** ![ Abbildung der Registerkarte "Mitarbeiterschulung"](../assets/images/employee-training-discover-tab.png)</span><span class="sxs-lookup"><span data-stu-id="c808b-247">**View employee training events** ![Employee training tab image](../assets/images/employee-training-discover-tab.png)</span></span>  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    <span data-ttu-id="c808b-248">**Mitarbeiterschulungsereignis erstellen** ![ Formular zum Erstellen eines Ereignisses für Mitarbeiterschulungen](../assets/images/employee-training-create-event.jpg)</span><span class="sxs-lookup"><span data-stu-id="c808b-248">**Create employee training event** ![Employee training create event form](../assets/images/employee-training-create-event.jpg)</span></span>
:::column-end:::
:::row-end:::

## <a name="expert-finder"></a><span data-ttu-id="c808b-249">Experten-Finder</span><span class="sxs-lookup"><span data-stu-id="c808b-249">Expert Finder</span></span>

<span data-ttu-id="c808b-250">Expert Finder ist ein [Microsoft Teams-Bot,](../bots/what-are-bots.md) der bestimmte Organisationsmitglieder basierend auf ihren Fähigkeiten, Interessen und Bildungsattributen identifiziert.</span><span class="sxs-lookup"><span data-stu-id="c808b-250">Expert Finder is a [Microsoft Teams bot](../bots/what-are-bots.md) that identifies specific organization members based on their skills, interests, and education attributes.</span></span> <span data-ttu-id="c808b-251">Mitglieder finden Experten in einer Organisation, die einer Stichwortsuche von Azure Active Directory-Benutzerprofilen entsprechen.</span><span class="sxs-lookup"><span data-stu-id="c808b-251">Members find experts within an organization  that match a keyword search of Azure Active Directory user profiles.</span></span>

[<span data-ttu-id="c808b-252">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-252">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-expertfinder)

![Demo zu Suchergebnissen der Expertensuche](../assets/images/expert-finder.png)

## <a name="faq-plus"></a><span data-ttu-id="c808b-254">FAQ Plus</span><span class="sxs-lookup"><span data-stu-id="c808b-254">FAQ Plus</span></span>

<span data-ttu-id="c808b-255">Unterhaltungs-F&Bots sind eine einfache Möglichkeit, Antworten auf häufig gestellte Fragen von Benutzern zur Verfügung zu stellen.</span><span class="sxs-lookup"><span data-stu-id="c808b-255">Conversational Q&A bots are an easy way to provide answers to frequently asked questions by users.</span></span> <span data-ttu-id="c808b-256">Die meisten Bots können jedoch nicht sinnvoll mit Benutzern interagieren, da kein Benutzer in der Schleife ist, wenn der Bot ausfällt.</span><span class="sxs-lookup"><span data-stu-id="c808b-256">However, most bots fail to engage with users in meaningful way because there is no human in the loop when the bot fails.</span></span> <span data-ttu-id="c808b-257">Faq bot is a friendly Q&A bot that brings a human in the loop when it is unable to help.</span><span class="sxs-lookup"><span data-stu-id="c808b-257">FAQ bot is a friendly Q&A bot that brings a human in the loop when it is unable to help.</span></span> <span data-ttu-id="c808b-258">Einer kann dem Bot eine Frage stellen, und der Bot antwortet mit einer Antwort, wenn er in der Wissensdatenbank enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="c808b-258">One can ask the bot a question and the bot responds with an answer if it is contained in the knowledge base.</span></span> <span data-ttu-id="c808b-259">Wenn nicht, ermöglicht der Bot dem Benutzer, eine Abfrage zu übermitteln, die dann an ein vorkonfiguriertes Expertenteam gesendet wird, das bei der Unterstützung hilft, indem er auf die Benachrichtigungen innerhalb des Teams selbst einwirken kann.</span><span class="sxs-lookup"><span data-stu-id="c808b-259">If not, the bot allows the user to submit a query which then gets posted to a pre-configured team of experts who help to provide support by acting upon the notifications from within the team itself.</span></span>

> [!NOTE]
> <span data-ttu-id="c808b-260">Die neueste Version von **FAQ Plus** unterstützt verbesserte Q&A-Lösungen, indem ein Expertenteam folgendes abschließen kann:</span><span class="sxs-lookup"><span data-stu-id="c808b-260">The latest release of **FAQ Plus** supports improved Q&A resolutions by enabling a team of experts to complete the following:</span></span>
>
> <span data-ttu-id="c808b-261">&#x2714; Hinzufügen neuer Fragen&Direkt zur Wissensdatenbank mithilfe von Nachrichtenerweiterungen.</span><span class="sxs-lookup"><span data-stu-id="c808b-261">&#x2714; Add new Q&As directly to the knowledge base using message extensions.</span></span>
>
> <span data-ttu-id="c808b-262">&#x2714; Bearbeiten und Löschen von Q&A pairs, die von einem Bot hinzugefügt wurden.</span><span class="sxs-lookup"><span data-stu-id="c808b-262">&#x2714; Edit and delete Q&A pairs added by a bot.</span></span>
>
> <span data-ttu-id="c808b-263">&#x2714; Verfolgen des Überarbeitungsverlaufs von Fragen&A0</span><span class="sxs-lookup"><span data-stu-id="c808b-263">&#x2714; Track the revision history of Q&As.</span></span>
>
> <span data-ttu-id="c808b-264">&#x2714; Konfigurieren Sie eine Antwort mit zusätzlichen Details, die als adaptive [Karte angezeigt werden.](../task-modules-and-cards/cards/cards-reference.md#adaptive-card)</span><span class="sxs-lookup"><span data-stu-id="c808b-264">&#x2714; Configure an answer with additional details to display as an [adaptive card](../task-modules-and-cards/cards/cards-reference.md#adaptive-card).</span></span>
>
[<span data-ttu-id="c808b-265">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-265">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-faqplusv2)

![HÄUFIG gestellte Fragen plus GIF](../assets/images/FAQPlusEndUser.gif)

## <a name="goal-tracker"></a><span data-ttu-id="c808b-267">Zielverfolgung</span><span class="sxs-lookup"><span data-stu-id="c808b-267">Goal Tracker</span></span>

<span data-ttu-id="c808b-268">Die Zielverfolgungs-App ist eine umfassende Lösung für Ihre Organisation, um das Einrichten von Zielen, das Beobachten des Fortschritts und die Anerkennung des Erfolgs in Microsoft Teams zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="c808b-268">The Goal Tracker app is a comprehensive solution for your organization to support establishing goals, observing progress, and acknowledging success within Microsoft Teams.</span></span> <span data-ttu-id="c808b-269">Mit der App können Benutzer Ziele auf professioneller, persönlicher und Teamebene festlegen, nachverfolgen und aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="c808b-269">The app enables users to set, track, and update objectives on a professional, personal, and team level.</span></span> <span data-ttu-id="c808b-270">Teammitglieder erhalten außerdem zeitnahe Erinnerungen und Statusupdates, um konzentriert zu bleiben und auf dem neuesten Stand zu bleiben.</span><span class="sxs-lookup"><span data-stu-id="c808b-270">Team members also receive timely reminders and status updates to remain focused and stay on track.</span></span>

[<span data-ttu-id="c808b-271">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-271">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-app-goaltracker)

:::row:::
  :::column span="2":::
    ![Festlegen von Zielen](../assets/images/goal-tracker-set-goals-view.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Ziele des Ansichtssatzes](../assets/images/goal-tracker-your-goals-view.png)
:::column-end:::
:::row-end:::

## <a name="great-ideas"></a><span data-ttu-id="c808b-274">Großartige Ideen</span><span class="sxs-lookup"><span data-stu-id="c808b-274">Great Ideas</span></span>

<span data-ttu-id="c808b-275">Die App "Großartige Ideen" unterstützt und fördert Innovation und Kreativität in Ihrer Organisation.</span><span class="sxs-lookup"><span data-stu-id="c808b-275">The Great Ideas app supports and empowers innovation and creativity within your organization.</span></span> <span data-ttu-id="c808b-276">Die App ermöglicht Es Ihren Mitarbeitern, Ideen mit Kollegen und Führungskräften auszutauschen, neue Übermittlungen zu entdecken, Beiträge zu Peers ins Blickpunkt zu stellen und ihre Stimme für die besten Vorschläge in Microsoft Teams zu geben.</span><span class="sxs-lookup"><span data-stu-id="c808b-276">The app enables your employees to share ideas with colleagues and leadership, discover new submissions, spotlight contributions for peer consideration, and cast their vote for the best proposals within Microsoft Teams.</span></span>

[<span data-ttu-id="c808b-277">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-277">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-greatideas)

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

## <a name="group-activities"></a><span data-ttu-id="c808b-280">Gruppenaktivitäten</span><span class="sxs-lookup"><span data-stu-id="c808b-280">Group Activities</span></span>

<span data-ttu-id="c808b-281">Gruppenaktivitäten ist eine Microsoft Teams-App, mit der Teambesitzer schnell Aktivitätsgruppen erstellen und Workflows für die Zusammenarbeit im Kontext von Microsoft Teams verwalten können.</span><span class="sxs-lookup"><span data-stu-id="c808b-281">Group Activities is a Microsoft Teams app that makes it easy for team owners to quickly create activity groups and manage collaboration workflows within the context of Microsoft Teams.</span></span> <span data-ttu-id="c808b-282">Aktivitätsautoren können Aktivitäten erstellen, Teammitglieder nach dem Zufallsprinzip in Gruppen verteilen und optional vom Bot Erinnerungen senden, bis die Aktivitäten abgeschlossen sind.</span><span class="sxs-lookup"><span data-stu-id="c808b-282">Activity authors are enabled to create activities, randomly distribute team members in groups, and optionally have the bot send reminders until activities are complete.</span></span>

[<span data-ttu-id="c808b-283">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-283">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-groupactivities)

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

## <a name="grow-your-skills"></a><span data-ttu-id="c808b-286">Erweitern Ihrer Fähigkeiten</span><span class="sxs-lookup"><span data-stu-id="c808b-286">Grow Your Skills</span></span>

<span data-ttu-id="c808b-287">Die App "Grow Your Skills" unterstützt das berufliche Wachstum und die Entwicklung, indem Mitarbeiter an ergänzenden Projekten für Ihre Organisation mit beitragen und gleichzeitig neue Fähigkeiten erlernen können.</span><span class="sxs-lookup"><span data-stu-id="c808b-287">The Grow Your Skills app supports professional growth and development by enabling employees to contribute to supplemental projects for your organization while simultaneously learning new skills.</span></span> <span data-ttu-id="c808b-288">Mitarbeiter können die App verwenden, um Möglichkeiten zu finden, die ihren Interessen entsprechen, eine sinnvolle Zusammenarbeit mit Gleichgesinnten zu genießen und neue Fachkenntnisse und Funktionen in der Teams-Umgebung zu erwerben.</span><span class="sxs-lookup"><span data-stu-id="c808b-288">Employees can use the app to locate opportunities that meet their interests, enjoy meaningful collaboration with peers, and acquire new levels of expertise and capabilities, all within the Teams environment.</span></span>

[<span data-ttu-id="c808b-289">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-289">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-growyourskills)

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

## <a name="hr-support"></a><span data-ttu-id="c808b-292">HR Support</span><span class="sxs-lookup"><span data-stu-id="c808b-292">HR Support</span></span>

<span data-ttu-id="c808b-293">Hr Support Bot ist ein freundlicher Q&Ein Bot, der einen Supportexperten/Experten aus dem Personalteam in die Schleife bringt, wenn er nicht helfen kann.</span><span class="sxs-lookup"><span data-stu-id="c808b-293">HR Support bot is a friendly Q&A bot that brings a support professional/expert from the HR team in the loop when it is unable to help.</span></span> <span data-ttu-id="c808b-294">Einer kann dem Bot eine Frage stellen, und der Bot antwortet mit einer Antwort, wenn er in der Wissensdatenbank enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="c808b-294">One can ask the bot a question and the bot responds with an answer if it is contained in the knowledge base.</span></span> <span data-ttu-id="c808b-295">Wenn nicht, ermöglicht der Bot dem Benutzer, eine Abfrage zu übermitteln, die dann in einem vorkonfigurierten Team von Experten veröffentlicht wird, die bei der Unterstützung helfen, indem er auf die Benachrichtigungen innerhalb des Teams selbst einwirken kann.</span><span class="sxs-lookup"><span data-stu-id="c808b-295">If not, the bot allows the user to submit a query which then gets posted in a pre-configured team of experts who are help to provide support by acting upon the notifications from within their team itself.</span></span> <span data-ttu-id="c808b-296">Darüber hinaus schlägt der Bot Links zu empfohlenen Personalrichtlinien/Fragen vor, indem er nach vorkonfigurierten Tags in der Frage sucht.</span><span class="sxs-lookup"><span data-stu-id="c808b-296">Additionally, the bot suggests links to recommended HR policies/questions by searching for pre-configured tags in the question.</span></span> <span data-ttu-id="c808b-297">Diese Kacheln befinden sich auch auf der zugeordneten Registerkarte als Kurzübersicht.</span><span class="sxs-lookup"><span data-stu-id="c808b-297">These tiles can also be found in the associated tab as a quick reference.</span></span> <span data-ttu-id="c808b-298">Der Personalsupport funktioniert gut für QnA mit geringem Gewicht und bietet schnellen Support beim Starten neuer Projekte/Initiativen in der Organisation.</span><span class="sxs-lookup"><span data-stu-id="c808b-298">HR Support works well for light weight QnA and to provide quick support when launching new projects/initiatives in the organization.</span></span>

[<span data-ttu-id="c808b-299">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-299">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-hrsupport-app)

![HR Support](../assets/images/expert-user.png)

## <a name="icebreaker"></a><span data-ttu-id="c808b-301">Icebreaker</span><span class="sxs-lookup"><span data-stu-id="c808b-301">Icebreaker</span></span>

<span data-ttu-id="c808b-302">Icebreaker ist ein [Microsoft Teams-Bot,](../bots/what-are-bots.md) der Ihrem Team dabei hilft, sich näher zu kommen, indem es jede Woche zwei zufällige Teammitglieder zu treffen paart.</span><span class="sxs-lookup"><span data-stu-id="c808b-302">Icebreaker is a [Microsoft Teams bot](../bots/what-are-bots.md) that helps your team get closer by pairing two random team members up every week to meet.</span></span> <span data-ttu-id="c808b-303">Der Bot erleichtert die Planung, indem automatisch kostenlose Zeiten vorschlagen werden, die für beide Mitglieder funktionieren.</span><span class="sxs-lookup"><span data-stu-id="c808b-303">The bot makes scheduling easy by automatically suggesting free times that work for both members.</span></span> <span data-ttu-id="c808b-304">Stärken Sie persönliche Verbindungen, und schaffen Sie mit dieser App eine enge Community.</span><span class="sxs-lookup"><span data-stu-id="c808b-304">Strengthen personal connections and build a tightly knit community with this app.</span></span>

<span data-ttu-id="c808b-305">Die Icebreaker-App fördert nicht nur persönliche Verbindungen im gesamten Team, sondern kann auch dazu beitragen, interessenbasierte Communitys in Ihrer Organisation zu fördern.</span><span class="sxs-lookup"><span data-stu-id="c808b-305">In addition to encouraging personal connections across your entire team, the Icebreaker app can help cultivate interest-based communities within your organization.</span></span> <span data-ttu-id="c808b-306">Beispielsweise können Sie diese App für eine DevOps-Interessengruppe verwenden, um Ideen und bewährte Methoden zu unterstützen, die organisch in Ihrer Organisation verteilt werden.</span><span class="sxs-lookup"><span data-stu-id="c808b-306">For example, you can use this app for a DevOps interest group to help ideas and best practices organically spread across your organization.</span></span>

[<span data-ttu-id="c808b-307">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-307">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-icebreaker-app)

![Icebreaker-App](../assets/images/icebreaker.png)

## <a name="incentives"></a><span data-ttu-id="c808b-309">Incentives</span><span class="sxs-lookup"><span data-stu-id="c808b-309">Incentives</span></span>

<span data-ttu-id="c808b-310">Incentives ist eine [Power Apps-Vorlage,](/powerapps/maker/canvas-apps/embed-teams-app) die die förderungsbewachte Mitarbeiterteilnahme an bestimmten Aktivitäten wie Schulungen und Change Management Initiative verwaltet und verfolgt.</span><span class="sxs-lookup"><span data-stu-id="c808b-310">Incentives is a [Power Apps](/powerapps/maker/canvas-apps/embed-teams-app) template that manages and tracks incentivized employee participation in designated activities such as trainings and change management initiatives.</span></span> <span data-ttu-id="c808b-311">Administratoren verwenden die App, um festgelegte Aktivitäten festzulegen, Punkte für den Abschluss zuzuordnen und erforderliche Berechtigungspunktstufen für Preise anzugeben.</span><span class="sxs-lookup"><span data-stu-id="c808b-311">Admins use the app to establish designated activities, assign points for completion, and specify required eligibility point levels for rewards.</span></span> <span data-ttu-id="c808b-312">Mitarbeiter verwenden die App, um ihre gesammelten Punkte zu sehen und, wenn sie die Berechtigung erreicht haben, einlösbare Preise anfordert und in Anspruch zu bekommen.</span><span class="sxs-lookup"><span data-stu-id="c808b-312">Employees use the app to view their accumulated points and, upon reaching eligibility, request and claim redeemable rewards.</span></span>

[<span data-ttu-id="c808b-313">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-313">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-incentives)

![Demo zur Anreiz-App](../assets/images/incentives-app.png)

## <a name="incident-reporter"></a><span data-ttu-id="c808b-315">Incident Reporter</span><span class="sxs-lookup"><span data-stu-id="c808b-315">Incident Reporter</span></span>

<span data-ttu-id="c808b-316">Incident Reporter ist ein [Microsoft Teams-Bot,](../bots/what-are-bots.md)  der die Verwaltung von Vorfällen in Ihrer Organisation optimiert.</span><span class="sxs-lookup"><span data-stu-id="c808b-316">Incident Reporter is a [Microsoft Teams bot](../bots/what-are-bots.md)  that optimizes the management of incidents in your organization.</span></span> <span data-ttu-id="c808b-317">Der Bot vereinfacht die automatisierte Erfassung von Vorfalldaten, angepasste Vorfallberichte, relevante Benachrichtigungen von Beteiligten und die End-to-End-Nachverfolgung von Vorfällen.</span><span class="sxs-lookup"><span data-stu-id="c808b-317">The bot facilitates automated incident data collection, customized incident reports, relevant stakeholder notifications, and end-to-end incident tracking.</span></span>

[<span data-ttu-id="c808b-318">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-318">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-incidentreport)

:::row:::
  :::column span="2":::
    ![Bereichsansicht der Vorfallberichtsgruppe](../assets/images/incident-reporter-02.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Vorfallberichtsansicht für persönlichen Bereich](../assets/images/incident-reporter-01.jpg)
:::column-end:::
:::row-end:::

## <a name="inspection-9734"></a><span data-ttu-id="c808b-321">&#9734;</span><span class="sxs-lookup"><span data-stu-id="c808b-321">Inspection &#9734;</span></span>

 <span data-ttu-id="c808b-322">Bei der Überprüfung handelt es sich um eine Microsoft Teams-App, mit der Front-Line-Mitarbeiter alles von Standorten bis hin zu Ressourcen und Geräten überprüfen können.</span><span class="sxs-lookup"><span data-stu-id="c808b-322">Inspection is a Microsoft Teams app that enables front line workers to inspect anything from  locations to assets and equipments.</span></span> <span data-ttu-id="c808b-323">Beispiel: Einzelhandel, Produktionsbetrieb oder Autos und Maschinen.</span><span class="sxs-lookup"><span data-stu-id="c808b-323">For example, a retail store, manufacturing plant, or vehicles and machines.</span></span> <span data-ttu-id="c808b-324">Es gibt zwei Apps in dieser Lösung, die jeweils für verschiedene Benutzertypen vorgesehen sind.</span><span class="sxs-lookup"><span data-stu-id="c808b-324">There are two apps in this solution, each intended for different types of users.</span></span>

<span data-ttu-id="c808b-325">Die App ermöglicht es den Front-Line-Mitarbeitern, ein Objekt oder einen Bereich zu überprüfen, die Qualität von Produkten und Diensten zu verwalten oder die Sicherheit am Arbeitsplatz zu gewährleisten.</span><span class="sxs-lookup"><span data-stu-id="c808b-325">The app empowers the front line workers to inspect an asset or area, to manage quality of products and services, or maintain safety at workplace.</span></span> <span data-ttu-id="c808b-326">Es erleichtert die Kommunikation zwischen Teammitgliedern, um während der Überprüfung gefundene Probleme zu beheben.</span><span class="sxs-lookup"><span data-stu-id="c808b-326">It facilitates communication between team members to address issues found during inspection.</span></span> <span data-ttu-id="c808b-327">Die App bietet einfachen Berichten für Manager, um die Problemlösung zu beschleunigen und Trends zu hervorheben.</span><span class="sxs-lookup"><span data-stu-id="c808b-327">The app provides simple reports for managers to expedite issue resolution and highlight trends.</span></span>

[<span data-ttu-id="c808b-328">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-328">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-inspection)

 ![Übersicht über die Überprüfung](../assets/images/inspection-app.png)  


## <a name="issue-reporting-9734"></a><span data-ttu-id="c808b-330">Problemberichterstattungsberichte &#9734;</span><span class="sxs-lookup"><span data-stu-id="c808b-330">Issue Reporting &#9734;</span></span>

<span data-ttu-id="c808b-331">Mit der App "Problemberichterstattung" können Mitarbeiter und Manager Probleme lösen und verwalten.</span><span class="sxs-lookup"><span data-stu-id="c808b-331">The Issue Reporting app empowers the employees and managers to raise and manage issues.</span></span> <span data-ttu-id="c808b-332">Sie besteht aus zwei Apps, der App "Problembericht" für die Berichterstellung und der App "Probleme verwalten" zum Verwalten von Problemen.</span><span class="sxs-lookup"><span data-stu-id="c808b-332">It consists of two apps, Issue reporting app for reporting issues and Manage Issues app for managing issues.</span></span>

<span data-ttu-id="c808b-333">Die Teammanager verwenden die App "Probleme verwalten", um die App zu konfigurieren, einschließlich des Kanals, in dem Microsoft Teams-Nachrichten und -Planner-Aufgaben von der App erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="c808b-333">The team managers use the Manage Issues app to configure the app experience, including the channel in which Microsoft Teams messages and Planner tasks are created by the app.</span></span> <span data-ttu-id="c808b-334">Manager verwenden die App auch zum Erstellen von Vorlagenformularen, um Details zu sammeln, wenn ein Benutzer ein Problem meldet.</span><span class="sxs-lookup"><span data-stu-id="c808b-334">Managers also use the app to create template forms to collect details when a user reports an issue.</span></span> <span data-ttu-id="c808b-335">Beispiel: Überprüfen, Bearbeiten oder Löschen von Formularen für Problemvorlagen.</span><span class="sxs-lookup"><span data-stu-id="c808b-335">For example, review, edit, or delete issue template forms.</span></span> <span data-ttu-id="c808b-336">Die App kann auch verwendet werden, um Teamprobleme zu überprüfen, einen Bericht zum Problemverlauf zu erstellen und die Problemlösung effizient zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="c808b-336">The app can also be used to review team issues, report on issue history, and efficiently manage issue resolution.</span></span>

<span data-ttu-id="c808b-337">Die Mitarbeiter verwenden die App "Problemberichterstattung", um Probleme und Details zu protokollieren, die zur Behebung dieser Probleme erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="c808b-337">The employees use the Issue reporting app to log issues and details required to resolve them.</span></span> <span data-ttu-id="c808b-338">Die App wird auch verwendet, um vorhandene Probleme zu ändern und zu beheben und eine hohe Ansicht von Einzel- oder Teamproblemen zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="c808b-338">The app is also used to modify and resolve existing issues and get a high-level view of individual or team issues.</span></span>

[<span data-ttu-id="c808b-339">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-339">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-issuereporting)

![Problemberichtsteamansicht](../assets/images/issue-reporting-team-view.png)  

## <a name="new-employee-onboarding"></a><span data-ttu-id="c808b-341">Onboarding neuer Mitarbeiter</span><span class="sxs-lookup"><span data-stu-id="c808b-341">New Employee Onboarding</span></span> 

<span data-ttu-id="c808b-342">Das Onboarding neuer Mitarbeiter ist eine integrierte Microsoft Teams- und [SharePoint New Employee Onboarding-Lösung,](https://lookbook.microsoft.com/details/75e60a32-9849-4ed4-b83e-b2b08983ad19) die es Ihrer Organisation ermöglicht, Mitarbeitern auf ihrer Reise nach Neueinstellungen eine konsistente, qualitativ hochwertige Onboardingerfahrung zu bieten.</span><span class="sxs-lookup"><span data-stu-id="c808b-342">New Employee Onboarding is an integrated Microsoft Teams and [SharePoint New Employee Onboarding Solution](https://lookbook.microsoft.com/details/75e60a32-9849-4ed4-b83e-b2b08983ad19) that enables your organization to provide a consistent, high-quality onboarding experience for employees on their new-hire journey.</span></span> <span data-ttu-id="c808b-343">Die App kann von Personalteams und Einstellungsmanagern verwendet werden, um während des gesamten Orientierungs- und Einstellungsprozesses relevante Informationen zur Verfügung zu stellen und von Neueinstellungen Feedback zu teilen, Einführungen zu geben und Onboardingaufgaben auszuführen.</span><span class="sxs-lookup"><span data-stu-id="c808b-343">The app can be used by human resource teams and hiring managers to provide relevant information throughout the orientation and induction process and by new hires to share feedback, provide introductions, and complete onboarding tasks.</span></span>

[<span data-ttu-id="c808b-344">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-344">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-newemployeeonboarding)

:::row:::
  :::column span="2":::
    <span data-ttu-id="c808b-345">**Willkommenskarte für neue Mitarbeiter** ![ Abbildung der Willkommenskarte für neue Mitarbeiter](../assets/images/new-employee-welcome-card.png)</span><span class="sxs-lookup"><span data-stu-id="c808b-345">**New employee welcome card** ![Image of new employee welcome card](../assets/images/new-employee-welcome-card.png)</span></span>
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    <span data-ttu-id="c808b-346">**Prüfliste für neue Mitarbeiter** ![ Abbildung der Prüfliste für neue Mitarbeiter](../assets/images/new-employee-checklist.png)</span><span class="sxs-lookup"><span data-stu-id="c808b-346">**New employee checklist** ![Image of new employee checklist](../assets/images/new-employee-checklist.png)</span></span>  
:::column-end:::
:::row-end:::

## <a name="open-badges"></a><span data-ttu-id="c808b-347">Öffnen von Signalen</span><span class="sxs-lookup"><span data-stu-id="c808b-347">Open Badges</span></span>

<span data-ttu-id="c808b-348">Open Badges ist eine Microsoft Teams-App, mit der Einzelpersonen digitale Lernanmeldeinformationen im Kontext von Teams erhalten und überall freigeben können.</span><span class="sxs-lookup"><span data-stu-id="c808b-348">Open Badges is a Microsoft Teams app that enables individuals to earn digital learning credential badges within the Teams context and share them everywhere.</span></span> <span data-ttu-id="c808b-349">Mithilfe von Funktionen der Drittanbieter-Zertifizierungsstelle für digitale Badges, [Badgr](https://badgr.org/), werden die vergebenen Badges im Badgr-Profil eines Empfängers aufgezeichnet und stehen zur Verfügung, um ein umfassendes Bild der lebensl.n-Lernerfahrungen zu erstellen und frei zu geben.</span><span class="sxs-lookup"><span data-stu-id="c808b-349">Using capabilities from the third-party digital badge issuing authority, [Badgr](https://badgr.org/), awarded badges are recorded in a recipient's Badgr profile and available to build and share a rich picture of lifetime learning journeys.</span></span>

[<span data-ttu-id="c808b-350">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-350">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-openbadges)

:::row:::
  :::column span="2":::
    ![Abbildung der verfügbaren Badges](../assets/images/open-badges-1.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Ansicht "Vergebene Badges"](../assets/images/open-badges-2.png)
:::column-end:::
:::row-end:::

## <a name="poll"></a><span data-ttu-id="c808b-353">Umfrage</span><span class="sxs-lookup"><span data-stu-id="c808b-353">Poll</span></span> 

<span data-ttu-id="c808b-354">Bei "Umfrage" [](../messaging-extensions/what-are-messaging-extensions.md) handelt es sich um eine benutzerdefinierte Microsoft Teams-Messaging-Erweiterungs-App, mit der Sie schnell Umfragen in einem Chat oder kanal erstellen und senden können, um Die meinungs- und präferenzen des Teams zu sammeln.</span><span class="sxs-lookup"><span data-stu-id="c808b-354">Poll is a custom Microsoft Teams [messaging extension](../messaging-extensions/what-are-messaging-extensions.md) app that enables you to quickly create and send polls in a chat or a channel to gather team opinions and preferences.</span></span> <span data-ttu-id="c808b-355">Die App wird auf allen Microsoft Teams-Plattformclients unterstützt – Desktop, Browser, iOS und Android – und kann im Rahmen Ihres Microsoft 365-Abonnements zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="c808b-355">The app is supported across all Teams platform clients — desktop, browser, iOS, and Android  — and is ready for deployment as part of your Microsoft 365 subscription.</span></span>

[<span data-ttu-id="c808b-356">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-356">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-poll-app)

:::row:::
  :::column span="1":::
    ![Erstellen einer Umfrage in der Ansicht "Teams"](../assets/images/poll-app-template-compose-view.gif)  
:::column-end:::
:::row-end:::

## <a name="quick-responses"></a><span data-ttu-id="c808b-358">Schnelle Antworten</span><span class="sxs-lookup"><span data-stu-id="c808b-358">Quick Responses</span></span>

<span data-ttu-id="c808b-359">Schnelle Antworten ist eine Microsoft Teams-App, die eine robuste Lösung für die effektive Beantwortung häufig gestellter Fragen (FAQs) der Benutzer bietet.</span><span class="sxs-lookup"><span data-stu-id="c808b-359">Quick Responses is a Microsoft Teams app that delivers a robust solution for effectively answering users' commonly asked questions (FAQs).</span></span> <span data-ttu-id="c808b-360">Anstatt jede Abfrage manuell und fortlaufend wiederholte Informationen zu beantworten, erstellt die App eine Bibliothek mit Antworten für eine interaktive Benutzererfahrung über [Teams-Messaging-Erweiterungen.](../messaging-extensions/what-are-messaging-extensions.md)</span><span class="sxs-lookup"><span data-stu-id="c808b-360">Instead of answering each query manually and  continuously repeating information, the app will build a library of responses for an interactive user experience via Teams [messaging extensions](../messaging-extensions/what-are-messaging-extensions.md).</span></span>

[<span data-ttu-id="c808b-361">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-361">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-quickresponses)

![Beispielansicht von Antworten](../assets/images/quick-responses.png)

## <a name="rapid-assist-9734"></a><span data-ttu-id="c808b-363">Rapid Assist &#9734;</span><span class="sxs-lookup"><span data-stu-id="c808b-363">Rapid Assist &#9734;</span></span>

<span data-ttu-id="c808b-364">Rapid Assist ist eine Microsoft [Power Platform-basierte](https://powerapps.microsoft.com/blog/now-in-preview-customize-teams-with-built-in-power-platform-capabilities/) App, mit der sich kundenorientierte Mitarbeiter schnell mit den Experten in Verbindung bringen können, um schnell Antworten zu erhalten, nach Informationen zu suchen, offene Anfragen zu verfolgen und Experten zu ermöglichen, Benachrichtigungen zu erhalten, um schnell einen Anruf zu erhalten, um Fragen zu beantworten.</span><span class="sxs-lookup"><span data-stu-id="c808b-364">Rapid Assist is a Microsoft [Power Platform](https://powerapps.microsoft.com/blog/now-in-preview-customize-teams-with-built-in-power-platform-capabilities/) based app that allows customer facing associates to rapidly connect with the experts to get quick answers, search for information, follow up open requests, and allow experts to receive notifications to quickly get on a call to help answer questions.</span></span> <span data-ttu-id="c808b-365">Die App, die mit Microsoft [Power Apps](/powerapps/powerapps-overview) und [Power Automate](/power-automate/getting-started)erstellt wurde, ist tief in Microsoft Teams integriert, damit Organisationen problemlos Front-Line-Mitarbeiter mit Unternehmenskontakten verbinden können, um Kundenanfragen zu lösen und eine großartige Kundenerfahrung zu bieten.</span><span class="sxs-lookup"><span data-stu-id="c808b-365">The app built using Microsoft [Power Apps](/powerapps/powerapps-overview) and [Power Automate](/power-automate/getting-started), deeply integrates with Microsoft Teams to enable organizations to easily connect frontline workers with corporate liaisons to resolve customer queries and deliver a great customer experience.</span></span> 

[<span data-ttu-id="c808b-366">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-366">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-rapid-assist)

:::row:::
   :::column span="":::
     ![Anforderungsschnittstelle für Endbenutzer](../assets/images/EndUserHome.png)
   :::column-end:::
   :::column span="":::
      ![Ansicht der Expertenanfrage](../assets/images/ExpertViewRequests.png)
   :::column-end:::
:::row-end:::

## <a name="reflect"></a><span data-ttu-id="c808b-369">Spiegeln</span><span class="sxs-lookup"><span data-stu-id="c808b-369">Reflect</span></span> 

<span data-ttu-id="c808b-370">Reflect ist eine [](../messaging-extensions/what-are-messaging-extensions.md) benutzerdefinierte Microsoft Teams-Messaging-Erweiterungs-App, die ihren Teammitgliedern eine sichere und inklusive Ressource bietet, um den Zustand ihres gefühlsmäßigen Wohlbefindens mit Kollegen und/oder Gruppenleitern direkt in Teams zu teilen.</span><span class="sxs-lookup"><span data-stu-id="c808b-370">Reflect is a custom Microsoft Teams [messaging extension](../messaging-extensions/what-are-messaging-extensions.md) app that provides a safe and inclusive resource for your team members to share the state of their emotional well-being with colleagues and/or group leaders directly within Teams.</span></span> <span data-ttu-id="c808b-371">Die App ist in Kanal-, Gruppen-, Besprechungs- und 1:1-Chats verfügbar, und die Eincheckantwort kann auf öffentlich, privat-zu-absender oder vollständig anonym festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="c808b-371">The app is available in channel, group, meeting, and 1:1 chats and the check-in response can be set to public, private-to-sender, or fully anonymous.</span></span>

[<span data-ttu-id="c808b-372">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-372">Get it on GitHub</span></span>](https://github.com/OfficeDev/Microsoft-Teams-App-Reflect)

:::row:::
    :::column:::
    <span data-ttu-id="c808b-373">**Well-Being-Umfrage**</span><span class="sxs-lookup"><span data-stu-id="c808b-373">**Well-being poll**</span></span>
    
    ![Spiegeln sie die Benutzerumfrage der App wider](../assets/images/reflect-app-user-poll.png)
    :::column-end:::
:::row-end:::

## <a name="remote-support"></a><span data-ttu-id="c808b-375">Remoteunterstützung</span><span class="sxs-lookup"><span data-stu-id="c808b-375">Remote Support</span></span>

<span data-ttu-id="c808b-376">Remote support is a [Microsoft Teams bot](../bots/what-are-bots.md) that provides a focused interface between support requesters throughout your organization and the internal support team.</span><span class="sxs-lookup"><span data-stu-id="c808b-376">Remote Support is a [Microsoft Teams bot](../bots/what-are-bots.md) that provides a focused interface between support requesters throughout your organization and the internal support team.</span></span>  <span data-ttu-id="c808b-377">Endbenutzer können Supportanfragen übermitteln, bearbeiten oder zurückziehen, und das Supportteam kann alle Anfragen innerhalb der Teams-Plattform beantworten, verwalten und aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="c808b-377">End-users can submit, edit, or withdraw requests for support and the support team can respond, manage, and update requests all within the Teams platform.</span></span>

[<span data-ttu-id="c808b-378">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-378">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-remotesupport)

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

## <a name="request-a-team"></a><span data-ttu-id="c808b-381">Request-a-team</span><span class="sxs-lookup"><span data-stu-id="c808b-381">Request-a-team</span></span>

<span data-ttu-id="c808b-382">"Team anfordern" ist eine Microsoft Teams-App, die die Erstellung neuer Teams für Ihre Unternehmensorganisation optimiert.</span><span class="sxs-lookup"><span data-stu-id="c808b-382">Request-a-team is a Microsoft Teams app that optimizes new team creation for your enterprise organization.</span></span> <span data-ttu-id="c808b-383">Die App unterstützt Standardisierung und bewährte Methoden beim Erstellen neuer Teaminstanzen durch die Integration eines assistentengesteuerten Anforderungsformulars, eines eingebetteten Genehmigungsprozesses, eines Anforderungsstatusdashboards und automatisierter Teambuilds.</span><span class="sxs-lookup"><span data-stu-id="c808b-383">The app supports standardization and best practices when creating new team instances through the integration of a wizard-guided request form, an embedded approval process, a request status dashboard, and automated team builds.</span></span>

[<span data-ttu-id="c808b-384">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-384">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-requestateam)

:::row:::
  :::column span="2":::
    ![Ansicht der Startseite "Team anfordern"](../assets/images/request-a-team-two.jpg)
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Seitenansicht des Assistenten zum Anfordern eines Teams](../assets/images/request-a-team-three.png)
:::column-end:::
:::row-end:::

## <a name="scrums-for-channels"></a><span data-ttu-id="c808b-387">Scrums für Kanäle</span><span class="sxs-lookup"><span data-stu-id="c808b-387">Scrums for Channels</span></span>

<span data-ttu-id="c808b-388">Scrums für Kanäle ist eine Scrum-Assistenten-App, mit der Benutzer Scrums in Kanälen in Microsoft Teams planen und ausführen können.</span><span class="sxs-lookup"><span data-stu-id="c808b-388">Scrums for Channels is a scrum assistant app that enables users to schedule and run scrums in channels within Microsoft Teams.</span></span> <span data-ttu-id="c808b-389">Die App ist ideal für Remoteteams und Teams, die aus Mitgliedern aus verschiedenen geografischen Standorten und Zeitzonen bestehen, um tägliche Updates gemeinsam zu nutzen und die Teilnahme an besprechungsgesteuerten Stand-up-Besprechungen sicherzustellen.</span><span class="sxs-lookup"><span data-stu-id="c808b-389">The app is great for remote teams and teams comprised of members from varied geographical locations and time zones to share daily updates and ensure participation in scrum stand-up meetings.</span></span>

[<span data-ttu-id="c808b-390">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-390">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-scrumsforchannels)

> [!NOTE]
> <span data-ttu-id="c808b-391">Informationen zum Durchführen von Scrumbesprechungen in einem Gruppenchat finden Sie in der [Appvorlage "Scrums für Gruppenchat".](#scrums-for-group-chat)</span><span class="sxs-lookup"><span data-stu-id="c808b-391">To conduct scrum meetings in a group chat, please see our [Scrums for Group Chat](#scrums-for-group-chat) app template.</span></span>

:::row:::
  :::column span="2":::
    ![Ansicht "Scrums für Kanaleinstellungen"](../assets/images/scrum-for-channels-settings.png)
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Scrums für Die Statusansicht des Kanalteammitglieds](../assets/images/scrum-for-channels-status.png)
:::column-end:::
:::row-end:::

## <a name="scrums-for-group-chat"></a><span data-ttu-id="c808b-394">Scrums für Gruppenchat</span><span class="sxs-lookup"><span data-stu-id="c808b-394">Scrums for Group Chat</span></span>

> [!NOTE]
> <span data-ttu-id="c808b-395">Die Vorlage "Scrums Status"-App wurde aktualisiert und heißt jetzt Scrums für Gruppenchat.</span><span class="sxs-lookup"><span data-stu-id="c808b-395">The Scrums Status app template has been updated and is now Scrums for Group Chat.</span></span>

<span data-ttu-id="c808b-396">Scrums für Gruppenchat ist ein unterstützender Scrum-Assistent, mit dem Gruppenchatmitglieder asynchrone Stand-up-Besprechungen ausführen und ihre täglichen Updates problemlos freigeben können.</span><span class="sxs-lookup"><span data-stu-id="c808b-396">Scrums for Group Chat is a supportive scrum assistant that enables group chat members to run asynchronous stand-up meetings and easily share their daily updates.</span></span> <span data-ttu-id="c808b-397">Es ermöglicht allen Mitgliedern des Gruppenchats, zum Scrum beizutragen und die Von anderen im ausgeführten Scrum vorgenommenen Updates zu sehen.</span><span class="sxs-lookup"><span data-stu-id="c808b-397">It allows all members of the group chat to contribute to the scrum and view the updates made by others in the running scrum.</span></span>

[<span data-ttu-id="c808b-398">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-398">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-scrumsforgroupchat)

![Scrums für Gruppenchatdemo](https://raw.githubusercontent.com/wiki/OfficeDev/microsoft-teams-app-scrumstatus/images/StartScrum.jpg)

## <a name="share-now"></a><span data-ttu-id="c808b-400">Jetzt freigeben</span><span class="sxs-lookup"><span data-stu-id="c808b-400">Share Now</span></span> 

<span data-ttu-id="c808b-401">Die App "Jetzt freigeben" fördert den positiven Austausch von Informationen zwischen Kollegen, indem Ihren Benutzern das einfache Freigeben von Inhalten in der Teams-Umgebung ermöglicht wird.</span><span class="sxs-lookup"><span data-stu-id="c808b-401">The Share Now app promotes the positive exchange of information between colleagues by enabling your users to easily share content within the Teams environment.</span></span> <span data-ttu-id="c808b-402">Benutzer interagieren mit der App, um elemente von Interesse mit Teammitgliedern zu teilen, neue freigegebene Inhalte zu entdecken, Einstellungen und Lesezeichenfavoriten zum späteren Lesen zu setzen.</span><span class="sxs-lookup"><span data-stu-id="c808b-402">Users engage the app to share items of interest with team members, discover new shared content, set preferences, and bookmark favorites for later reading.</span></span>

[<span data-ttu-id="c808b-403">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-403">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-sharenow)

![Auswählen der Inhaltsansicht](../assets/images/share-now-suggested-content.png)

## <a name="sharepoint-list-search"></a><span data-ttu-id="c808b-405">SharePoint-Listensuche</span><span class="sxs-lookup"><span data-stu-id="c808b-405">SharePoint List Search</span></span>

<span data-ttu-id="c808b-406">Die Zusammenarbeit in Microsoft Teams verweist häufig auf Informationen, die in Elementen in einer SharePoint-Liste enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="c808b-406">Collaboration in Microsoft Teams quite often references information contained within items in a SharePoint list.</span></span> <span data-ttu-id="c808b-407">Durch das einfache Einf?nen eines Links zu dem in Frage stehenden Element wird jeder dazu verf?ungen, den Kontext von der Unterhaltung weg zu wechseln, die erforderlichen Informationen zu finden und dann zu Teams zurückzukehren, um die Unterhaltung fortzufahren.</span><span class="sxs-lookup"><span data-stu-id="c808b-407">Simply pasting a link to the item in question forces everyone to switch context away from the conversation, find the needed information, then return to Teams to continue the conversation.</span></span> <span data-ttu-id="c808b-408">Wenn die Unterhaltung fortgesetzt wird, müssen Die Benutzer in der Regel mehrmals zum Referenzelement wechseln, um neue Kommentare zu überprüfen und die darin enthaltenen Informationen zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="c808b-408">As the conversation continues typically people will have to switch back to the reference item multiple times to verify new comments and refresh their memories of the information contained within the item.</span></span> <span data-ttu-id="c808b-409">Dieser Kontextwechsel schafft eine Barriere für eine reibungslose Zusammenarbeit und ist ein Rezept für Dinge, die durch die Risse fallen.</span><span class="sxs-lookup"><span data-stu-id="c808b-409">This context switching creates a barrier to smooth collaboration, and is a recipe for things falling through the cracks.</span></span>

<span data-ttu-id="c808b-410">Um diese Probleme zu mindern, freuen wir uns, Ihnen die App-Vorlage "Listensuche" zur Hilfe zu bringen.</span><span class="sxs-lookup"><span data-stu-id="c808b-410">To help alleviate this pain, we are happy to bring to you the List Search app template.</span></span> <span data-ttu-id="c808b-411">Millionen von Benutzern verwenden SharePoint, um einige der wichtigsten Workflows in ihren Organisationen zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="c808b-411">Millions of users use SharePoint to power some of the core workflows in their organizations.</span></span> <span data-ttu-id="c808b-412">Die Zusammenarbeit an Listen kann jedoch besonders mühsam sein.</span><span class="sxs-lookup"><span data-stu-id="c808b-412">However, collaborating around lists can be especially tedious.</span></span> <span data-ttu-id="c808b-413">Mithilfe der Listensuche-App-Vorlage in Microsoft Teams können Benutzer Informationen aus SharePoint-Listenelementen direkt in eine Chat unterhaltung einfügen, um den Kontextwechsel zu mindern, der beim einfachen Einfügen eines Links in einen Chat verursacht wird.</span><span class="sxs-lookup"><span data-stu-id="c808b-413">Using the List Search app template in Microsoft Teams, users can insert information from SharePoint list items directly within a chat conversation to alleviate the context-switching caused when simply inserting a link into a chat.</span></span> <span data-ttu-id="c808b-414">Die Informationen werden als leicht lesbare, automatisch formatierte Karte eingefügt, die Ihren Benutzern dabei hilft, an der Unterhaltung zu bleiben.</span><span class="sxs-lookup"><span data-stu-id="c808b-414">The information is inserted as an easy-to-read auto-formatted card, helping your users stay engaged in the conversation.</span></span>

[<span data-ttu-id="c808b-415">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-415">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-list-search-app)

![Such-App auflisten](../assets/images/list-search-template.png)

## <a name="staff-check-ins"></a><span data-ttu-id="c808b-417">Einchecken von Mitarbeitern</span><span class="sxs-lookup"><span data-stu-id="c808b-417">Staff Check-ins</span></span>

<span data-ttu-id="c808b-418">Bei Den Einchecken von Mitarbeitern handelt es sich um [eine Power Apps-basierte](/powerapps/powerapps-overview)App, die die Aufsichtskommunikation zwischen Ihrem Geschäfts- und Außenpersonal ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="c808b-418">Staff Check-ins is a [Power Apps](/powerapps/powerapps-overview)-based app that enables oversight communication between your business and field personnel.</span></span> <span data-ttu-id="c808b-419">Mitarbeiter können auf einfache Weise zeitkritische Informationen und Statusaktualisierungen entweder geplant oder ad-hoc direkt aus Teams bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="c808b-419">Staff can easily provide time-critical information and status updates on either a scheduled or ad-hoc basis directly from Teams.</span></span> <span data-ttu-id="c808b-420">Die App unterstützt Echtzeitspeicherort, Fotos und Notizen sowie Erinnerungsbenachrichtigungen und automatisierte Workflows.</span><span class="sxs-lookup"><span data-stu-id="c808b-420">The app supports real-time location, photos, and notes as well as reminder notifications and automated workflows.</span></span>

[<span data-ttu-id="c808b-421">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-421">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-staffcheckins)

![Erstellen der Eincheckansicht](../assets/images/staff-check-ins-create.png)

## <a name="survey"></a><span data-ttu-id="c808b-423">Umfrage</span><span class="sxs-lookup"><span data-stu-id="c808b-423">Survey</span></span>

<span data-ttu-id="c808b-424">Umfrage ist eine [](../messaging-extensions/what-are-messaging-extensions.md) benutzerdefinierte Microsoft Teams-Messaging-Erweiterungs-App, mit der Sie eine Umfrage in einem Chat oder kanal erstellen können, um Daten zu sammeln und einblicke zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="c808b-424">Survey is a custom Microsoft Teams [messaging extension](../messaging-extensions/what-are-messaging-extensions.md) app that enables you to create a survey in a chat or a channel to gather data and gain actionable insight.</span></span>  <span data-ttu-id="c808b-425">Die App wird auf allen Microsoft Teams-Plattformclients unterstützt – Desktop, Browser, iOS und Android – und kann im Rahmen Ihres Microsoft 365-Abonnements zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="c808b-425">The app is supported across all Teams platform clients — desktop, browser, iOS, and Android — and is ready for deployment as part of your Microsoft 365 subscription.</span></span>  

[<span data-ttu-id="c808b-426">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-426">Get it on GitHub</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Survey-app)

:::row:::
  :::column span="2":::
    ![Erstellen einer Umfrage in der Ansicht "Teams"](../assets/images/survey-app-template-compose-view.gif)
:::column-end:::
:::row-end:::

## <a name="virtual-rounding-9734"></a><span data-ttu-id="c808b-428">Virtuelles Rundungs&#9734;</span><span class="sxs-lookup"><span data-stu-id="c808b-428">Virtual Rounding &#9734;</span></span>

<span data-ttu-id="c808b-429">Krankenhaus- und Notaufnahmeanbieter nehmen Dutzende und häufig Hunderte von "Runden" pro Tag vor.</span><span class="sxs-lookup"><span data-stu-id="c808b-429">Hospital and emergency room providers make dozens, and often hundreds of “rounds” per day.</span></span> <span data-ttu-id="c808b-430">Diese schnellen Einchecken für Patienten sollen eine Statusüberprüfung der Behandlung des Patienten ermöglichen und sicherstellen, dass die Bedenken des Patienten behoben werden.</span><span class="sxs-lookup"><span data-stu-id="c808b-430">These quick check-ins on patients are intended to provide a status check on how the patient is doing and ensure that the patient’s concerns are addressed.</span></span> <span data-ttu-id="c808b-431">Die Rundung ist zwar eine wesentliche Methode, um sicherzustellen, dass Patienten von mehreren Anbietertypen überwacht werden, sie stellen jedoch eine große Ppe dar, da für jeden Besuch, von jedem Anbieter eine neue Maske und neue Abläufe verwendet werden müssen.</span><span class="sxs-lookup"><span data-stu-id="c808b-431">While rounding is an essential practice to ensure patients are being monitored by multiple types of providers, they represent a huge drain on PPE, because for each visit, from each provider, a new mask, and new set of gloves must be used.</span></span> <span data-ttu-id="c808b-432">Mit diesen App-Vorlagen können Medizinischer Mitarbeiter über eine Microsoft Teams-Besprechung zwischen dem Anbieter und dem Patienten auf einfache Weise Runden durchführen.</span><span class="sxs-lookup"><span data-stu-id="c808b-432">With this app templates, medical workers can easily conduct rounds virtually, through a Microsoft Teams meeting between the provider and the patient.</span></span>

<span data-ttu-id="c808b-433">Auf die virtuelle Rundungslösung wird auch im Microsoft Health and Life [Science-Blogbeitrag verwiesen.](https://aka.ms/teamsvirtualrounding)</span><span class="sxs-lookup"><span data-stu-id="c808b-433">The Virtual Rounding solution is also referenced in the Microsoft Health and Life Sciences [blog post](https://aka.ms/teamsvirtualrounding).</span></span>

[<span data-ttu-id="c808b-434">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-434">Get it on GitHub</span></span>](https://github.com/SmartterHealth/Virtual-Rounding)

![Virtuelles Runden](../assets/images/virtual-rounding-overview.png)

## <a name="visitor-management"></a><span data-ttu-id="c808b-436">Besucherverwaltung</span><span class="sxs-lookup"><span data-stu-id="c808b-436">Visitor Management</span></span>

<span data-ttu-id="c808b-437">Mit der Besucherverwaltungs-App können Ihre Organisation und Ihre Mitarbeiter den Besucherprozess vor Ort ganz einfach und effizient direkt in Microsoft Teams verwalten.</span><span class="sxs-lookup"><span data-stu-id="c808b-437">The Visitor Management app enables your organization and employees to easily and efficiently manage the on-site visitor process, directly from Microsoft Teams.</span></span> <span data-ttu-id="c808b-438">Die App ermöglicht Mitarbeitern das Erstellen von Besucheranfragen, das zentrale Nachverfolgen eines Anforderungsstatus über das Besucherdashboard und das Empfangen von Echtzeitbenachrichtigungen, wenn ein Besucher eintrifft.</span><span class="sxs-lookup"><span data-stu-id="c808b-438">The app enables employees to create visitor requests, centrally track a request status through the visitor dashboard, and receive real-time notifications when a visitor arrives.</span></span>

[<span data-ttu-id="c808b-439">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-439">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-app-visitormanagement)

:::row:::
  :::column span="2":::
    ![Erstellen einer Anforderungsansicht](../assets/images/visitor-management-create-request.png)
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Benachrichtigung über besucherantreffende Besucher](../assets/images/visitor-management-notify-host.png)
:::column-end:::
:::row-end:::

## <a name="workplace-awards"></a><span data-ttu-id="c808b-442">Workplace Award</span><span class="sxs-lookup"><span data-stu-id="c808b-442">Workplace Awards</span></span>

<span data-ttu-id="c808b-443">Workplace Award ist eine Teams-App-Vorlage, die einen positiven Rahmen bietet, um die Erkennung zu fördern und die Kultur der Anerkennung von Mitarbeitern am modernen Arbeitsplatz zu fördern.</span><span class="sxs-lookup"><span data-stu-id="c808b-443">Workplace Awards is a Teams app template that provides a positive framework to foster recognition and encourage the culture of employee appreciation in the modern workplace.</span></span> <span data-ttu-id="c808b-444">Mit der App können Sie ein Mitarbeiterpreis- und Anerkennungsprogramm (R&R) einrichten und verwalten, bei dem Mitarbeiter Kollegen problemlos ernennen und unterstützen können und Ihr R&R-Leiter eingereichte Benennungen anzeigen, Preise gewähren und Empfänger ankündigen kann.</span><span class="sxs-lookup"><span data-stu-id="c808b-444">The app enables you to setup and manage an employee rewards and recognition (R&R) program where employees can easily nominate and endorse colleagues and your R&R leader can view submitted nominations, grant awards, and announce recipients.</span></span>

[<span data-ttu-id="c808b-445">Abrufen auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c808b-445">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-workplaceawards)

:::row:::
  :::column span="2":::
    ![<span data-ttu-id="c808b-446">Workplace-Preis-Benennungskarte</span><span class="sxs-lookup"><span data-stu-id="c808b-446">Workplace awards nomination card</span></span> ](../assets/images/workplace-awards-nominate.png)
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Registerkarte "Workplace-Preisliste"](../assets/images/workplace-awards-champion-tab.png)
:::column-end:::
:::row-end:::

<span data-ttu-id="c808b-448">Haben Sie eine Idee für eine App-Vorlage, die Sie sehen möchten?</span><span class="sxs-lookup"><span data-stu-id="c808b-448">Have an idea for an app template you'd like to see?</span></span> <span data-ttu-id="c808b-449">[Teilen Sie uns dies bitte mit.](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR2_7qFm_lcZAr4eqEhnLsZ9UMVZGT1lCT0FXUDdZMUM0RkpBS1BESTAwWC4u)</span><span class="sxs-lookup"><span data-stu-id="c808b-449">[Please let us know](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR2_7qFm_lcZAr4eqEhnLsZ9UMVZGT1lCT0FXUDdZMUM0RkpBS1BESTAwWC4u).</span></span>
