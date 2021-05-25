---
title: Entwerfen Ihrer Registerkarte für Desktop und Web
description: Erfahren Sie, wie Sie Teams Registerkarte (Desktop und Web) entwerfen und das Microsoft Teams UI Kit erhalten.
author: heath-hamilton
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 38eb7e400de63beb0d2840ee573bbfd16299cfbd
ms.sourcegitcommit: 4224c44d169b1a289cbf1d3353de6bc6de7c7ea8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/25/2021
ms.locfileid: "52644713"
---
# <a name="designing-your-tab-for-microsoft-teams"></a><span data-ttu-id="786f3-103">Entwerfen Ihrer Registerkarte für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="786f3-103">Designing your tab for Microsoft Teams</span></span>

<span data-ttu-id="786f3-104">Eine Registerkarte ist ein großer Canvas für Ihre App-Inhalte.</span><span class="sxs-lookup"><span data-stu-id="786f3-104">A tab is a large canvas for your app content.</span></span> <span data-ttu-id="786f3-105">Um Ihr App-Design zu leiten, wird in den folgenden Informationen beschrieben und veranschaulicht, wie Benutzer Registerkarten hinzufügen, verwenden und verwalten Teams.</span><span class="sxs-lookup"><span data-stu-id="786f3-105">To guide your app design, the following information describes and illustrates how people can add, use, and manage tabs in Teams.</span></span>

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="786f3-106">Microsoft Teams-UI-Kit</span><span class="sxs-lookup"><span data-stu-id="786f3-106">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="786f3-107">Umfassende Richtlinien für das Registerkartendesign, einschließlich Elemente, die Sie bei Bedarf packen und ändern können, finden Sie im Microsoft Teams UI Kit.</span><span class="sxs-lookup"><span data-stu-id="786f3-107">You can find comprehensive tab design guidelines, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span> <span data-ttu-id="786f3-108">Das Benutzeroberflächenkit enthält auch wichtige Themen wie Barrierefreiheit und reaktionsschnelle Größenanpassung, die hier nicht behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="786f3-108">The UI kit also has essential topics such as accessibility and responsive sizing that aren't covered here.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="786f3-109">Holen Sie sich das Microsoft Teams-UI-Kit (Figma)</span><span class="sxs-lookup"><span data-stu-id="786f3-109">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-tab"></a><span data-ttu-id="786f3-110">Registerkarte hinzufügen</span><span class="sxs-lookup"><span data-stu-id="786f3-110">Add a tab</span></span>

<span data-ttu-id="786f3-111">Sie können eine Registerkarte aus dem Teams (AppSource) oder in einem der folgenden Kontexte hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="786f3-111">You can add a tab from the Teams store (AppSource) or in one of the following contexts:</span></span>

* <span data-ttu-id="786f3-112">Chat</span><span class="sxs-lookup"><span data-stu-id="786f3-112">Chat</span></span>
* <span data-ttu-id="786f3-113">Kanal</span><span class="sxs-lookup"><span data-stu-id="786f3-113">Channel</span></span>
* <span data-ttu-id="786f3-114">Besprechung (vor, während oder nach der Besprechung)</span><span class="sxs-lookup"><span data-stu-id="786f3-114">Meeting (before, during, or after the meeting)</span></span>

# <a name="desktop"></a>[<span data-ttu-id="786f3-115">Desktop</span><span class="sxs-lookup"><span data-stu-id="786f3-115">Desktop</span></span>](#tab/desktop)

<span data-ttu-id="786f3-116">Das folgende Beispiel zeigt, wie Benutzer eine Registerkarte in einem Kanal hinzufügen können.</span><span class="sxs-lookup"><span data-stu-id="786f3-116">The following example shows how users can add a tab in a channel.</span></span>

:::image type="content" source="../../assets/images/tabs/design-add-tab.png" alt-text="Beispiel zeigt eine Registerkarte, die in einem Kanal hinzugefügt wird." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="786f3-118">Mobil</span><span class="sxs-lookup"><span data-stu-id="786f3-118">Mobile</span></span>](#tab/mobile)

<span data-ttu-id="786f3-119">Benutzer können auf Registerkarten zugreifen, indem sie die Schaltfläche **Mehr** im Kanal (Beispiel unten) oder chatten, in dem sie hinzugefügt wurden.</span><span class="sxs-lookup"><span data-stu-id="786f3-119">Users can access tabs by selecting the **More** button in the channel (example below) or chat in which they've been added.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-design-access-tab.png" alt-text="Beispiel zeigt eine mobile Registerkarte, die in einem Kanal hinzugefügt wird." border="false":::

---

## <a name="set-up-a-tab"></a><span data-ttu-id="786f3-121">Einrichten einer Registerkarte</span><span class="sxs-lookup"><span data-stu-id="786f3-121">Set up a tab</span></span>

<span data-ttu-id="786f3-122">Es gibt einen kurzen Einrichtungsprozess zum Hinzufügen einer App als Kanal, Chat oder Besprechungsregisterkarte. Die Erfahrung liegt weitgehend bei Ihnen.</span><span class="sxs-lookup"><span data-stu-id="786f3-122">There's a short setup process to add an app as a channel, chat, or meeting tab. The experience is largely up to you.</span></span> <span data-ttu-id="786f3-123">Sie könnten beispielsweise eine Beschreibung der Verwendung der App und einige optionale Einstellungen haben.</span><span class="sxs-lookup"><span data-stu-id="786f3-123">For example, you could have a description of how to use the app and some optional settings.</span></span> <span data-ttu-id="786f3-124">Schließen Sie hier einen Anmeldeschritt ein, wenn Sie Benutzer authentifizieren müssen.</span><span class="sxs-lookup"><span data-stu-id="786f3-124">Include a sign-in step here if you need to authenticate users.</span></span>

### <a name="tab-configuration-dialog"></a><span data-ttu-id="786f3-125">Dialogfeld "Registerkartenkonfiguration"</span><span class="sxs-lookup"><span data-stu-id="786f3-125">Tab configuration dialog</span></span>

:::image type="content" source="../../assets/images/tabs/design-set-up-tab-config.png" alt-text="Beispiel zeigt eine modale Registerkartenkonfiguration." border="false":::

### <a name="anatomy-tab-configuration-dialog"></a><span data-ttu-id="786f3-127">Anatomie: Dialogfeld "Registerkartenkonfiguration"</span><span class="sxs-lookup"><span data-stu-id="786f3-127">Anatomy: Tab configuration dialog</span></span>

:::image type="content" source="../../assets/images/tabs/test.png" alt-text="Abbildung der Ui-Anatomie einer modalen Registerkartenkonfiguration." border="false":::

|<span data-ttu-id="786f3-129">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="786f3-129">Counter</span></span>|<span data-ttu-id="786f3-130">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="786f3-130">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="786f3-131">1</span><span class="sxs-lookup"><span data-stu-id="786f3-131">1</span></span>|<span data-ttu-id="786f3-132">**App-Logo:** Vollfarbiges App-Logo Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="786f3-132">**App logo**: Full color app logo of your app.</span></span>|
|<span data-ttu-id="786f3-133">2</span><span class="sxs-lookup"><span data-stu-id="786f3-133">2</span></span>|<span data-ttu-id="786f3-134">**App-Name**: Vollständiger Name Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="786f3-134">**App name**: Full name of your app.</span></span>|
|<span data-ttu-id="786f3-135">3</span><span class="sxs-lookup"><span data-stu-id="786f3-135">3</span></span>|<span data-ttu-id="786f3-136">**iframe**: Responsive space for your app's content (for example, tab settings or authentication).</span><span class="sxs-lookup"><span data-stu-id="786f3-136">**iframe**: Responsive space for your app’s content (for example, tab settings or authentication).</span></span>|
|<span data-ttu-id="786f3-137">4 </span><span class="sxs-lookup"><span data-stu-id="786f3-137">4</span></span>|<span data-ttu-id="786f3-138">**Über Link**: Öffnet ein Dialogfeld, in dem weitere Informationen zur App angezeigt werden, z. B. eine vollständige Beschreibung, von der App erforderliche Berechtigungen und Links zu Ihrer Datenschutzrichtlinie und den Nutzungsbedingungen.</span><span class="sxs-lookup"><span data-stu-id="786f3-138">**About link**: Opens a dialog showing more information about the app, such as a full description, permissions required by the app, and links to your privacy policy and terms of service.</span></span>|
|<span data-ttu-id="786f3-139">5 </span><span class="sxs-lookup"><span data-stu-id="786f3-139">5</span></span>|<span data-ttu-id="786f3-140">**Schaltfläche Schließen**: Schließt das Dialogfeld.</span><span class="sxs-lookup"><span data-stu-id="786f3-140">**Close button**: Closes the dialog.</span></span>|
|<span data-ttu-id="786f3-141">6 </span><span class="sxs-lookup"><span data-stu-id="786f3-141">6</span></span>|<span data-ttu-id="786f3-142">**Option Teammitglieder benachrichtigen:** Im Dialogfeld werden Benutzer gefragt, ob sie einen Beitrag erstellen möchten, der andere darüber informiert, dass sie eine Registerkarte hinzugefügt haben.</span><span class="sxs-lookup"><span data-stu-id="786f3-142">**Notify team members option**: The dialog asks users if they want to create a post letting others know they added a tab.</span></span>|
|<span data-ttu-id="786f3-143">7 </span><span class="sxs-lookup"><span data-stu-id="786f3-143">7</span></span>|<span data-ttu-id="786f3-144">**Schaltfläche "Zurück":** Geht zum vorherigen Schritt, basierend auf dem Ort, an dem das Dialogfeld geöffnet wurde.</span><span class="sxs-lookup"><span data-stu-id="786f3-144">**Back button**: Goes to the previous step based on where the dialog opened.</span></span>|
|<span data-ttu-id="786f3-145">8 </span><span class="sxs-lookup"><span data-stu-id="786f3-145">8</span></span>|<span data-ttu-id="786f3-146">**Schaltfläche "Speichern":** Schließt die Registerkarteneinrichtung ab.</span><span class="sxs-lookup"><span data-stu-id="786f3-146">**Save button**: Completes tab setup.</span></span>|

### <a name="tab-authentication-with-single-sign-on"></a><span data-ttu-id="786f3-147">Registerkartenauthentifizierung mit einmaligem Anmelden</span><span class="sxs-lookup"><span data-stu-id="786f3-147">Tab authentication with single sign-on</span></span>

<span data-ttu-id="786f3-148">Sie können einen Schritt hinzufügen, in dem sich Benutzer zuerst mit ihren Microsoft-Anmeldeinformationen anmelden müssen.</span><span class="sxs-lookup"><span data-stu-id="786f3-148">You can add a step in which users must first sign in with their Microsoft credentials.</span></span> <span data-ttu-id="786f3-149">Diese Authentifizierungsmethode wird als einmaliges Anmelden (Single Sign-On, SSO) bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="786f3-149">This authentication method is called single sign-on (SSO).</span></span>

:::image type="content" source="../../assets/images/tabs/design-set-up-tab-auth.png" alt-text="Beispiel zeigt einen Registerkartenauthentifizierungsbildschirm." border="false":::

### <a name="designing-a-tab-setup-with-ui-templates"></a><span data-ttu-id="786f3-151">Entwerfen einer Registerkarteneinrichtung mit Benutzeroberflächenvorlagen</span><span class="sxs-lookup"><span data-stu-id="786f3-151">Designing a tab setup with UI templates</span></span>

<span data-ttu-id="786f3-152">Verwenden Sie eine der folgenden Teams- und Benutzeroberflächenvorlagen, um beim Entwerfen der Registerkarteneinrichtung zu helfen:</span><span class="sxs-lookup"><span data-stu-id="786f3-152">Use one of the following Teams UI templates to help design your tab setup experience:</span></span>

* <span data-ttu-id="786f3-153">[Liste](../../concepts/design/design-teams-app-ui-templates.md#list): Listen können verwandte Elemente in einem scannierbaren Format anzeigen und Benutzern das Ausführen von Aktionen für eine gesamte Liste oder einzelne Elemente ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="786f3-153">[List](../../concepts/design/design-teams-app-ui-templates.md#list): Lists can display related items in a scannable format and allow users to take actions on an entire list or individual items.</span></span>
* <span data-ttu-id="786f3-154">[Formular](../../concepts/design/design-teams-app-ui-templates.md#form): Formulare sind für die strukturierte Erfassung, Validierung und Übermittlung von Benutzereingaben.</span><span class="sxs-lookup"><span data-stu-id="786f3-154">[Form](../../concepts/design/design-teams-app-ui-templates.md#form): Forms are for collecting, validating, and submitting user input in a structured way.</span></span>
* <span data-ttu-id="786f3-155">[Leerer](../../concepts/design/design-teams-app-ui-templates.md#empty-state)Zustand: Die Vorlage für den leeren Zustand kann für viele Szenarien verwendet werden, z. B. für die Anmeldung, die Erstlauferfahrung, Fehlermeldungen und vieles mehr.</span><span class="sxs-lookup"><span data-stu-id="786f3-155">[Empty state](../../concepts/design/design-teams-app-ui-templates.md#empty-state): The empty state template can be used for many scenarios, including sign in, first-run experiences, error messages, and more.</span></span>

## <a name="view-a-tab"></a><span data-ttu-id="786f3-156">Anzeigen einer Registerkarte</span><span class="sxs-lookup"><span data-stu-id="786f3-156">View a tab</span></span>

<span data-ttu-id="786f3-157">Registerkarten bieten eine Vollbildweberfahrung in Teams, in der Sie gemeinsamen Inhalt ( z. B. Aufgabenboards und Dashboards ) und wichtige Informationen anzeigen können.</span><span class="sxs-lookup"><span data-stu-id="786f3-157">Tabs provide a full-screen web experience in Teams where you can display collaborative content—such task boards and dashboards—and important information.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="786f3-158">Desktop</span><span class="sxs-lookup"><span data-stu-id="786f3-158">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/tabs/design-view-tab.png" alt-text="Beispiel zeigt eine Registerkarte mit einem Aufgabenboard." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="786f3-160">Mobil</span><span class="sxs-lookup"><span data-stu-id="786f3-160">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/tabs/mobile-design-view-tab.png" alt-text="Beispiel zeigt eine mobile Registerkarte mit einem Aufgabenboard." border="false":::

---

### <a name="anatomy-tab"></a><span data-ttu-id="786f3-162">Anatomie: Registerkarte</span><span class="sxs-lookup"><span data-stu-id="786f3-162">Anatomy: Tab</span></span>

# <a name="desktop"></a>[<span data-ttu-id="786f3-163">Desktop</span><span class="sxs-lookup"><span data-stu-id="786f3-163">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/tabs/design-view-tab-anatomy.png" alt-text="Abbildung der Ui-Anatomie einer Registerkarte." border="false":::

|<span data-ttu-id="786f3-165">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="786f3-165">Counter</span></span>|<span data-ttu-id="786f3-166">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="786f3-166">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="786f3-167">1</span><span class="sxs-lookup"><span data-stu-id="786f3-167">1</span></span>|<span data-ttu-id="786f3-168">**Registerkartenname:** Navigationsbezeichnung für Ihre Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="786f3-168">**Tab name**: Navigation label for your tab.</span></span>|
|<span data-ttu-id="786f3-169">2</span><span class="sxs-lookup"><span data-stu-id="786f3-169">2</span></span>|<span data-ttu-id="786f3-170">**Registerkartenüberlauf**: Öffnet Registerkartenaktionen, z. B. Umbenennen und Entfernen.</span><span class="sxs-lookup"><span data-stu-id="786f3-170">**Tab overflow**: Opens tab actions, such as rename and remove.</span></span>|
|<span data-ttu-id="786f3-171">3</span><span class="sxs-lookup"><span data-stu-id="786f3-171">3</span></span>|<span data-ttu-id="786f3-172">**Tab-Chat:** Öffnet einen Chat auf der rechten Seite, sodass Benutzer neben dem Inhalt eine Unterhaltung führen können.</span><span class="sxs-lookup"><span data-stu-id="786f3-172">**Tab chat**: Opens a chat to the right, allowing users to have a conversation next to the content.</span></span>|
|<span data-ttu-id="786f3-173">4 </span><span class="sxs-lookup"><span data-stu-id="786f3-173">4</span></span>|<span data-ttu-id="786f3-174">**iframe**: Zeigt Ihre App-Inhalte an.</span><span class="sxs-lookup"><span data-stu-id="786f3-174">**iframe**: Displays your app content.</span></span>|

# <a name="mobile"></a>[<span data-ttu-id="786f3-175">Mobil</span><span class="sxs-lookup"><span data-stu-id="786f3-175">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/tabs/mobile-design-view-tab-anatomy.png" alt-text="Abbildung der Ui-Anatomie einer Registerkarte." border="false":::

|<span data-ttu-id="786f3-177">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="786f3-177">Counter</span></span>|<span data-ttu-id="786f3-178">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="786f3-178">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="786f3-179">1</span><span class="sxs-lookup"><span data-stu-id="786f3-179">1</span></span>|<span data-ttu-id="786f3-180">**Registerkartenname:** Navigationsbezeichnung für Ihre Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="786f3-180">**Tab name**: Navigation label for your tab.</span></span>|
|<span data-ttu-id="786f3-181">2</span><span class="sxs-lookup"><span data-stu-id="786f3-181">2</span></span>|<span data-ttu-id="786f3-182">**Tab-Chat:** Öffnet einen Chat, mit dem Benutzer neben dem Inhalt eine Unterhaltung führen können.</span><span class="sxs-lookup"><span data-stu-id="786f3-182">**Tab chat**: Opens a chat that allows users to have a conversation next to the content.</span></span>|
|<span data-ttu-id="786f3-183">3</span><span class="sxs-lookup"><span data-stu-id="786f3-183">3</span></span>|<span data-ttu-id="786f3-184">**webview**: Zeigt Ihre App-Inhalte an.</span><span class="sxs-lookup"><span data-stu-id="786f3-184">**webview**: Displays your app content.</span></span>|

---

### <a name="designing-a-tab-with-ui-templates-and-advanced-components"></a><span data-ttu-id="786f3-185">Entwerfen einer Registerkarte mit Benutzeroberflächenvorlagen und erweiterten Komponenten</span><span class="sxs-lookup"><span data-stu-id="786f3-185">Designing a tab with UI templates and advanced components</span></span>

<span data-ttu-id="786f3-186">Verwenden Sie eine der folgenden Teams Und-Komponenten, um Ihre Registerkartenerfahrung zu entwerfen:</span><span class="sxs-lookup"><span data-stu-id="786f3-186">Use one of the following Teams templates and components to help design your tab experience:</span></span>

* <span data-ttu-id="786f3-187">[Liste](../../concepts/design/design-teams-app-ui-templates.md#list): Listen können verwandte Elemente in einem scannierbaren Format anzeigen und Benutzern das Ausführen von Aktionen für eine gesamte Liste oder einzelne Elemente ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="786f3-187">[List](../../concepts/design/design-teams-app-ui-templates.md#list): Lists can display related items in a scannable format and allow users to take actions on an entire list or individual items.</span></span>
* <span data-ttu-id="786f3-188">[Task board:](../../concepts/design/design-teams-app-ui-templates.md#task-board)Ein Task Board, manchmal auch als Kanbanboard oder Schwimmstreifen bezeichnet, ist eine Sammlung von Karten, die häufig zum Nachverfolgen des Status von Arbeitselementen oder Tickets verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="786f3-188">[Task board](../../concepts/design/design-teams-app-ui-templates.md#task-board): A task board, sometimes called a kanban board or swim lanes, is a collection of cards often used to track the status of work items or tickets.</span></span>
* <span data-ttu-id="786f3-189">[Dashboard:](../../concepts/design/design-teams-app-ui-templates.md#dashboard)Ein Dashboard ist ein Canvas mit mehreren Karten, die eine Übersicht über Daten oder Inhalte bieten.</span><span class="sxs-lookup"><span data-stu-id="786f3-189">[Dashboard](../../concepts/design/design-teams-app-ui-templates.md#dashboard): A dashboard is a canvas containing multiple cards that provide an overview of data or content.</span></span>
* <span data-ttu-id="786f3-190">[Formular](../../concepts/design/design-teams-app-ui-templates.md#form): Formulare sind für die strukturierte Erfassung, Validierung und Übermittlung von Benutzereingaben.</span><span class="sxs-lookup"><span data-stu-id="786f3-190">[Form](../../concepts/design/design-teams-app-ui-templates.md#form): Forms are for collecting, validating, and submitting user input in a structured way.</span></span>
* <span data-ttu-id="786f3-191">[Leerer](../../concepts/design/design-teams-app-ui-templates.md#empty-state)Zustand: Die Vorlage für den leeren Zustand kann für viele Szenarien verwendet werden, z. B. für die Anmeldung, die Erstlauferfahrung, Fehlermeldungen und vieles mehr.</span><span class="sxs-lookup"><span data-stu-id="786f3-191">[Empty state](../../concepts/design/design-teams-app-ui-templates.md#empty-state): The empty state template can be used for many scenarios, including sign in, first-run experiences, error messages, and more.</span></span>
* <span data-ttu-id="786f3-192">[Linkes](../../concepts/design/design-teams-app-advanced-ui-components.md#left-nav)Navigationselement: Die linke Navigationskomponente kann hilfreich sein, wenn Ihre Registerkarte eine Navigation erfordert.</span><span class="sxs-lookup"><span data-stu-id="786f3-192">[Left nav](../../concepts/design/design-teams-app-advanced-ui-components.md#left-nav): The left nav component can help if your tab requires some navigation.</span></span> <span data-ttu-id="786f3-193">Im Allgemeinen sollten Sie die Registerkartennavigation auf ein Minimum beschränken.</span><span class="sxs-lookup"><span data-stu-id="786f3-193">In general, you should keep tab navigation to a minimum.</span></span>

## <a name="use-a-tab-to-collaborate"></a><span data-ttu-id="786f3-194">Verwenden einer Registerkarte für die Zusammenarbeit</span><span class="sxs-lookup"><span data-stu-id="786f3-194">Use a tab to collaborate</span></span>

<span data-ttu-id="786f3-195">Registerkarten erleichtern Unterhaltungen über Inhalte an einem zentralen Ort.</span><span class="sxs-lookup"><span data-stu-id="786f3-195">Tabs help facilitate conversations about content in a central location.</span></span>

### <a name="thread-discussion"></a><span data-ttu-id="786f3-196">Threaddiskussion</span><span class="sxs-lookup"><span data-stu-id="786f3-196">Thread discussion</span></span>

<span data-ttu-id="786f3-197">Benutzer können automatisch in einem Kanal oder Chat posten, nachdem sie eine neue Registerkarte hinzugefügt haben. Dies benachrichtigt nicht nur Teammitglieder über den neuen Inhalt und stellt einen Link zur Registerkarte zur Seite, sondern ermöglicht es Benutzern, über die Registerkarte zu sprechen.</span><span class="sxs-lookup"><span data-stu-id="786f3-197">Users can automatically post to a channel or chat once they’ve added a new tab. This not only notifies team members of the new content and provides a link to tab, it allows people to start talking about the tab.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="786f3-198">Desktop</span><span class="sxs-lookup"><span data-stu-id="786f3-198">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/tabs/design-use-tab-channel.png" alt-text="Beispiel zeigt eine Registerkarte, die in einem Kanalthread behandelt wird." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="786f3-200">Mobil</span><span class="sxs-lookup"><span data-stu-id="786f3-200">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/tabs/mobile-design-use-tab-channel.png" alt-text="Beispiel zeigt eine mobile Registerkarte, die in einem Kanalthread behandelt wird." border="false":::

---

### <a name="tab-chat"></a><span data-ttu-id="786f3-202">Registerkartenchat</span><span class="sxs-lookup"><span data-stu-id="786f3-202">Tab chat</span></span>

<span data-ttu-id="786f3-203">Benutzer können neben den angezeigten Registerkarteninhalten eine Unterhaltung führen.</span><span class="sxs-lookup"><span data-stu-id="786f3-203">Users can have a conversation next to the tab content they're viewing.</span></span> <span data-ttu-id="786f3-204">Auf dem Desktop wird der Chat an der Seite des App-Inhalts geöffnet.</span><span class="sxs-lookup"><span data-stu-id="786f3-204">On desktop, the chat opens to the side of the app content.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="786f3-205">Desktop</span><span class="sxs-lookup"><span data-stu-id="786f3-205">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/tabs/design-use-tab-side-chat.png" alt-text="Beispiel zeigt eine Registerkarte mit einem auf der rechten Seite geöffneten Chat." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="786f3-207">Mobil</span><span class="sxs-lookup"><span data-stu-id="786f3-207">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/tabs/mobile-design-use-tab-side-chat.png" alt-text="Beispiel zeigt eine mobile Registerkarte mit einem kontextbezogenen Chatbereich." border="false":::

---

### <a name="permissions-and-role-based-views"></a><span data-ttu-id="786f3-209">Berechtigungen und rollenbasierte Ansichten</span><span class="sxs-lookup"><span data-stu-id="786f3-209">Permissions and role-based views</span></span>

<span data-ttu-id="786f3-210">Die Registerkartenerfahrung kann für Benutzer je nach ihren Berechtigungen unterschiedlich sein.</span><span class="sxs-lookup"><span data-stu-id="786f3-210">The tab experience may be different for users depending on their permissions.</span></span> <span data-ttu-id="786f3-211">Beispielsweise kann ein Benutzer auf die Registerkarte zugreifen, ohne sich anmelden zu müssen.</span><span class="sxs-lookup"><span data-stu-id="786f3-211">For example, one user can access the tab without having to sign in.</span></span> <span data-ttu-id="786f3-212">Ein anderer Benutzer muss sich jedoch signieren und sieht leicht andere Inhalte.</span><span class="sxs-lookup"><span data-stu-id="786f3-212">Another user, however, must sign and will see slightly different content.</span></span>

## <a name="manage-a-tab"></a><span data-ttu-id="786f3-213">Verwalten einer Registerkarte</span><span class="sxs-lookup"><span data-stu-id="786f3-213">Manage a tab</span></span>

<span data-ttu-id="786f3-214">Sie können Optionen zum Umbenennen, Entfernen oder Ändern einer Registerkarte hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="786f3-214">You can include options to rename, remove, or modify a tab.</span></span>

### <a name="anatomy-tab-menu"></a><span data-ttu-id="786f3-215">Anatomie: Registerkartenmenü</span><span class="sxs-lookup"><span data-stu-id="786f3-215">Anatomy: Tab menu</span></span>

# <a name="desktop"></a>[<span data-ttu-id="786f3-216">Desktop</span><span class="sxs-lookup"><span data-stu-id="786f3-216">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/tabs/design-manage-tab-menu-anatomy.png" alt-text="Abbildung der Ui-Anatomie eines Registerkartenmenüs." border="false":::

|<span data-ttu-id="786f3-218">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="786f3-218">Counter</span></span>|<span data-ttu-id="786f3-219">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="786f3-219">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="786f3-220">1</span><span class="sxs-lookup"><span data-stu-id="786f3-220">1</span></span>|<span data-ttu-id="786f3-221">**Einstellungen**: (Optional) Ermöglicht Benutzern das Ändern der Einstellungen einer Registerkarte, nachdem sie hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="786f3-221">**Settings**: (Optional) Allows users to modify a tab’s settings after it’s been added.</span></span>|
|<span data-ttu-id="786f3-222">2</span><span class="sxs-lookup"><span data-stu-id="786f3-222">2</span></span>|<span data-ttu-id="786f3-223">**Umbenennen:** Benutzer können der Registerkarte einen Namen geben, der für den Kanal, den Chat oder die Besprechung von Bedeutung ist.</span><span class="sxs-lookup"><span data-stu-id="786f3-223">**Rename**: Users can give the tab a name that’s meaningful to the channel, chat, or meeting.</span></span>|
|<span data-ttu-id="786f3-224">3</span><span class="sxs-lookup"><span data-stu-id="786f3-224">3</span></span>|<span data-ttu-id="786f3-225">**Remove**: Entfernt die Registerkarte aus dem Kanal, Chat oder besprechung.</span><span class="sxs-lookup"><span data-stu-id="786f3-225">**Remove**: Removes the tab from the channel, chat, or meeting.</span></span>|

# <a name="mobile"></a>[<span data-ttu-id="786f3-226">Mobil</span><span class="sxs-lookup"><span data-stu-id="786f3-226">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/tabs/mobile-design-manage-tab-menu-anatomy.png" alt-text="Abbildung der Ui-Anatomie eines mobilen Registerkartenmenüs." border="false":::

|<span data-ttu-id="786f3-228">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="786f3-228">Counter</span></span>|<span data-ttu-id="786f3-229">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="786f3-229">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="786f3-230">1</span><span class="sxs-lookup"><span data-stu-id="786f3-230">1</span></span>|<span data-ttu-id="786f3-231">**Öffnen im Browser**: Öffnet die App im Standardbrowser des Geräts.</span><span class="sxs-lookup"><span data-stu-id="786f3-231">**Open in browser**: Opens the app in the device’s default browser.</span></span>|
|<span data-ttu-id="786f3-232">2</span><span class="sxs-lookup"><span data-stu-id="786f3-232">2</span></span>|<span data-ttu-id="786f3-233">**Link kopieren:** Benutzer können einen Link zur Registerkarte kopieren und freigeben.</span><span class="sxs-lookup"><span data-stu-id="786f3-233">**Copy link**: Users can copy and share a link to the tab.</span></span>|
|<span data-ttu-id="786f3-234">3</span><span class="sxs-lookup"><span data-stu-id="786f3-234">3</span></span>|<span data-ttu-id="786f3-235">**Einstellungen**: (Optional) Ändern Sie die Einstellungen einer Registerkarte, nachdem sie hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="786f3-235">**Settings**: (Optional) Modify a tab’s settings after it's been added.</span></span>|
|<span data-ttu-id="786f3-236">4 </span><span class="sxs-lookup"><span data-stu-id="786f3-236">4</span></span>|<span data-ttu-id="786f3-237">**Umbenennen:** Benutzer können der Registerkarte einen Namen geben, der für den Kanal, den Chat oder die Besprechung von Bedeutung ist.</span><span class="sxs-lookup"><span data-stu-id="786f3-237">**Rename**: Users can give the tab a name that's meaningful to the channel, chat, or meeting.</span></span>|
|<span data-ttu-id="786f3-238">5 </span><span class="sxs-lookup"><span data-stu-id="786f3-238">5</span></span>|<span data-ttu-id="786f3-239">**Löschen**: Entfernt die Registerkarte aus dem Kanal, Chat oder der Besprechung.</span><span class="sxs-lookup"><span data-stu-id="786f3-239">**Delete**: Removes the tab from the channel, chat, or meeting.</span></span>|

---

## <a name="tab-notifications-and-deep-linking"></a><span data-ttu-id="786f3-240">Registerkartenbenachrichtigungen und tiefe Verknüpfungen</span><span class="sxs-lookup"><span data-stu-id="786f3-240">Tab notifications and deep linking</span></span>

<span data-ttu-id="786f3-241">Sie können eine Nachricht mit einem tiefen Link zu Ihrer Registerkarte senden. Beispielsweise zeigt eine Karte eine Zusammenfassung der Fehlerdaten an, die ein Benutzer auswählen kann, um den gesamten Fehler auf einer Registerkarte zu sehen. Das Senden von Nachrichten zu Registerkartenaktivitäten erhöht das Bewusstsein, ohne dass alle Benutzer (d. h. Aktivitäten ohne Geräusche) explizit benachrichtigt werden.</span><span class="sxs-lookup"><span data-stu-id="786f3-241">You can send a message with a deep link to your tab. For example, a card shows a summary of bug data a user can select to see the entire bug in a tab. Sending messages about tab activity increases awareness without explicitly notifying everyone (i.e., activity without noise).</span></span> <span data-ttu-id="786f3-242">Sie können auch @mention benutzer bei Bedarf.</span><span class="sxs-lookup"><span data-stu-id="786f3-242">You also can @mention specific users if needed.</span></span>

<span data-ttu-id="786f3-243">Benachrichtigen Sie Die Benutzer über die Registerkartenaktivität auf eine der folgenden Weisen:</span><span class="sxs-lookup"><span data-stu-id="786f3-243">Notify users of tab activity one of the following ways:</span></span>

* <span data-ttu-id="786f3-244">**Bot**: Diese Methode wird vor allem dann bevorzugt, wenn der Registerkartenthread gezielt ist.</span><span class="sxs-lookup"><span data-stu-id="786f3-244">**Bot**: This method is preferred especially if the tab thread is targeted.</span></span> <span data-ttu-id="786f3-245">Die Thread-Unterhaltung der Registerkarte wird als zuletzt aktiv angezeigt.</span><span class="sxs-lookup"><span data-stu-id="786f3-245">The tab’s threaded conversation is moved into view as recently active.</span></span> <span data-ttu-id="786f3-246">Diese Methode ermöglicht auch eine gewisse Raffinesse in der Art und Weise, wie die Benachrichtigung gesendet wird.</span><span class="sxs-lookup"><span data-stu-id="786f3-246">This method also allows for some sophistication in how the notification is sent.</span></span>
* <span data-ttu-id="786f3-247">**Nachricht**: Eine Nachricht wird im Aktivitätsfeed des Benutzers mit einem tiefen [Link zur Registerkarte angezeigt.](../../concepts/build-and-test/deep-links.md?view=msteams-client-js-latest&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="786f3-247">**Message**: A message shows up in the user’s activity feed with a [deep link to the tab](../../concepts/build-and-test/deep-links.md?view=msteams-client-js-latest&preserve-view=true).</span></span>

## <a name="best-practices"></a><span data-ttu-id="786f3-248">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="786f3-248">Best practices</span></span>

<span data-ttu-id="786f3-249">Verwenden Sie diese Empfehlungen, um eine hochwertige App-Erfahrung zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="786f3-249">Use these recommendations to create a quality app experience:</span></span>

### <a name="collaboration"></a><span data-ttu-id="786f3-250">Zusammenarbeit</span><span class="sxs-lookup"><span data-stu-id="786f3-250">Collaboration</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-collaboration-do.png" alt-text="Abbildung zeigt, was mit dem Registerkartennavigationsdesign zu tun ist." border="false":::

#### <a name="do-facilitate-conversation"></a><span data-ttu-id="786f3-252">Do: Unterhaltung erleichtern</span><span class="sxs-lookup"><span data-stu-id="786f3-252">Do: Facilitate conversation</span></span>

<span data-ttu-id="786f3-253">Fügen Sie Inhalte und Komponenten ein, über die Personen sprechen können.</span><span class="sxs-lookup"><span data-stu-id="786f3-253">Include content and components people can talk about.</span></span> <span data-ttu-id="786f3-254">Wenn sie nicht in den Kontext eines Chats, Kanals oder einer Besprechung passt, gehört sie nicht zu Ihrer Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="786f3-254">If it doesn’t fit within the context of a chat, channel, or meeting, it doesn’t belong in your tab.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-collaboration-dont.png" alt-text="Beispiel zeigt, was nicht mit dem Design der Registerkartennavigation zu tun ist." border="false":::

#### <a name="dont-treat-your-tab-like-any-other-webpage"></a><span data-ttu-id="786f3-256">Don't: Behandeln Ihrer Registerkarte wie jede andere Webseite</span><span class="sxs-lookup"><span data-stu-id="786f3-256">Don't: Treat your tab like any other webpage</span></span>

<span data-ttu-id="786f3-257">Eine Registerkarte ist keine Webseite, die jemand einmal anzeigen kann.</span><span class="sxs-lookup"><span data-stu-id="786f3-257">A tab isn’t a webpage someone might view once.</span></span> <span data-ttu-id="786f3-258">Auf einer Registerkarte sollten Ihre wichtigsten, relevanten Inhalte angezeigt werden, die die Personen benötigen, um gemeinsam etwas zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="786f3-258">A tab should display your most important, relevant content that people need to accomplish something together.</span></span>

   :::column-end:::
:::row-end:::

### <a name="navigation"></a><span data-ttu-id="786f3-259">Navigation</span><span class="sxs-lookup"><span data-stu-id="786f3-259">Navigation</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-nav-do.png" alt-text="Beispiel, in dem gezeigt wird, was mit dem Registerkartennavigationsdesign zu tun ist." border="false":::

#### <a name="do-limit-tasks-and-data"></a><span data-ttu-id="786f3-261">Do: Einschränken von Aufgaben und Daten</span><span class="sxs-lookup"><span data-stu-id="786f3-261">Do: Limit tasks and data</span></span>

<span data-ttu-id="786f3-262">Registerkarten funktionieren am besten, wenn sie bestimmte Anforderungen erfüllen.</span><span class="sxs-lookup"><span data-stu-id="786f3-262">Tabs work best when they address specific needs.</span></span> <span data-ttu-id="786f3-263">Schließen Sie eine begrenzte Anzahl von Aufgaben und Daten ein, die für das Team oder die Gruppe relevant sind.</span><span class="sxs-lookup"><span data-stu-id="786f3-263">Include a limited set of tasks and data relevant to the team or group.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-nav-dont.png" alt-text="Abbildung, die zeigt, was nicht mit dem Design der Registerkartennavigation zu tun ist." border="false":::

#### <a name="dont-embed-your-entire-app"></a><span data-ttu-id="786f3-265">Don't: Embed your entire app</span><span class="sxs-lookup"><span data-stu-id="786f3-265">Don't: Embed your entire app</span></span>

<span data-ttu-id="786f3-266">Die Verwendung einer Registerkarte zum Anzeigen einer gesamten App mit mehrstufiger Navigation und komplexen Interaktionen führt zu Einer Informationsüberlastung.</span><span class="sxs-lookup"><span data-stu-id="786f3-266">Using a tab to display an entire app with multi-level navigation and complex interactions leads to information overload.</span></span>

   :::column-end:::
:::row-end:::

### <a name="setup"></a><span data-ttu-id="786f3-267">Setup</span><span class="sxs-lookup"><span data-stu-id="786f3-267">Setup</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-setup-do.png" alt-text="Abbildung, die zeigt, was mit dem Design der Registerkarteneinrichtung zu tun ist." border="false":::

#### <a name="do-keep-it-simple"></a><span data-ttu-id="786f3-269">Do: Keep it simple</span><span class="sxs-lookup"><span data-stu-id="786f3-269">Do: Keep it simple</span></span>

<span data-ttu-id="786f3-270">Wenn Ihre App eine Authentifizierung erfordert, versuchen Sie, Microsoft single sign-on (SSO) zu integrieren, um eine nahtlose Anmeldung zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="786f3-270">If your app requires authentication, try integrating Microsoft single sign-on (SSO) for a more seamless sign-in experience.</span></span> <span data-ttu-id="786f3-271">Fügen Sie außerdem nur wichtige Informationen und Schritte zum Hinzufügen der Registerkarte hinzu.</span><span class="sxs-lookup"><span data-stu-id="786f3-271">Also, only include essential information and steps to add the tab.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-setup-dont.png" alt-text="Abbildung, die zeigt, was nicht mit dem Design der Registerkarteneinrichtung zu tun ist." border="false":::

#### <a name="dont-have-too-many-steps"></a><span data-ttu-id="786f3-273">Don't: Have too many steps</span><span class="sxs-lookup"><span data-stu-id="786f3-273">Don't: Have too many steps</span></span>

<span data-ttu-id="786f3-274">Entfernen Sie alle unnötigen Schritte zum Hinzufügen einer Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="786f3-274">Remove any unnecessary steps for adding a tab.</span></span>

   :::column-end:::
:::row-end:::

### <a name="theming"></a><span data-ttu-id="786f3-275">Designs</span><span class="sxs-lookup"><span data-stu-id="786f3-275">Theming</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-theming-do.png" alt-text="Abbildung, die zeigt, was mit dem Registerkarten-Theming zu tun ist." border="false":::

#### <a name="do-take-advantage-of-teams-color-tokens"></a><span data-ttu-id="786f3-277">Do: Nutzen Teams Farbtoken</span><span class="sxs-lookup"><span data-stu-id="786f3-277">Do: Take advantage of Teams color tokens</span></span>

<span data-ttu-id="786f3-278">Jedes Teams design verfügt über ein eigenes Farbschema.</span><span class="sxs-lookup"><span data-stu-id="786f3-278">Each Teams theme has its own color scheme.</span></span> <span data-ttu-id="786f3-279">Verwenden Sie Farbtoken <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">(Fluent UI)</a> in Ihrem Entwurf, um Designänderungen automatisch zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="786f3-279">To handle theme changes automatically, use <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">color tokens (Fluent UI)</a> in your design.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-theming-dont.png" alt-text="Abbildung, die zeigt, was nicht mit Registerkarten-Theming zu tun ist." border="false":::

#### <a name="dont-hard-code-color-values"></a><span data-ttu-id="786f3-281">Don't: Hartcodefarbwerte</span><span class="sxs-lookup"><span data-stu-id="786f3-281">Don't: Hard code color values</span></span>

<span data-ttu-id="786f3-282">Wenn Sie keine Teams verwenden, sind Ihre Designs weniger skalierbar und nehmen sich mehr Zeit für die Verwaltung.</span><span class="sxs-lookup"><span data-stu-id="786f3-282">If you don’t use Teams color tokens, your designs will be less scalable and take more time to manage.</span></span>

   :::column-end:::
:::row-end:::
