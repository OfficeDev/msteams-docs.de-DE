---
title: Entwerfen der Registerkarte für Desktop und Webdienste
description: Hier erfahren Sie, wie Sie eine Registerkarte "Teams" (Desktop und Internet) entwerfen und das Microsoft Teams UI Kit abrufen.
author: heath-hamilton
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 692a21c78dc86cbca5bf248e55d0332bd71c6b92
ms.sourcegitcommit: c102da958759c13aa9e0f81bde1cffb34a8bef34
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "49604671"
---
# <a name="designing-your-tab-for-microsoft-teams-desktop-and-web"></a><span data-ttu-id="73798-103">Entwerfen der Registerkarte für Microsoft Teams Desktop und Internet</span><span class="sxs-lookup"><span data-stu-id="73798-103">Designing your tab for Microsoft Teams desktop and web</span></span>

<span data-ttu-id="73798-104">Eine Registerkarte ist eine große Leinwand für Inhalte, die die Zusammenarbeit erleichtert.</span><span class="sxs-lookup"><span data-stu-id="73798-104">A tab is a large canvas for content that facilitates collaboration.</span></span> <span data-ttu-id="73798-105">Um Ihr App-Design zu führen, werden in den folgenden Informationen beschrieben und veranschaulicht, wie Benutzer Registerkarten in Microsoft Teams hinzufügen, verwenden und verwalten können.</span><span class="sxs-lookup"><span data-stu-id="73798-105">To guide your app design, the following information describes and illustrates how people can add, use, and manage tabs in Teams.</span></span>

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="73798-106">Microsoft Teams-UI-Kit</span><span class="sxs-lookup"><span data-stu-id="73798-106">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="73798-107">Umfassende Registerkarten-Entwurfsrichtlinien, einschließlich der Elemente, die Sie nach Bedarf abrufen und ändern können, finden Sie im Microsoft Teams UI Kit.</span><span class="sxs-lookup"><span data-stu-id="73798-107">You can find comprehensive tab design guidelines, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span> <span data-ttu-id="73798-108">Das UI Kit enthält auch wichtige Themen wie Barrierefreiheit und Anpassungsfähigkeit, die hier nicht behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="73798-108">The UI kit also has essential topics such as accessibility and responsive sizing that aren't covered here.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="73798-109">Abrufen des Microsoft Teams UI Kit (Figma)</span><span class="sxs-lookup"><span data-stu-id="73798-109">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-tab"></a><span data-ttu-id="73798-110">Registerkarte hinzufügen</span><span class="sxs-lookup"><span data-stu-id="73798-110">Add a tab</span></span>

<span data-ttu-id="73798-111">Sie können eine Registerkarte aus dem Microsoft Teams Store (AppSource) oder einen der folgenden Kontexte hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="73798-111">You can add a tab from the Teams store (AppSource) or in one of the following contexts:</span></span>

* <span data-ttu-id="73798-112">Chat</span><span class="sxs-lookup"><span data-stu-id="73798-112">Chat</span></span>
* <span data-ttu-id="73798-113">Kanal</span><span class="sxs-lookup"><span data-stu-id="73798-113">Channel</span></span>
* <span data-ttu-id="73798-114">Besprechung (vor, während oder nach der Besprechung)</span><span class="sxs-lookup"><span data-stu-id="73798-114">Meeting (before, during, or after the meeting)</span></span>

<span data-ttu-id="73798-115">Im folgenden Beispiel wird gezeigt, wie eine Registerkarte in einem Kanal hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="73798-115">The following example shows how a tab is added in a channel.</span></span>

:::image type="content" source="../../assets/images/tabs/design-add-tab.png" alt-text="Beispiel zeigt eine Registerkarte, die in einem Kanal hinzugefügt wird." border="false":::

## <a name="set-up-a-tab"></a><span data-ttu-id="73798-117">Einrichten einer Registerkarte</span><span class="sxs-lookup"><span data-stu-id="73798-117">Set up a tab</span></span>

<span data-ttu-id="73798-118">Es gibt einen kurzen Einrichtungsprozess, um eine App als Kanal, Chat oder Besprechungs Registerkarte hinzuzufügen. Die Erfahrung liegt weitgehend an Ihnen.</span><span class="sxs-lookup"><span data-stu-id="73798-118">There's a short setup process to add an app as a channel, chat, or meeting tab. The experience is largely up to you.</span></span> <span data-ttu-id="73798-119">Sie können beispielsweise eine Beschreibung der Verwendung der APP und einiger optionaler Einstellungen haben.</span><span class="sxs-lookup"><span data-stu-id="73798-119">For example, you could have a description of how to use the app and some optional settings.</span></span> <span data-ttu-id="73798-120">Fügen Sie hier einen Anmelde Schritt ein, wenn Sie Benutzer authentifizieren müssen.</span><span class="sxs-lookup"><span data-stu-id="73798-120">Include a sign-in step here if you need to authenticate users.</span></span>

### <a name="tab-configuration-modal"></a><span data-ttu-id="73798-121">Modale Konfiguration der Registerkarte</span><span class="sxs-lookup"><span data-stu-id="73798-121">Tab configuration modal</span></span>

:::image type="content" source="../../assets/images/tabs/design-set-up-tab-config.png" alt-text="Beispiel zeigt eine modale Registerkartenkonfiguration." border="false":::

### <a name="anatomy-tab-configuration-modal"></a><span data-ttu-id="73798-123">Anatomie: modale Konfiguration der Registerkarte</span><span class="sxs-lookup"><span data-stu-id="73798-123">Anatomy: Tab configuration modal</span></span>

:::image type="content" source="../../assets/images/tabs/test.png" alt-text="Abbildung der Benutzeroberflächen Anatomie einer Registerkartenkonfiguration mit modaler Darstellung." border="false":::

|<span data-ttu-id="73798-125">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="73798-125">Counter</span></span>|<span data-ttu-id="73798-126">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="73798-126">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="73798-127">1</span><span class="sxs-lookup"><span data-stu-id="73798-127">1</span></span>|<span data-ttu-id="73798-128">**App-Logo**: vollfarbiges App-Logo Ihrer APP.</span><span class="sxs-lookup"><span data-stu-id="73798-128">**App logo**: Full color app logo of your app.</span></span>|
|<span data-ttu-id="73798-129">2 </span><span class="sxs-lookup"><span data-stu-id="73798-129">2</span></span>|<span data-ttu-id="73798-130">**App-Name**: vollständiger Name Ihrer APP.</span><span class="sxs-lookup"><span data-stu-id="73798-130">**App name**: Full name of your app.</span></span>|
|<span data-ttu-id="73798-131">3 </span><span class="sxs-lookup"><span data-stu-id="73798-131">3</span></span>|<span data-ttu-id="73798-132">**iframe**: reaktionsfähiger Speicherplatz für den Inhalt Ihrer APP (beispielsweise Registerkarteneinstellungen oder Authentifizierung).</span><span class="sxs-lookup"><span data-stu-id="73798-132">**iframe**: Responsive space for your app’s content (for example, tab settings or authentication).</span></span>|
|<span data-ttu-id="73798-133">4 </span><span class="sxs-lookup"><span data-stu-id="73798-133">4</span></span>|<span data-ttu-id="73798-134">**Info über Link**: öffnet ein Dialogfeld mit weiteren Informationen zur APP, beispielsweise eine vollständige Beschreibung, Berechtigungen, die für die APP erforderlich sind, sowie Links zu ihren Datenschutzrichtlinien und Nutzungsbedingungen.</span><span class="sxs-lookup"><span data-stu-id="73798-134">**About link**: Opens a dialog showing more information about the app, such as a full description, permissions required by the app, and links to your privacy policy and terms of service.</span></span>
|<span data-ttu-id="73798-135">5 </span><span class="sxs-lookup"><span data-stu-id="73798-135">5</span></span>|<span data-ttu-id="73798-136">**Schließen-Schaltfläche**: schließt den modal.</span><span class="sxs-lookup"><span data-stu-id="73798-136">**Close button**: Closes the modal.</span></span>|
|<span data-ttu-id="73798-137">6 </span><span class="sxs-lookup"><span data-stu-id="73798-137">6</span></span>|<span data-ttu-id="73798-138">**Teammitglieder Benachrichtigen Option**: das modale fragt, ob Sie einen Beitrag erstellen lassen möchten, bei dem andere wissen, dass Sie eine Registerkarte hinzugefügt haben.</span><span class="sxs-lookup"><span data-stu-id="73798-138">**Notify team members option**: The modal asks if you want to create a post letting others know you added a tab.</span></span>|
|<span data-ttu-id="73798-139">7 </span><span class="sxs-lookup"><span data-stu-id="73798-139">7</span></span>|<span data-ttu-id="73798-140">**Zurück-Schaltfläche**: wechselt zum vorherigen Schritt basierend auf der Stelle, an der das Dialogfeld geöffnet wurde.</span><span class="sxs-lookup"><span data-stu-id="73798-140">**Back button**: Goes to the previous step based on where the dialog opened.</span></span>|
|<span data-ttu-id="73798-141">8 </span><span class="sxs-lookup"><span data-stu-id="73798-141">8</span></span>|<span data-ttu-id="73798-142">**Schaltfläche Speichern**: schließt das Registerkarten Setup ab.</span><span class="sxs-lookup"><span data-stu-id="73798-142">**Save button**: Completes tab setup.</span></span>|

### <a name="tab-authentication-with-single-sign-on"></a><span data-ttu-id="73798-143">Tab-Authentifizierung mit einmaligem Anmelden</span><span class="sxs-lookup"><span data-stu-id="73798-143">Tab authentication with single sign-on</span></span>

<span data-ttu-id="73798-144">Sie können einen Schritt hinzufügen, in dem sich Benutzer zunächst mit Ihren Microsoft-Anmeldeinformationen anmelden müssen.</span><span class="sxs-lookup"><span data-stu-id="73798-144">You can add a step in which users must first sign in with their Microsoft credentials.</span></span> <span data-ttu-id="73798-145">Diese Authentifizierungsmethode wird als einmaliges Anmelden (Single Sign-on, SSO) bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="73798-145">This authentication method is called single sign-on (SSO).</span></span>

:::image type="content" source="../../assets/images/tabs/design-set-up-tab-auth.png" alt-text="Beispiel zeigt einen Bildschirm für die Registerkarten Authentifizierung." border="false":::

### <a name="designing-a-tab-setup-with-ui-templates"></a><span data-ttu-id="73798-147">Entwerfen eines Registerkarten-Setups mit Benutzeroberflächenvorlagen</span><span class="sxs-lookup"><span data-stu-id="73798-147">Designing a tab setup with UI templates</span></span>

<span data-ttu-id="73798-148">Verwenden Sie eine der folgenden Microsoft Teams-Benutzeroberflächenvorlagen, die Ihnen bei der Gestaltung ihrer Registerkarten Einrichtung helfen:</span><span class="sxs-lookup"><span data-stu-id="73798-148">Use one of the following Teams UI templates to help design your tab setup experience:</span></span>

* <span data-ttu-id="73798-149">[List](../../concepts/design/design-teams-app-ui-templates.md#list): Listen können verwandte Elemente in einem scannable-Format anzeigen und Benutzern das Ausführen von Aktionen für eine gesamte Liste oder einzelne Elemente gestatten.</span><span class="sxs-lookup"><span data-stu-id="73798-149">[List](../../concepts/design/design-teams-app-ui-templates.md#list): Lists can display related items in a scannable format and allow users to take actions on an entire list or individual items.</span></span>
* <span data-ttu-id="73798-150">[Formular](../../concepts/design/design-teams-app-ui-templates.md#form): Formulare dienen zum Sammeln, validieren und Übermitteln von Benutzereingaben in strukturierter Form.</span><span class="sxs-lookup"><span data-stu-id="73798-150">[Form](../../concepts/design/design-teams-app-ui-templates.md#form): Forms are for collecting, validating, and submitting user input in a structured way.</span></span>
* <span data-ttu-id="73798-151">[Leer State](../../concepts/design/design-teams-app-ui-templates.md#empty-state): die leere Statusvorlage kann für viele Szenarien verwendet werden, einschließlich Anmeldung, Erstausführung, Fehlermeldungen und mehr.</span><span class="sxs-lookup"><span data-stu-id="73798-151">[Empty state](../../concepts/design/design-teams-app-ui-templates.md#empty-state): The empty state template can be used for many scenarios, including sign in, first-run experiences, error messages, and more.</span></span>

## <a name="view-a-tab"></a><span data-ttu-id="73798-152">Anzeigen einer Registerkarte</span><span class="sxs-lookup"><span data-stu-id="73798-152">View a tab</span></span>

<span data-ttu-id="73798-153">Registerkarten bieten eine Vollbildfunktion in Microsoft Teams, in der Sie kollaborativen Inhalt anzeigen können – solche Aufgaben Bretter und Dashboards – und wichtige Informationen.</span><span class="sxs-lookup"><span data-stu-id="73798-153">Tabs provide a full-screen web experience in Teams where you can display collaborative content—such task boards and dashboards—and important information.</span></span>

:::image type="content" source="../../assets/images/tabs/design-view-tab.png" alt-text="Beispiel zeigt eine Registerkarte mit einem Task Board." border="false":::

### <a name="anatomy-tab"></a><span data-ttu-id="73798-155">Anatomie: Registerkarte</span><span class="sxs-lookup"><span data-stu-id="73798-155">Anatomy: Tab</span></span>

:::image type="content" source="../../assets/images/tabs/design-view-tab-anatomy.png" alt-text="Abbildung der Benutzeroberflächen Anatomie einer Registerkarte." border="false":::

|<span data-ttu-id="73798-157">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="73798-157">Counter</span></span>|<span data-ttu-id="73798-158">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="73798-158">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="73798-159">1</span><span class="sxs-lookup"><span data-stu-id="73798-159">1</span></span>|<span data-ttu-id="73798-160">**Tab Name**: Navigations Bezeichnung für die Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="73798-160">**Tab name**: Navigation label for your tab.</span></span>|
|<span data-ttu-id="73798-161">2 </span><span class="sxs-lookup"><span data-stu-id="73798-161">2</span></span>|<span data-ttu-id="73798-162">**Registerkarten Überlauf**: Öffnet Registerkarten Aktionen wie umbenennen und entfernen.</span><span class="sxs-lookup"><span data-stu-id="73798-162">**Tab overflow**: Opens tab actions, such as rename and remove.</span></span>|
|<span data-ttu-id="73798-163">3 </span><span class="sxs-lookup"><span data-stu-id="73798-163">3</span></span>|<span data-ttu-id="73798-164">**Tab Chat**: öffnet einen Chat-Thread auf der rechten Seite, sodass Benutzer eine Unterhaltung neben dem Inhalt haben.</span><span class="sxs-lookup"><span data-stu-id="73798-164">**Tab chat**: Opens a chat thread on the right, allowing users to have a conversation next to the content.</span></span>|
|<span data-ttu-id="73798-165">4 </span><span class="sxs-lookup"><span data-stu-id="73798-165">4</span></span>|<span data-ttu-id="73798-166">**iframe**: zeigt den Inhalt Ihrer Registerkarte an.</span><span class="sxs-lookup"><span data-stu-id="73798-166">**iframe**: Displays your tab’s content.</span></span>

### <a name="designing-a-tab-with-ui-templates"></a><span data-ttu-id="73798-167">Entwerfen einer Registerkarte mit Benutzeroberflächenvorlagen</span><span class="sxs-lookup"><span data-stu-id="73798-167">Designing a tab with UI templates</span></span>

<span data-ttu-id="73798-168">Verwenden Sie eine der folgenden Teams-Benutzeroberflächenvorlagen, um die Gestaltung ihrer Tab-Oberfläche zu unterstützen:</span><span class="sxs-lookup"><span data-stu-id="73798-168">Use one of the following Teams UI templates to help design your tab experience:</span></span>

* <span data-ttu-id="73798-169">[List](../../concepts/design/design-teams-app-ui-templates.md#list): Listen können verwandte Elemente in einem scannable-Format anzeigen und Benutzern das Ausführen von Aktionen für eine gesamte Liste oder einzelne Elemente gestatten.</span><span class="sxs-lookup"><span data-stu-id="73798-169">[List](../../concepts/design/design-teams-app-ui-templates.md#list): Lists can display related items in a scannable format and allow users to take actions on an entire list or individual items.</span></span>
* <span data-ttu-id="73798-170">[Task Board](../../concepts/design/design-teams-app-ui-templates.md#task-board): ein Aufgaben Gremium, das manchmal als Kanban-Board oder als Swim Lanes bezeichnet wird, ist eine Sammlung von Karten, die häufig zum Nachverfolgen des Status von Arbeitsaufgaben oder Tickets verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="73798-170">[Task board](../../concepts/design/design-teams-app-ui-templates.md#task-board): A task board, sometimes called a kanban board or swim lanes, is a collection of cards often used to track the status of work items or tickets.</span></span>
* <span data-ttu-id="73798-171">[Dashboard](../../concepts/design/design-teams-app-ui-templates.md#dashboard): ein Dashboard ist eine Leinwand mit mehreren Karten, die eine Übersicht über Daten oder Inhalte bieten.</span><span class="sxs-lookup"><span data-stu-id="73798-171">[Dashboard](../../concepts/design/design-teams-app-ui-templates.md#dashboard): A dashboard is a canvas containing multiple cards that provide an overview of data or content.</span></span>
* <span data-ttu-id="73798-172">[Formular](../../concepts/design/design-teams-app-ui-templates.md#form): Formulare dienen zum Sammeln, validieren und Übermitteln von Benutzereingaben in strukturierter Form.</span><span class="sxs-lookup"><span data-stu-id="73798-172">[Form](../../concepts/design/design-teams-app-ui-templates.md#form): Forms are for collecting, validating, and submitting user input in a structured way.</span></span>
* <span data-ttu-id="73798-173">[Leer State](../../concepts/design/design-teams-app-ui-templates.md#empty-state): die leere Statusvorlage kann für viele Szenarien verwendet werden, einschließlich Anmeldung, Erstausführung, Fehlermeldungen und mehr.</span><span class="sxs-lookup"><span data-stu-id="73798-173">[Empty state](../../concepts/design/design-teams-app-ui-templates.md#empty-state): The empty state template can be used for many scenarios, including sign in, first-run experiences, error messages, and more.</span></span>
* <span data-ttu-id="73798-174">[Linker NAV](../../concepts/design/design-teams-app-ui-templates.md#left-nav): die linke Navigationsvorlage kann hilfreich sein, wenn Ihre Registerkarte eine Navigation erfordert.</span><span class="sxs-lookup"><span data-stu-id="73798-174">[Left nav](../../concepts/design/design-teams-app-ui-templates.md#left-nav): The left nav template can help if your tab requires some navigation.</span></span> <span data-ttu-id="73798-175">Im Allgemeinen sollten Sie die Registerkartennavigation auf ein Minimum beschränken.</span><span class="sxs-lookup"><span data-stu-id="73798-175">In general, you should keep tab navigation to a minimum.</span></span>

## <a name="use-a-tab-to-collaborate"></a><span data-ttu-id="73798-176">Verwenden einer Registerkarte für die Zusammenarbeit</span><span class="sxs-lookup"><span data-stu-id="73798-176">Use a tab to collaborate</span></span>

<span data-ttu-id="73798-177">Mithilfe von Registerkarten können Unterhaltungen zu Inhalten an einem zentralen Ort erleichtert werden.</span><span class="sxs-lookup"><span data-stu-id="73798-177">Tabs help facilitate conversations about content in a central location.</span></span>

### <a name="thread-discussion"></a><span data-ttu-id="73798-178">Thread Diskussion</span><span class="sxs-lookup"><span data-stu-id="73798-178">Thread discussion</span></span>

<span data-ttu-id="73798-179">Benutzer können automatisch in einem Kanal oder Chat Posten, nachdem Sie eine neue Registerkarte hinzugefügt haben. Dies benachrichtigt nicht nur Teammitglieder über den neuen Inhalt und stellt einen Link zur Registerkarte zur Verfügung, damit die Benutzer über die Registerkarte sprechen können.</span><span class="sxs-lookup"><span data-stu-id="73798-179">Users can automatically post to a channel or chat once they’ve added a new tab. This not only notifies team members of the new content and provides a link to tab, it allows people to start talking about the tab.</span></span>

:::image type="content" source="../../assets/images/tabs/design-use-tab-channel.png" alt-text="Beispiel zeigt eine Registerkarte, die in einem Kanal Thread erörtert wird." border="false":::

### <a name="side-by-side-discussion"></a><span data-ttu-id="73798-181">Parallele Diskussionen</span><span class="sxs-lookup"><span data-stu-id="73798-181">Side-by-side discussion</span></span>

<span data-ttu-id="73798-182">Benutzer können beim Anzeigen des Inhalts der Registerkarte eine Unterhaltung als nächstes haben.</span><span class="sxs-lookup"><span data-stu-id="73798-182">Users can have a conversation next while viewing the tab’s content.</span></span>

:::image type="content" source="../../assets/images/tabs/design-use-tab-side-chat.png" alt-text="Beispiel zeigt eine Registerkarte mit geöffnetem Chat auf der rechten Seite." border="false":::

### <a name="permissions-and-role-based-views"></a><span data-ttu-id="73798-184">Berechtigungen und rollenbasierte Ansichten</span><span class="sxs-lookup"><span data-stu-id="73798-184">Permissions and role-based views</span></span>

<span data-ttu-id="73798-185">Die Registerkarte kann für Benutzer je nach Ihren Berechtigungen unterschiedlich sein.</span><span class="sxs-lookup"><span data-stu-id="73798-185">The tab experience may be different for users depending on their permissions.</span></span> <span data-ttu-id="73798-186">Beispielsweise kann ein Benutzer auf die Registerkarte zugreifen, ohne sich anzumelden.</span><span class="sxs-lookup"><span data-stu-id="73798-186">For example, one user can access the tab without having to sign in.</span></span> <span data-ttu-id="73798-187">Ein anderer Benutzer muss jedoch leicht unterschiedliche Inhalte unterzeichnen und sehen.</span><span class="sxs-lookup"><span data-stu-id="73798-187">Another user, however, must sign and will see slightly different content.</span></span>

## <a name="manage-a-tab"></a><span data-ttu-id="73798-188">Verwalten einer Registerkarte</span><span class="sxs-lookup"><span data-stu-id="73798-188">Manage a tab</span></span>

<span data-ttu-id="73798-189">Sie können Optionen einschließen, um eine Registerkarte umzubenennen, zu entfernen oder zu ändern.</span><span class="sxs-lookup"><span data-stu-id="73798-189">You can include options to rename, remove, or modify a tab.</span></span>

### <a name="anatomy-tab-menu"></a><span data-ttu-id="73798-190">Anatomie: Register Menü</span><span class="sxs-lookup"><span data-stu-id="73798-190">Anatomy: Tab menu</span></span>

:::image type="content" source="../../assets/images/tabs/design-manage-tab-menu-anatomy.png" alt-text="Abbildung der Benutzeroberflächen Anatomie eines Registerkarten Menüs" border="false":::

|<span data-ttu-id="73798-192">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="73798-192">Counter</span></span>|<span data-ttu-id="73798-193">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="73798-193">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="73798-194">1</span><span class="sxs-lookup"><span data-stu-id="73798-194">1</span></span>|<span data-ttu-id="73798-195">**Settings**: (optional) ermöglicht Benutzern, die Einstellungen einer Registerkarte zu ändern, nachdem Sie hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="73798-195">**Settings**: (Optional) Allows users to modify a tab’s settings after it’s been added.</span></span>|
|<span data-ttu-id="73798-196">2 </span><span class="sxs-lookup"><span data-stu-id="73798-196">2</span></span>|<span data-ttu-id="73798-197">**Umbenennen**: ermöglicht Benutzern, der Registerkarte einen Namen zu geben, der für das Team aussagekräftiger ist.</span><span class="sxs-lookup"><span data-stu-id="73798-197">**Rename**: Allows users to give the tab a name that’s more meaningful to the team.</span></span>|
|<span data-ttu-id="73798-198">3 </span><span class="sxs-lookup"><span data-stu-id="73798-198">3</span></span>|<span data-ttu-id="73798-199">**Remove**: entfernt die Registerkarte aus dem Kanal, dem Chat oder der Besprechung.</span><span class="sxs-lookup"><span data-stu-id="73798-199">**Remove**: Removes the tab from the channel, chat, or meeting.</span></span>|

## <a name="tab-notifications-and-deep-linking"></a><span data-ttu-id="73798-200">Registerkarten Benachrichtigungen und Deep Linking</span><span class="sxs-lookup"><span data-stu-id="73798-200">Tab notifications and deep linking</span></span>

<span data-ttu-id="73798-201">Sie können eine Nachricht mit einem Deep-Link an Ihre Registerkarte senden. Beispielsweise zeigt eine Karte eine Zusammenfassung der Fehlerdaten an, die ein Benutzer auswählen kann, um den gesamten Fehler auf einer Registerkarte anzuzeigen. Durch das Senden von Nachrichten zur Tab-Aktivität wird die Bekanntheit erhöht, ohne dass alle Personen explizit benachrichtigt werden (also Aktivität ohne Rauschen).</span><span class="sxs-lookup"><span data-stu-id="73798-201">You can send a message with a deep link to your tab. For example, a card shows a summary of bug data a user can select to see the entire bug in a tab. Sending messages about tab activity increases awareness without explicitly notifying everyone (i.e., activity without noise).</span></span> <span data-ttu-id="73798-202">Bei Bedarf können Sie auch bestimmte Benutzer @mention.</span><span class="sxs-lookup"><span data-stu-id="73798-202">You also can @mention specific users if needed.</span></span>

<span data-ttu-id="73798-203">Benutzer von Tab-Aktivität auf eine der folgenden Arten Benachrichtigen:</span><span class="sxs-lookup"><span data-stu-id="73798-203">Notify users of tab activity one of the following ways:</span></span>

* <span data-ttu-id="73798-204">**Bot**: Diese Methode wird vor allem bevorzugt, wenn der Tab-Thread gezielt ist.</span><span class="sxs-lookup"><span data-stu-id="73798-204">**Bot**: This method is preferred especially if the tab thread is targeted.</span></span> <span data-ttu-id="73798-205">Die threaded-Unterhaltung der Registerkarte wird als kürzlich aktiviert in die Ansicht verschoben.</span><span class="sxs-lookup"><span data-stu-id="73798-205">The tab’s threaded conversation is moved into view as recently active.</span></span> <span data-ttu-id="73798-206">Diese Methode ermöglicht auch eine gewisse Raffinesse in der Art und Weise, wie die Benachrichtigung gesendet wird.</span><span class="sxs-lookup"><span data-stu-id="73798-206">This method also allows for some sophistication in how the notification is sent.</span></span>
* <span data-ttu-id="73798-207">**Meldung**: eine Nachricht wird im Aktivitätsfeed des Benutzers mit einem [tiefen Link zur Registerkarte](../../concepts/build-and-test/deep-links.md?view=msteams-client-js-latest&preserve-view=true)angezeigt.</span><span class="sxs-lookup"><span data-stu-id="73798-207">**Message**: A message shows up in the user’s activity feed with a [deep link to the tab](../../concepts/build-and-test/deep-links.md?view=msteams-client-js-latest&preserve-view=true).</span></span>

## <a name="best-practices"></a><span data-ttu-id="73798-208">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="73798-208">Best practices</span></span>

### <a name="collaboration"></a><span data-ttu-id="73798-209">Zusammenarbeit</span><span class="sxs-lookup"><span data-stu-id="73798-209">Collaboration</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-collaboration-do.png" alt-text="Abbildung, die zeigt, was mit dem Design der Registerkartennavigation zu tun ist." border="false":::

#### <a name="do-facilitate-conversation"></a><span data-ttu-id="73798-211">Do: Unterstützung für Unterhaltungen</span><span class="sxs-lookup"><span data-stu-id="73798-211">Do: Facilitate conversation</span></span>

<span data-ttu-id="73798-212">Inhalte und Komponenten einbeziehen, über die Menschen sprechen können.</span><span class="sxs-lookup"><span data-stu-id="73798-212">Include content and components people can talk about.</span></span> <span data-ttu-id="73798-213">Wenn er nicht in den Kontext eines Chats, Kanals oder einer Besprechung passt, gehört er nicht in Ihre Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="73798-213">If it doesn’t fit within the context of a chat, channel, or meeting, it doesn’t belong in your tab.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-collaboration-dont.png" alt-text="Illustration, die zeigt, was nicht mit dem Design der Registerkartennavigation zu tun ist." border="false":::

#### <a name="dont-treat-your-tab-like-any-other-webpage"></a><span data-ttu-id="73798-215">Nicht: behandeln ihrer Registerkarte wie jede andere Webseite</span><span class="sxs-lookup"><span data-stu-id="73798-215">Don't: Treat your tab like any other webpage</span></span>

<span data-ttu-id="73798-216">Eine Registerkarte ist keine Webseite, die von jemand einmal angezeigt werden kann.</span><span class="sxs-lookup"><span data-stu-id="73798-216">A tab isn’t a webpage someone might view once.</span></span> <span data-ttu-id="73798-217">Auf einer Registerkarte sollten Ihre wichtigsten, relevanten Inhalte angezeigt werden, die die Benutzer benötigen, um gemeinsam etwas zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="73798-217">A tab should display your most important, relevant content that people need to accomplish something together.</span></span>

   :::column-end:::
:::row-end:::

### <a name="navigation"></a><span data-ttu-id="73798-218">Navigation</span><span class="sxs-lookup"><span data-stu-id="73798-218">Navigation</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-nav-do.png" alt-text="Abbildung, die zeigt, was mit dem Design der Registerkartennavigation zu tun ist." border="false":::

#### <a name="do-limit-tasks-and-data"></a><span data-ttu-id="73798-220">Do: begrenzen von Vorgängen und Daten</span><span class="sxs-lookup"><span data-stu-id="73798-220">Do: Limit tasks and data</span></span>

<span data-ttu-id="73798-221">Registerkarten funktionieren am besten, wenn Sie bestimmte Anforderungen erfüllen.</span><span class="sxs-lookup"><span data-stu-id="73798-221">Tabs work best when they address specific needs.</span></span> <span data-ttu-id="73798-222">Einschließen einer begrenzten Gruppe von Aufgaben und Daten, die für das Team oder die Gruppe relevant sind.</span><span class="sxs-lookup"><span data-stu-id="73798-222">Include a limited set of tasks and data relevant to the team or group.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-nav-dont.png" alt-text="Illustration, die zeigt, was nicht mit dem Design der Registerkartennavigation zu tun ist." border="false":::

#### <a name="dont-embed-your-entire-app"></a><span data-ttu-id="73798-224">Nicht: Einbetten der gesamten App</span><span class="sxs-lookup"><span data-stu-id="73798-224">Don't: Embed your entire app</span></span>

<span data-ttu-id="73798-225">Die Verwendung einer Registerkarte zum Anzeigen einer ganzen app mit mehrstufiger Navigation und komplexen Interaktionen führt zu Informationsüberlastung.</span><span class="sxs-lookup"><span data-stu-id="73798-225">Using a tab to display an entire app with multi-level navigation and complex interactions leads to information overload.</span></span>

   :::column-end:::
:::row-end:::

### <a name="setup"></a><span data-ttu-id="73798-226">Setup</span><span class="sxs-lookup"><span data-stu-id="73798-226">Setup</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-setup-do.png" alt-text="Abbildung, die zeigt, was mit dem Design der Registerkarten Einrichtung geschieht." border="false":::

#### <a name="do-keep-it-simple"></a><span data-ttu-id="73798-228">Do: einfache Aufbewahrung</span><span class="sxs-lookup"><span data-stu-id="73798-228">Do: Keep it simple</span></span>

<span data-ttu-id="73798-229">Wenn Ihre APP eine Authentifizierung erfordert, versuchen Sie, Microsoft Single Sign-on (SSO) zu integrieren, um eine nahtlose Anmeldung zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="73798-229">If your app requires authentication, try integrating Microsoft single sign-on (SSO) for a more seamless sign-in experience.</span></span> <span data-ttu-id="73798-230">Schließen Sie außerdem nur wichtige Informationen und Schritte zum Hinzufügen der Registerkarte ein.</span><span class="sxs-lookup"><span data-stu-id="73798-230">Also, only include essential information and steps to add the tab.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-setup-dont.png" alt-text="Abbildung zeigt, was mit dem Design der Registerkarten Einrichtung nicht getan werden kann." border="false":::

#### <a name="dont-have-too-many-steps"></a><span data-ttu-id="73798-232">Nicht: zu viele Schritte</span><span class="sxs-lookup"><span data-stu-id="73798-232">Don't: Have too many steps</span></span>

<span data-ttu-id="73798-233">Entfernen Sie alle unnötigen Schritte zum Hinzufügen einer Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="73798-233">Remove any unnecessary steps for adding a tab.</span></span>

   :::column-end:::
:::row-end:::

### <a name="theming"></a><span data-ttu-id="73798-234">Designs</span><span class="sxs-lookup"><span data-stu-id="73798-234">Theming</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-theming-do.png" alt-text="Illustration, die zeigt, was mit der Tab-Funktion zu tun ist." border="false":::

#### <a name="do-take-advantage-of-teams-color-tokens"></a><span data-ttu-id="73798-236">Do: nutzen Sie die Vorteile von Microsoft Teams-Farb Token</span><span class="sxs-lookup"><span data-stu-id="73798-236">Do: Take advantage of Teams color tokens</span></span>

<span data-ttu-id="73798-237">Jedes Microsoft Teams-Design verfügt über ein eigenes Farbschema.</span><span class="sxs-lookup"><span data-stu-id="73798-237">Each Teams theme has its own color scheme.</span></span> <span data-ttu-id="73798-238">Um Designänderungen automatisch zu behandeln, verwenden Sie <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">Farb Token (Fluent UI)</a> in Ihrem Design.</span><span class="sxs-lookup"><span data-stu-id="73798-238">To handle theme changes automatically, use <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">color tokens (Fluent UI)</a> in your design.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-theming-dont.png" alt-text="Illustration, die zeigt, was mit der Tab-Funktion nicht getan werden kann." border="false":::

#### <a name="dont-hard-code-color-values"></a><span data-ttu-id="73798-240">Nicht: Farb Werte mit festem Code</span><span class="sxs-lookup"><span data-stu-id="73798-240">Don't: Hard code color values</span></span>

<span data-ttu-id="73798-241">Wenn Sie keine Microsoft Teams-Farb Token verwenden, sind Ihre Designs weniger skalierbar und benötigen mehr Zeit zum Verwalten.</span><span class="sxs-lookup"><span data-stu-id="73798-241">If you don’t use Teams color tokens, your designs will be less scalable and take more time to manage.</span></span>

   :::column-end:::
:::row-end:::

## <a name="validate-your-design"></a><span data-ttu-id="73798-242">Überprüfen des Designs</span><span class="sxs-lookup"><span data-stu-id="73798-242">Validate your design</span></span>

<span data-ttu-id="73798-243">Wenn Sie Ihre APP in AppSource veröffentlichen möchten, sollten Sie sich mit den Entwurfsproblemen vertraut machen, die häufig dazu führen, dass apps während der Übermittlung fehlschlagen.</span><span class="sxs-lookup"><span data-stu-id="73798-243">If you plan to publish your app to AppSource, you should understand the design issues that commonly cause apps to fail during submission.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="73798-244">Überprüfen der Entwurfs Validierungsrichtlinien</span><span class="sxs-lookup"><span data-stu-id="73798-244">Check design validation guidelines</span></span>](../../concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#validation-guidelines--most-failed-test-cases)
