---
title: Entwerfen Ihrer Registerkarte für Desktop und Web
description: Erfahren Sie, wie Sie eine Registerkarte Teams (Desktop und Web) entwerfen und das Microsoft Teams UI Kit erhalten.
author: heath-hamilton
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 840cb9f65f867358615ea006594433d8a1099111
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019685"
---
# <a name="designing-your-tab-for-microsoft-teams-desktop-and-web"></a><span data-ttu-id="21fcb-103">Entwerfen Ihrer Registerkarte für Microsoft Teams Desktop und Web</span><span class="sxs-lookup"><span data-stu-id="21fcb-103">Designing your tab for Microsoft Teams desktop and web</span></span>

<span data-ttu-id="21fcb-104">Eine Registerkarte ist ein großer Canvas-Bereich für Ihre Inhalte.</span><span class="sxs-lookup"><span data-stu-id="21fcb-104">A tab is a large canvas for your content.</span></span> <span data-ttu-id="21fcb-105">Um Ihr App-Design zu leiten, wird in den folgenden Informationen beschrieben und veranschaulicht, wie Benutzer Registerkarten in Teams hinzufügen, verwenden und verwalten können.</span><span class="sxs-lookup"><span data-stu-id="21fcb-105">To guide your app design, the following information describes and illustrates how people can add, use, and manage tabs in Teams.</span></span>

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="21fcb-106">Microsoft Teams-UI-Kit</span><span class="sxs-lookup"><span data-stu-id="21fcb-106">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="21fcb-107">Im Microsoft Teams UI Kit finden Sie umfassende Richtlinien für den Registerkartenentwurf, einschließlich Elemente, die Sie bei Bedarf packen und ändern können.</span><span class="sxs-lookup"><span data-stu-id="21fcb-107">You can find comprehensive tab design guidelines, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span> <span data-ttu-id="21fcb-108">Das Benutzeroberflächenkit enthält auch wichtige Themen wie Barrierefreiheit und reaktionsschnelle Größenanpassung, die hier nicht behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="21fcb-108">The UI kit also has essential topics such as accessibility and responsive sizing that aren't covered here.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="21fcb-109">Holen Sie sich das Microsoft Teams-UI-Kit (Figma)</span><span class="sxs-lookup"><span data-stu-id="21fcb-109">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-tab"></a><span data-ttu-id="21fcb-110">Registerkarte hinzufügen</span><span class="sxs-lookup"><span data-stu-id="21fcb-110">Add a tab</span></span>

<span data-ttu-id="21fcb-111">Sie können eine Registerkarte aus dem Teams Store (AppSource) oder in einem der folgenden Kontexte hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="21fcb-111">You can add a tab from the Teams store (AppSource) or in one of the following contexts:</span></span>

* <span data-ttu-id="21fcb-112">Chat</span><span class="sxs-lookup"><span data-stu-id="21fcb-112">Chat</span></span>
* <span data-ttu-id="21fcb-113">Kanal</span><span class="sxs-lookup"><span data-stu-id="21fcb-113">Channel</span></span>
* <span data-ttu-id="21fcb-114">Besprechung (vor, während oder nach der Besprechung)</span><span class="sxs-lookup"><span data-stu-id="21fcb-114">Meeting (before, during, or after the meeting)</span></span>

<span data-ttu-id="21fcb-115">Das folgende Beispiel zeigt, wie eine Registerkarte in einem Kanal hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="21fcb-115">The following example shows how a tab is added in a channel.</span></span>

:::image type="content" source="../../assets/images/tabs/design-add-tab.png" alt-text="Beispiel zeigt eine Registerkarte, die in einem Kanal hinzugefügt wird." border="false":::

## <a name="set-up-a-tab"></a><span data-ttu-id="21fcb-117">Einrichten einer Registerkarte</span><span class="sxs-lookup"><span data-stu-id="21fcb-117">Set up a tab</span></span>

<span data-ttu-id="21fcb-118">Es gibt einen kurzen Einrichtungsprozess zum Hinzufügen einer App als Kanal, Chat oder Besprechungsregisterkarte. Die Erfahrung liegt weitgehend bei Ihnen.</span><span class="sxs-lookup"><span data-stu-id="21fcb-118">There's a short setup process to add an app as a channel, chat, or meeting tab. The experience is largely up to you.</span></span> <span data-ttu-id="21fcb-119">Sie könnten beispielsweise eine Beschreibung der Verwendung der App und einige optionale Einstellungen haben.</span><span class="sxs-lookup"><span data-stu-id="21fcb-119">For example, you could have a description of how to use the app and some optional settings.</span></span> <span data-ttu-id="21fcb-120">Schließen Sie hier einen Anmeldeschritt ein, wenn Sie Benutzer authentifizieren müssen.</span><span class="sxs-lookup"><span data-stu-id="21fcb-120">Include a sign-in step here if you need to authenticate users.</span></span>

### <a name="tab-configuration-modal"></a><span data-ttu-id="21fcb-121">Modale Registerkartenkonfiguration</span><span class="sxs-lookup"><span data-stu-id="21fcb-121">Tab configuration modal</span></span>

:::image type="content" source="../../assets/images/tabs/design-set-up-tab-config.png" alt-text="Beispiel zeigt eine modale Registerkartenkonfiguration." border="false":::

### <a name="anatomy-tab-configuration-modal"></a><span data-ttu-id="21fcb-123">Anatomie: Modale Tabkonfiguration</span><span class="sxs-lookup"><span data-stu-id="21fcb-123">Anatomy: Tab configuration modal</span></span>

:::image type="content" source="../../assets/images/tabs/test.png" alt-text="Abbildung der Ui-Anatomie einer modalen Registerkartenkonfiguration." border="false":::

|<span data-ttu-id="21fcb-125">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="21fcb-125">Counter</span></span>|<span data-ttu-id="21fcb-126">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="21fcb-126">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="21fcb-127">1</span><span class="sxs-lookup"><span data-stu-id="21fcb-127">1</span></span>|<span data-ttu-id="21fcb-128">**App-Logo:** Vollfarbiges App-Logo Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="21fcb-128">**App logo**: Full color app logo of your app.</span></span>|
|<span data-ttu-id="21fcb-129">2</span><span class="sxs-lookup"><span data-stu-id="21fcb-129">2</span></span>|<span data-ttu-id="21fcb-130">**App-Name**: Vollständiger Name Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="21fcb-130">**App name**: Full name of your app.</span></span>|
|<span data-ttu-id="21fcb-131">3</span><span class="sxs-lookup"><span data-stu-id="21fcb-131">3</span></span>|<span data-ttu-id="21fcb-132">**iframe**: Responsive space for your app's content (for example, tab settings or authentication).</span><span class="sxs-lookup"><span data-stu-id="21fcb-132">**iframe**: Responsive space for your app’s content (for example, tab settings or authentication).</span></span>|
|<span data-ttu-id="21fcb-133">4 </span><span class="sxs-lookup"><span data-stu-id="21fcb-133">4</span></span>|<span data-ttu-id="21fcb-134">**Über Link**: Öffnet ein Dialogfeld, in dem weitere Informationen zur App angezeigt werden, z. B. eine vollständige Beschreibung, von der App erforderliche Berechtigungen und Links zu Ihrer Datenschutzrichtlinie und den Nutzungsbedingungen.</span><span class="sxs-lookup"><span data-stu-id="21fcb-134">**About link**: Opens a dialog showing more information about the app, such as a full description, permissions required by the app, and links to your privacy policy and terms of service.</span></span>
|<span data-ttu-id="21fcb-135">5 </span><span class="sxs-lookup"><span data-stu-id="21fcb-135">5</span></span>|<span data-ttu-id="21fcb-136">**Schaltfläche Schließen**: Schließt den modalen.</span><span class="sxs-lookup"><span data-stu-id="21fcb-136">**Close button**: Closes the modal.</span></span>|
|<span data-ttu-id="21fcb-137">6 </span><span class="sxs-lookup"><span data-stu-id="21fcb-137">6</span></span>|<span data-ttu-id="21fcb-138">**Option Teammitglieder benachrichtigen:** Der Modal fragt, ob Sie einen Beitrag erstellen möchten, der andere darüber informiert, dass Sie eine Registerkarte hinzugefügt haben.</span><span class="sxs-lookup"><span data-stu-id="21fcb-138">**Notify team members option**: The modal asks if you want to create a post letting others know you added a tab.</span></span>|
|<span data-ttu-id="21fcb-139">7 </span><span class="sxs-lookup"><span data-stu-id="21fcb-139">7</span></span>|<span data-ttu-id="21fcb-140">**Schaltfläche "Zurück":** Geht zum vorherigen Schritt, basierend auf dem Ort, an dem das Dialogfeld geöffnet wurde.</span><span class="sxs-lookup"><span data-stu-id="21fcb-140">**Back button**: Goes to the previous step based on where the dialog opened.</span></span>|
|<span data-ttu-id="21fcb-141">8 </span><span class="sxs-lookup"><span data-stu-id="21fcb-141">8</span></span>|<span data-ttu-id="21fcb-142">**Schaltfläche "Speichern":** Schließt die Registerkarteneinrichtung ab.</span><span class="sxs-lookup"><span data-stu-id="21fcb-142">**Save button**: Completes tab setup.</span></span>|

### <a name="tab-authentication-with-single-sign-on"></a><span data-ttu-id="21fcb-143">Registerkartenauthentifizierung mit einmaligem Anmelden</span><span class="sxs-lookup"><span data-stu-id="21fcb-143">Tab authentication with single sign-on</span></span>

<span data-ttu-id="21fcb-144">Sie können einen Schritt hinzufügen, in dem sich Benutzer zuerst mit ihren Microsoft-Anmeldeinformationen anmelden müssen.</span><span class="sxs-lookup"><span data-stu-id="21fcb-144">You can add a step in which users must first sign in with their Microsoft credentials.</span></span> <span data-ttu-id="21fcb-145">Diese Authentifizierungsmethode wird als einmaliges Anmelden (Single Sign-On, SSO) bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="21fcb-145">This authentication method is called single sign-on (SSO).</span></span>

:::image type="content" source="../../assets/images/tabs/design-set-up-tab-auth.png" alt-text="Beispiel zeigt einen Registerkartenauthentifizierungsbildschirm." border="false":::

### <a name="designing-a-tab-setup-with-ui-templates"></a><span data-ttu-id="21fcb-147">Entwerfen einer Registerkarteneinrichtung mit Benutzeroberflächenvorlagen</span><span class="sxs-lookup"><span data-stu-id="21fcb-147">Designing a tab setup with UI templates</span></span>

<span data-ttu-id="21fcb-148">Verwenden Sie eine der folgenden Teams-UI-Vorlagen, um die Einrichtung ihrer Registerkarten zu gestalten:</span><span class="sxs-lookup"><span data-stu-id="21fcb-148">Use one of the following Teams UI templates to help design your tab setup experience:</span></span>

* <span data-ttu-id="21fcb-149">[Liste](../../concepts/design/design-teams-app-ui-templates.md#list): Listen können verwandte Elemente in einem scannierbaren Format anzeigen und Benutzern das Ausführen von Aktionen für eine gesamte Liste oder einzelne Elemente ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="21fcb-149">[List](../../concepts/design/design-teams-app-ui-templates.md#list): Lists can display related items in a scannable format and allow users to take actions on an entire list or individual items.</span></span>
* <span data-ttu-id="21fcb-150">[Formular](../../concepts/design/design-teams-app-ui-templates.md#form): Formulare sind für die strukturierte Erfassung, Validierung und Übermittlung von Benutzereingaben.</span><span class="sxs-lookup"><span data-stu-id="21fcb-150">[Form](../../concepts/design/design-teams-app-ui-templates.md#form): Forms are for collecting, validating, and submitting user input in a structured way.</span></span>
* <span data-ttu-id="21fcb-151">[Leerer](../../concepts/design/design-teams-app-ui-templates.md#empty-state)Zustand: Die Vorlage für den leeren Zustand kann für viele Szenarien verwendet werden, z. B. für die Anmeldung, die Erstlauferfahrung, Fehlermeldungen und vieles mehr.</span><span class="sxs-lookup"><span data-stu-id="21fcb-151">[Empty state](../../concepts/design/design-teams-app-ui-templates.md#empty-state): The empty state template can be used for many scenarios, including sign in, first-run experiences, error messages, and more.</span></span>

## <a name="view-a-tab"></a><span data-ttu-id="21fcb-152">Anzeigen einer Registerkarte</span><span class="sxs-lookup"><span data-stu-id="21fcb-152">View a tab</span></span>

<span data-ttu-id="21fcb-153">Registerkarten bieten eine Vollbildweberfahrung in Teams, in der Sie gemeinsame Inhalte wie Aufgabenboards und Dashboards sowie wichtige Informationen anzeigen können.</span><span class="sxs-lookup"><span data-stu-id="21fcb-153">Tabs provide a full-screen web experience in Teams where you can display collaborative content—such task boards and dashboards—and important information.</span></span>

:::image type="content" source="../../assets/images/tabs/design-view-tab.png" alt-text="Beispiel zeigt eine Registerkarte mit einem Aufgabenboard." border="false":::

### <a name="anatomy-tab"></a><span data-ttu-id="21fcb-155">Anatomie: Registerkarte</span><span class="sxs-lookup"><span data-stu-id="21fcb-155">Anatomy: Tab</span></span>

:::image type="content" source="../../assets/images/tabs/design-view-tab-anatomy.png" alt-text="Abbildung der Ui-Anatomie einer Registerkarte." border="false":::

|<span data-ttu-id="21fcb-157">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="21fcb-157">Counter</span></span>|<span data-ttu-id="21fcb-158">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="21fcb-158">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="21fcb-159">1</span><span class="sxs-lookup"><span data-stu-id="21fcb-159">1</span></span>|<span data-ttu-id="21fcb-160">**Registerkartenname:** Navigationsbezeichnung für Ihre Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="21fcb-160">**Tab name**: Navigation label for your tab.</span></span>|
|<span data-ttu-id="21fcb-161">2</span><span class="sxs-lookup"><span data-stu-id="21fcb-161">2</span></span>|<span data-ttu-id="21fcb-162">**Registerkartenüberlauf**: Öffnet Registerkartenaktionen, z. B. Umbenennen und Entfernen.</span><span class="sxs-lookup"><span data-stu-id="21fcb-162">**Tab overflow**: Opens tab actions, such as rename and remove.</span></span>|
|<span data-ttu-id="21fcb-163">3</span><span class="sxs-lookup"><span data-stu-id="21fcb-163">3</span></span>|<span data-ttu-id="21fcb-164">**Tab-Chat:** Öffnet rechts einen Chatthread, sodass Benutzer neben dem Inhalt eine Unterhaltung führen können.</span><span class="sxs-lookup"><span data-stu-id="21fcb-164">**Tab chat**: Opens a chat thread on the right, allowing users to have a conversation next to the content.</span></span>|
|<span data-ttu-id="21fcb-165">4 </span><span class="sxs-lookup"><span data-stu-id="21fcb-165">4</span></span>|<span data-ttu-id="21fcb-166">**iframe**: Zeigt den Inhalt Ihrer Registerkarte an.</span><span class="sxs-lookup"><span data-stu-id="21fcb-166">**iframe**: Displays your tab’s content.</span></span>

### <a name="designing-a-tab-with-ui-templates"></a><span data-ttu-id="21fcb-167">Entwerfen einer Registerkarte mit Benutzeroberflächenvorlagen</span><span class="sxs-lookup"><span data-stu-id="21fcb-167">Designing a tab with UI templates</span></span>

<span data-ttu-id="21fcb-168">Verwenden Sie eine der folgenden Teams-UI-Vorlagen, um die Registerkartenoberfläche zu entwerfen:</span><span class="sxs-lookup"><span data-stu-id="21fcb-168">Use one of the following Teams UI templates to help design your tab experience:</span></span>

* <span data-ttu-id="21fcb-169">[Liste](../../concepts/design/design-teams-app-ui-templates.md#list): Listen können verwandte Elemente in einem scannierbaren Format anzeigen und Benutzern das Ausführen von Aktionen für eine gesamte Liste oder einzelne Elemente ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="21fcb-169">[List](../../concepts/design/design-teams-app-ui-templates.md#list): Lists can display related items in a scannable format and allow users to take actions on an entire list or individual items.</span></span>
* <span data-ttu-id="21fcb-170">[Task board:](../../concepts/design/design-teams-app-ui-templates.md#task-board)Ein Task Board, manchmal auch als Kanbanboard oder Schwimmstreifen bezeichnet, ist eine Sammlung von Karten, die häufig zum Nachverfolgen des Status von Arbeitselementen oder Tickets verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="21fcb-170">[Task board](../../concepts/design/design-teams-app-ui-templates.md#task-board): A task board, sometimes called a kanban board or swim lanes, is a collection of cards often used to track the status of work items or tickets.</span></span>
* <span data-ttu-id="21fcb-171">[Dashboard:](../../concepts/design/design-teams-app-ui-templates.md#dashboard)Ein Dashboard ist ein Canvas mit mehreren Karten, die eine Übersicht über Daten oder Inhalte bieten.</span><span class="sxs-lookup"><span data-stu-id="21fcb-171">[Dashboard](../../concepts/design/design-teams-app-ui-templates.md#dashboard): A dashboard is a canvas containing multiple cards that provide an overview of data or content.</span></span>
* <span data-ttu-id="21fcb-172">[Formular](../../concepts/design/design-teams-app-ui-templates.md#form): Formulare sind für die strukturierte Erfassung, Validierung und Übermittlung von Benutzereingaben.</span><span class="sxs-lookup"><span data-stu-id="21fcb-172">[Form](../../concepts/design/design-teams-app-ui-templates.md#form): Forms are for collecting, validating, and submitting user input in a structured way.</span></span>
* <span data-ttu-id="21fcb-173">[Leerer](../../concepts/design/design-teams-app-ui-templates.md#empty-state)Zustand: Die Vorlage für den leeren Zustand kann für viele Szenarien verwendet werden, z. B. für die Anmeldung, die Erstlauferfahrung, Fehlermeldungen und vieles mehr.</span><span class="sxs-lookup"><span data-stu-id="21fcb-173">[Empty state](../../concepts/design/design-teams-app-ui-templates.md#empty-state): The empty state template can be used for many scenarios, including sign in, first-run experiences, error messages, and more.</span></span>
* <span data-ttu-id="21fcb-174">[Linkes](../../concepts/design/design-teams-app-ui-templates.md#left-nav)Navigationsmenü: Die linke Navigationsvorlage kann hilfreich sein, wenn Ihre Registerkarte eine Navigation erfordert.</span><span class="sxs-lookup"><span data-stu-id="21fcb-174">[Left nav](../../concepts/design/design-teams-app-ui-templates.md#left-nav): The left nav template can help if your tab requires some navigation.</span></span> <span data-ttu-id="21fcb-175">Im Allgemeinen sollten Sie die Registerkartennavigation auf ein Minimum beschränken.</span><span class="sxs-lookup"><span data-stu-id="21fcb-175">In general, you should keep tab navigation to a minimum.</span></span>

## <a name="use-a-tab-to-collaborate"></a><span data-ttu-id="21fcb-176">Verwenden einer Registerkarte für die Zusammenarbeit</span><span class="sxs-lookup"><span data-stu-id="21fcb-176">Use a tab to collaborate</span></span>

<span data-ttu-id="21fcb-177">Registerkarten erleichtern Unterhaltungen über Inhalte an einem zentralen Ort.</span><span class="sxs-lookup"><span data-stu-id="21fcb-177">Tabs help facilitate conversations about content in a central location.</span></span>

### <a name="thread-discussion"></a><span data-ttu-id="21fcb-178">Threaddiskussion</span><span class="sxs-lookup"><span data-stu-id="21fcb-178">Thread discussion</span></span>

<span data-ttu-id="21fcb-179">Benutzer können automatisch in einem Kanal oder Chat posten, nachdem sie eine neue Registerkarte hinzugefügt haben. Dies benachrichtigt nicht nur Teammitglieder über den neuen Inhalt und stellt einen Link zur Registerkarte zur Seite, sondern ermöglicht es Benutzern, über die Registerkarte zu sprechen.</span><span class="sxs-lookup"><span data-stu-id="21fcb-179">Users can automatically post to a channel or chat once they’ve added a new tab. This not only notifies team members of the new content and provides a link to tab, it allows people to start talking about the tab.</span></span>

:::image type="content" source="../../assets/images/tabs/design-use-tab-channel.png" alt-text="Beispiel zeigt eine Registerkarte, die in einem Kanalthread behandelt wird." border="false":::

### <a name="side-by-side-discussion"></a><span data-ttu-id="21fcb-181">Side-by-Side-Diskussion</span><span class="sxs-lookup"><span data-stu-id="21fcb-181">Side-by-side discussion</span></span>

<span data-ttu-id="21fcb-182">Benutzer können als Nächstes eine Unterhaltung führen, während sie den Inhalt der Registerkarte anzeigen.</span><span class="sxs-lookup"><span data-stu-id="21fcb-182">Users can have a conversation next while viewing the tab’s content.</span></span>

:::image type="content" source="../../assets/images/tabs/design-use-tab-side-chat.png" alt-text="Beispiel zeigt eine Registerkarte mit einem auf der rechten Seite geöffneten Chat." border="false":::

### <a name="permissions-and-role-based-views"></a><span data-ttu-id="21fcb-184">Berechtigungen und rollenbasierte Ansichten</span><span class="sxs-lookup"><span data-stu-id="21fcb-184">Permissions and role-based views</span></span>

<span data-ttu-id="21fcb-185">Die Registerkartenerfahrung kann für Benutzer je nach ihren Berechtigungen unterschiedlich sein.</span><span class="sxs-lookup"><span data-stu-id="21fcb-185">The tab experience may be different for users depending on their permissions.</span></span> <span data-ttu-id="21fcb-186">Beispielsweise kann ein Benutzer auf die Registerkarte zugreifen, ohne sich anmelden zu müssen.</span><span class="sxs-lookup"><span data-stu-id="21fcb-186">For example, one user can access the tab without having to sign in.</span></span> <span data-ttu-id="21fcb-187">Ein anderer Benutzer muss sich jedoch signieren und sieht leicht andere Inhalte.</span><span class="sxs-lookup"><span data-stu-id="21fcb-187">Another user, however, must sign and will see slightly different content.</span></span>

## <a name="manage-a-tab"></a><span data-ttu-id="21fcb-188">Verwalten einer Registerkarte</span><span class="sxs-lookup"><span data-stu-id="21fcb-188">Manage a tab</span></span>

<span data-ttu-id="21fcb-189">Sie können Optionen zum Umbenennen, Entfernen oder Ändern einer Registerkarte hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="21fcb-189">You can include options to rename, remove, or modify a tab.</span></span>

### <a name="anatomy-tab-menu"></a><span data-ttu-id="21fcb-190">Anatomie: Registerkartenmenü</span><span class="sxs-lookup"><span data-stu-id="21fcb-190">Anatomy: Tab menu</span></span>

:::image type="content" source="../../assets/images/tabs/design-manage-tab-menu-anatomy.png" alt-text="Abbildung der Ui-Anatomie eines Registerkartenmenüs." border="false":::

|<span data-ttu-id="21fcb-192">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="21fcb-192">Counter</span></span>|<span data-ttu-id="21fcb-193">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="21fcb-193">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="21fcb-194">1</span><span class="sxs-lookup"><span data-stu-id="21fcb-194">1</span></span>|<span data-ttu-id="21fcb-195">**Einstellungen**: (Optional) Ermöglicht Benutzern das Ändern der Einstellungen einer Registerkarte nach dem Hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="21fcb-195">**Settings**: (Optional) Allows users to modify a tab’s settings after it’s been added.</span></span>|
|<span data-ttu-id="21fcb-196">2</span><span class="sxs-lookup"><span data-stu-id="21fcb-196">2</span></span>|<span data-ttu-id="21fcb-197">**Rename**: Ermöglicht Benutzern, der Registerkarte einen Namen zu geben, der für das Team aussagekräftiger ist.</span><span class="sxs-lookup"><span data-stu-id="21fcb-197">**Rename**: Allows users to give the tab a name that’s more meaningful to the team.</span></span>|
|<span data-ttu-id="21fcb-198">3</span><span class="sxs-lookup"><span data-stu-id="21fcb-198">3</span></span>|<span data-ttu-id="21fcb-199">**Remove**: Entfernt die Registerkarte aus dem Kanal, Chat oder besprechung.</span><span class="sxs-lookup"><span data-stu-id="21fcb-199">**Remove**: Removes the tab from the channel, chat, or meeting.</span></span>|

## <a name="tab-notifications-and-deep-linking"></a><span data-ttu-id="21fcb-200">Registerkartenbenachrichtigungen und tiefe Verknüpfungen</span><span class="sxs-lookup"><span data-stu-id="21fcb-200">Tab notifications and deep linking</span></span>

<span data-ttu-id="21fcb-201">Sie können eine Nachricht mit einem tiefen Link zu Ihrer Registerkarte senden. Beispielsweise zeigt eine Karte eine Zusammenfassung der Fehlerdaten an, die ein Benutzer auswählen kann, um den gesamten Fehler auf einer Registerkarte zu sehen. Das Senden von Nachrichten zu Registerkartenaktivitäten erhöht das Bewusstsein, ohne dass alle Benutzer (d. h. Aktivitäten ohne Geräusche) explizit benachrichtigt werden.</span><span class="sxs-lookup"><span data-stu-id="21fcb-201">You can send a message with a deep link to your tab. For example, a card shows a summary of bug data a user can select to see the entire bug in a tab. Sending messages about tab activity increases awareness without explicitly notifying everyone (i.e., activity without noise).</span></span> <span data-ttu-id="21fcb-202">Sie können auch @mention benutzer bei Bedarf.</span><span class="sxs-lookup"><span data-stu-id="21fcb-202">You also can @mention specific users if needed.</span></span>

<span data-ttu-id="21fcb-203">Benachrichtigen Sie Die Benutzer über die Registerkartenaktivität auf eine der folgenden Weisen:</span><span class="sxs-lookup"><span data-stu-id="21fcb-203">Notify users of tab activity one of the following ways:</span></span>

* <span data-ttu-id="21fcb-204">**Bot**: Diese Methode wird vor allem dann bevorzugt, wenn der Registerkartenthread gezielt ist.</span><span class="sxs-lookup"><span data-stu-id="21fcb-204">**Bot**: This method is preferred especially if the tab thread is targeted.</span></span> <span data-ttu-id="21fcb-205">Die Thread-Unterhaltung der Registerkarte wird als zuletzt aktiv angezeigt.</span><span class="sxs-lookup"><span data-stu-id="21fcb-205">The tab’s threaded conversation is moved into view as recently active.</span></span> <span data-ttu-id="21fcb-206">Diese Methode ermöglicht auch eine gewisse Raffinesse in der Art und Weise, wie die Benachrichtigung gesendet wird.</span><span class="sxs-lookup"><span data-stu-id="21fcb-206">This method also allows for some sophistication in how the notification is sent.</span></span>
* <span data-ttu-id="21fcb-207">**Nachricht**: Eine Nachricht wird im Aktivitätsfeed des Benutzers mit einem tiefen [Link zur Registerkarte angezeigt.](../../concepts/build-and-test/deep-links.md?view=msteams-client-js-latest&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="21fcb-207">**Message**: A message shows up in the user’s activity feed with a [deep link to the tab](../../concepts/build-and-test/deep-links.md?view=msteams-client-js-latest&preserve-view=true).</span></span>

## <a name="best-practices"></a><span data-ttu-id="21fcb-208">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="21fcb-208">Best practices</span></span>

### <a name="collaboration"></a><span data-ttu-id="21fcb-209">Zusammenarbeit</span><span class="sxs-lookup"><span data-stu-id="21fcb-209">Collaboration</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-collaboration-do.png" alt-text="Abbildung zeigt, was mit dem Registerkartennavigationsdesign zu tun ist." border="false":::

#### <a name="do-facilitate-conversation"></a><span data-ttu-id="21fcb-211">Do: Unterhaltung erleichtern</span><span class="sxs-lookup"><span data-stu-id="21fcb-211">Do: Facilitate conversation</span></span>

<span data-ttu-id="21fcb-212">Fügen Sie Inhalte und Komponenten ein, über die Personen sprechen können.</span><span class="sxs-lookup"><span data-stu-id="21fcb-212">Include content and components people can talk about.</span></span> <span data-ttu-id="21fcb-213">Wenn sie nicht in den Kontext eines Chats, Kanals oder einer Besprechung passt, gehört sie nicht zu Ihrer Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="21fcb-213">If it doesn’t fit within the context of a chat, channel, or meeting, it doesn’t belong in your tab.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-collaboration-dont.png" alt-text="Beispiel zeigt, was nicht mit dem Design der Registerkartennavigation zu tun ist." border="false":::

#### <a name="dont-treat-your-tab-like-any-other-webpage"></a><span data-ttu-id="21fcb-215">Don't: Behandeln Ihrer Registerkarte wie jede andere Webseite</span><span class="sxs-lookup"><span data-stu-id="21fcb-215">Don't: Treat your tab like any other webpage</span></span>

<span data-ttu-id="21fcb-216">Eine Registerkarte ist keine Webseite, die jemand einmal anzeigen kann.</span><span class="sxs-lookup"><span data-stu-id="21fcb-216">A tab isn’t a webpage someone might view once.</span></span> <span data-ttu-id="21fcb-217">Auf einer Registerkarte sollten Ihre wichtigsten, relevanten Inhalte angezeigt werden, die die Personen benötigen, um gemeinsam etwas zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="21fcb-217">A tab should display your most important, relevant content that people need to accomplish something together.</span></span>

   :::column-end:::
:::row-end:::

### <a name="navigation"></a><span data-ttu-id="21fcb-218">Navigation</span><span class="sxs-lookup"><span data-stu-id="21fcb-218">Navigation</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-nav-do.png" alt-text="Beispiel, in dem gezeigt wird, was mit dem Registerkartennavigationsdesign zu tun ist." border="false":::

#### <a name="do-limit-tasks-and-data"></a><span data-ttu-id="21fcb-220">Do: Einschränken von Aufgaben und Daten</span><span class="sxs-lookup"><span data-stu-id="21fcb-220">Do: Limit tasks and data</span></span>

<span data-ttu-id="21fcb-221">Registerkarten funktionieren am besten, wenn sie bestimmte Anforderungen erfüllen.</span><span class="sxs-lookup"><span data-stu-id="21fcb-221">Tabs work best when they address specific needs.</span></span> <span data-ttu-id="21fcb-222">Schließen Sie eine begrenzte Anzahl von Aufgaben und Daten ein, die für das Team oder die Gruppe relevant sind.</span><span class="sxs-lookup"><span data-stu-id="21fcb-222">Include a limited set of tasks and data relevant to the team or group.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-nav-dont.png" alt-text="Abbildung, die zeigt, was nicht mit dem Design der Registerkartennavigation zu tun ist." border="false":::

#### <a name="dont-embed-your-entire-app"></a><span data-ttu-id="21fcb-224">Don't: Embed your entire app</span><span class="sxs-lookup"><span data-stu-id="21fcb-224">Don't: Embed your entire app</span></span>

<span data-ttu-id="21fcb-225">Die Verwendung einer Registerkarte zum Anzeigen einer gesamten App mit mehrstufiger Navigation und komplexen Interaktionen führt zu Einer Informationsüberlastung.</span><span class="sxs-lookup"><span data-stu-id="21fcb-225">Using a tab to display an entire app with multi-level navigation and complex interactions leads to information overload.</span></span>

   :::column-end:::
:::row-end:::

### <a name="setup"></a><span data-ttu-id="21fcb-226">Setup</span><span class="sxs-lookup"><span data-stu-id="21fcb-226">Setup</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-setup-do.png" alt-text="Abbildung, die zeigt, was mit dem Design der Registerkarteneinrichtung zu tun ist." border="false":::

#### <a name="do-keep-it-simple"></a><span data-ttu-id="21fcb-228">Do: Keep it simple</span><span class="sxs-lookup"><span data-stu-id="21fcb-228">Do: Keep it simple</span></span>

<span data-ttu-id="21fcb-229">Wenn Ihre App eine Authentifizierung erfordert, versuchen Sie, Microsoft single sign-on (SSO) zu integrieren, um eine nahtlose Anmeldung zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="21fcb-229">If your app requires authentication, try integrating Microsoft single sign-on (SSO) for a more seamless sign-in experience.</span></span> <span data-ttu-id="21fcb-230">Fügen Sie außerdem nur wichtige Informationen und Schritte zum Hinzufügen der Registerkarte hinzu.</span><span class="sxs-lookup"><span data-stu-id="21fcb-230">Also, only include essential information and steps to add the tab.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-setup-dont.png" alt-text="Abbildung, die zeigt, was nicht mit dem Design der Registerkarteneinrichtung zu tun ist." border="false":::

#### <a name="dont-have-too-many-steps"></a><span data-ttu-id="21fcb-232">Don't: Have too many steps</span><span class="sxs-lookup"><span data-stu-id="21fcb-232">Don't: Have too many steps</span></span>

<span data-ttu-id="21fcb-233">Entfernen Sie alle unnötigen Schritte zum Hinzufügen einer Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="21fcb-233">Remove any unnecessary steps for adding a tab.</span></span>

   :::column-end:::
:::row-end:::

### <a name="theming"></a><span data-ttu-id="21fcb-234">Designs</span><span class="sxs-lookup"><span data-stu-id="21fcb-234">Theming</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-theming-do.png" alt-text="Abbildung, die zeigt, was mit dem Registerkarten-Theming zu tun ist." border="false":::

#### <a name="do-take-advantage-of-teams-color-tokens"></a><span data-ttu-id="21fcb-236">Do: Nutzen von Teams-Farbtoken</span><span class="sxs-lookup"><span data-stu-id="21fcb-236">Do: Take advantage of Teams color tokens</span></span>

<span data-ttu-id="21fcb-237">Jedes Teams-Design verfügt über ein eigenes Farbschema.</span><span class="sxs-lookup"><span data-stu-id="21fcb-237">Each Teams theme has its own color scheme.</span></span> <span data-ttu-id="21fcb-238">Verwenden Sie Farbtoken <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">(Fluent UI)</a> in Ihrem Entwurf, um Designänderungen automatisch zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="21fcb-238">To handle theme changes automatically, use <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">color tokens (Fluent UI)</a> in your design.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-theming-dont.png" alt-text="Abbildung, die zeigt, was nicht mit Registerkarten-Theming zu tun ist." border="false":::

#### <a name="dont-hard-code-color-values"></a><span data-ttu-id="21fcb-240">Don't: Hartcodefarbwerte</span><span class="sxs-lookup"><span data-stu-id="21fcb-240">Don't: Hard code color values</span></span>

<span data-ttu-id="21fcb-241">Wenn Sie keine Teams-Farbtoken verwenden, sind Ihre Designs weniger skalierbar und brauchen mehr Zeit für die Verwaltung.</span><span class="sxs-lookup"><span data-stu-id="21fcb-241">If you don’t use Teams color tokens, your designs will be less scalable and take more time to manage.</span></span>

   :::column-end:::
:::row-end:::

## <a name="validate-your-design"></a><span data-ttu-id="21fcb-242">Validieren Ihres Designs</span><span class="sxs-lookup"><span data-stu-id="21fcb-242">Validate your design</span></span>

<span data-ttu-id="21fcb-243">Wenn Sie Ihre App in AppSource veröffentlichen möchten, sollten Sie die Entwurfsprobleme verstehen, die häufig dazu führen, dass Apps während der Übermittlung fehlschlagen.</span><span class="sxs-lookup"><span data-stu-id="21fcb-243">If you plan to publish your app to AppSource, you should understand the design issues that commonly cause apps to fail during submission.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="21fcb-244">Überprüfen der Richtlinien zur Designvalidierung</span><span class="sxs-lookup"><span data-stu-id="21fcb-244">Check design validation guidelines</span></span>](../../concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#validation-guidelines--most-failed-test-cases)
