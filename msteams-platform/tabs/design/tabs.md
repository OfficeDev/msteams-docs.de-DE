---
title: Entwerfen Ihrer Registerkarte für Desktop und Web
description: Erfahren Sie, wie Sie eine Teams Registerkarte (Desktop und Web) entwerfen und das Microsoft Teams UI Kit abrufen.
author: heath-hamilton
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: baa17cd97ff4e2cad91615dced5c4e4cf5e533c8
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566880"
---
# <a name="designing-your-tab-for-microsoft-teams-desktop-and-web"></a><span data-ttu-id="d6f0b-103">Entwerfen der Registerkarte für Microsoft Teams Desktop und Web</span><span class="sxs-lookup"><span data-stu-id="d6f0b-103">Designing your tab for Microsoft Teams desktop and web</span></span>

<span data-ttu-id="d6f0b-104">Eine Registerkarte ist ein großer Canvas für Ihre Inhalte.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-104">A tab is a large canvas for your content.</span></span> <span data-ttu-id="d6f0b-105">Die folgenden Informationen beschreiben und veranschaulichen, wie Benutzer Registerkarten in Teams hinzufügen, verwenden und verwalten können.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-105">To guide your app design, the following information describes and illustrates how people can add, use, and manage tabs in Teams.</span></span>

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="d6f0b-106">Microsoft Teams-UI-Kit</span><span class="sxs-lookup"><span data-stu-id="d6f0b-106">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="d6f0b-107">Umfassende Richtlinien für den Tab-Design, einschließlich Elemente, die Sie bei Bedarf greifen und ändern können, finden Sie im Microsoft Teams UI Kit.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-107">You can find comprehensive tab design guidelines, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span> <span data-ttu-id="d6f0b-108">Das UI-Kit enthält auch wichtige Themen wie Barrierefreiheit und reaktionsschnelle Größenanpassung, die hier nicht behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-108">The UI kit also has essential topics such as accessibility and responsive sizing that aren't covered here.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d6f0b-109">Holen Sie sich das Microsoft Teams-UI-Kit (Figma)</span><span class="sxs-lookup"><span data-stu-id="d6f0b-109">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-tab"></a><span data-ttu-id="d6f0b-110">Registerkarte hinzufügen</span><span class="sxs-lookup"><span data-stu-id="d6f0b-110">Add a tab</span></span>

<span data-ttu-id="d6f0b-111">Sie können eine Registerkarte aus dem Teams Store (AppSource) oder in einem der folgenden Kontexte hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="d6f0b-111">You can add a tab from the Teams store (AppSource) or in one of the following contexts:</span></span>

* <span data-ttu-id="d6f0b-112">Chat</span><span class="sxs-lookup"><span data-stu-id="d6f0b-112">Chat</span></span>
* <span data-ttu-id="d6f0b-113">Kanal</span><span class="sxs-lookup"><span data-stu-id="d6f0b-113">Channel</span></span>
* <span data-ttu-id="d6f0b-114">Besprechung (vor, während oder nach der Besprechung)</span><span class="sxs-lookup"><span data-stu-id="d6f0b-114">Meeting (before, during, or after the meeting)</span></span>

<span data-ttu-id="d6f0b-115">Das folgende Beispiel zeigt, wie eine Registerkarte in einem Kanal hinzugefügt wird:</span><span class="sxs-lookup"><span data-stu-id="d6f0b-115">The following example shows how a tab is added in a channel:</span></span>

:::image type="content" source="../../assets/images/tabs/design-add-tab.png" alt-text="Das Beispiel zeigt eine Registerkarte, die in einem Kanal hinzugefügt wird." border="false":::

## <a name="set-up-a-tab"></a><span data-ttu-id="d6f0b-117">Einrichten einer Registerkarte</span><span class="sxs-lookup"><span data-stu-id="d6f0b-117">Set up a tab</span></span>

<span data-ttu-id="d6f0b-118">Es gibt einen kurzen Einrichtungsprozess, um eine App als Kanal, Chat oder Besprechungsregisterkarte hinzuzufügen. Die Erfahrung liegt weitgehend bei Ihnen.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-118">There's a short setup process to add an app as a channel, chat, or meeting tab. The experience is largely up to you.</span></span> <span data-ttu-id="d6f0b-119">Sie können z. B. eine Beschreibung der Verwendung der App und einige optionale Einstellungen erhalten.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-119">For example, you could have a description of how to use the app and some optional settings.</span></span> <span data-ttu-id="d6f0b-120">Fügen Sie hier einen Anmeldeschritt ein, wenn Sie Benutzer authentifizieren müssen.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-120">Include a sign-in step here if you need to authenticate users.</span></span>

### <a name="tab-configuration-modal"></a><span data-ttu-id="d6f0b-121">Tabkonfiguration modal</span><span class="sxs-lookup"><span data-stu-id="d6f0b-121">Tab configuration modal</span></span>

:::image type="content" source="../../assets/images/tabs/design-set-up-tab-config.png" alt-text="Das Beispiel zeigt ein Modal der Registerkartenkonfiguration." border="false":::

### <a name="anatomy-tab-configuration-modal"></a><span data-ttu-id="d6f0b-123">Anatomie: Tab-Konfiguration modal</span><span class="sxs-lookup"><span data-stu-id="d6f0b-123">Anatomy: Tab configuration modal</span></span>

:::image type="content" source="../../assets/images/tabs/test.png" alt-text="Abbildung, die die UI-Anatomie eines Modals der Registerkartenkonfiguration zeigt." border="false":::

|<span data-ttu-id="d6f0b-125">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="d6f0b-125">Counter</span></span>|<span data-ttu-id="d6f0b-126">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d6f0b-126">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="d6f0b-127">1</span><span class="sxs-lookup"><span data-stu-id="d6f0b-127">1</span></span>|<span data-ttu-id="d6f0b-128">**App-Logo**: Vollfarb-App-Logo Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-128">**App logo**: Full color app logo of your app.</span></span>|
|<span data-ttu-id="d6f0b-129">2</span><span class="sxs-lookup"><span data-stu-id="d6f0b-129">2</span></span>|<span data-ttu-id="d6f0b-130">**App-Name**: Vollständiger Name Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-130">**App name**: Full name of your app.</span></span>|
|<span data-ttu-id="d6f0b-131">3</span><span class="sxs-lookup"><span data-stu-id="d6f0b-131">3</span></span>|<span data-ttu-id="d6f0b-132">**iframe**: Responsive Space für den Inhalt Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-132">**iframe**: Responsive space for your app’s content.</span></span> <span data-ttu-id="d6f0b-133">Zum Beispiel Tabstoppeinstellungen oder Authentifizierung.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-133">For example, tab settings or authentication.</span></span>|
|<span data-ttu-id="d6f0b-134">4 </span><span class="sxs-lookup"><span data-stu-id="d6f0b-134">4</span></span>|<span data-ttu-id="d6f0b-135">**Link :** Öffnet ein Dialogfeld mit weiteren Informationen zur App, z. B. eine vollständige Beschreibung, die von der App erforderlichen Berechtigungen und Links zu Ihrer Datenschutzrichtlinie und den Nutzungsbedingungen.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-135">**About link**: Opens a dialog showing more information about the app, such as a full description, permissions required by the app, and links to your privacy policy and terms of service.</span></span>
|<span data-ttu-id="d6f0b-136">5 </span><span class="sxs-lookup"><span data-stu-id="d6f0b-136">5</span></span>|<span data-ttu-id="d6f0b-137">**Schaltfläche Schließen**: Schließt das Modal.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-137">**Close button**: Closes the modal.</span></span>|
|<span data-ttu-id="d6f0b-138">6 </span><span class="sxs-lookup"><span data-stu-id="d6f0b-138">6</span></span>|<span data-ttu-id="d6f0b-139">**Option Teammitglieder benachrichtigen**: Das Modal fragt, ob Sie einen Beitrag erstellen möchten, der andere darüber informiert, dass Sie eine Registerkarte hinzugefügt haben.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-139">**Notify team members option**: The modal asks if you want to create a post letting others know you added a tab.</span></span>|
|<span data-ttu-id="d6f0b-140">7 </span><span class="sxs-lookup"><span data-stu-id="d6f0b-140">7</span></span>|<span data-ttu-id="d6f0b-141">**Zurück-Taste**: Wechselt zum vorherigen Schritt, je nach dem Ort, an dem das Dialogfeld geöffnet wurde.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-141">**Back button**: Goes to the previous step based on where the dialog opened.</span></span>|
|<span data-ttu-id="d6f0b-142">8 </span><span class="sxs-lookup"><span data-stu-id="d6f0b-142">8</span></span>|<span data-ttu-id="d6f0b-143">**Schaltfläche speichern**: Schließt tab Setup ab.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-143">**Save button**: Completes tab setup.</span></span>|

### <a name="tab-authentication-with-single-sign-on"></a><span data-ttu-id="d6f0b-144">Tab-Authentifizierung mit Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="d6f0b-144">Tab authentication with single sign-on</span></span>

<span data-ttu-id="d6f0b-145">Sie können einen Schritt hinzufügen, in dem sich Benutzer zuerst mit ihren Microsoft-Anmeldeinformationen anmelden müssen.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-145">You can add a step in which users must first sign in with their Microsoft credentials.</span></span> <span data-ttu-id="d6f0b-146">Diese Authentifizierungsmethode wird als Single Sign-On (SSO) bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-146">This authentication method is called single sign-on (SSO).</span></span>

:::image type="content" source="../../assets/images/tabs/design-set-up-tab-auth.png" alt-text="Das Beispiel zeigt einen Registerkartenauthentifizierungsbildschirm." border="false":::

### <a name="designing-a-tab-setup-with-ui-templates"></a><span data-ttu-id="d6f0b-148">Entwerfen eines Tabstopp-Setups mit UI-Vorlagen</span><span class="sxs-lookup"><span data-stu-id="d6f0b-148">Designing a tab setup with UI templates</span></span>

<span data-ttu-id="d6f0b-149">Verwenden Sie eine der folgenden Teams UI-Vorlagen, um die Einrichtung der Registerkarte zu entwerfen:</span><span class="sxs-lookup"><span data-stu-id="d6f0b-149">Use one of the following Teams UI templates to help design your tab setup experience:</span></span>

* <span data-ttu-id="d6f0b-150">[Liste](../../concepts/design/design-teams-app-ui-templates.md#list): Listen können verwandte Elemente in einem scannbaren Format anzeigen und Benutzern ermöglichen, Aktionen für eine gesamte Liste oder einzelne Elemente auszuführen.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-150">[List](../../concepts/design/design-teams-app-ui-templates.md#list): Lists can display related items in a scannable format and allow users to take actions on an entire list or individual items.</span></span>
* <span data-ttu-id="d6f0b-151">[Formular](../../concepts/design/design-teams-app-ui-templates.md#form): Formulare sind zum Sammeln, Validieren und Übermitteln von Benutzereingaben auf strukturierte Weise.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-151">[Form](../../concepts/design/design-teams-app-ui-templates.md#form): Forms are for collecting, validating, and submitting user input in a structured way.</span></span>
* <span data-ttu-id="d6f0b-152">[Leerer Zustand](../../concepts/design/design-teams-app-ui-templates.md#empty-state): Die leere Statusvorlage kann für viele Szenarien verwendet werden, einschließlich Anmeldung, Erstausführung, Fehlermeldungen und mehr.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-152">[Empty state](../../concepts/design/design-teams-app-ui-templates.md#empty-state): The empty state template can be used for many scenarios, including sign in, first-run experiences, error messages, and more.</span></span>

## <a name="view-a-tab"></a><span data-ttu-id="d6f0b-153">Anzeigen einer Registerkarte</span><span class="sxs-lookup"><span data-stu-id="d6f0b-153">View a tab</span></span>

<span data-ttu-id="d6f0b-154">Registerkarten bieten ein umfassendes Weberlebnis in Teams in dem Sie kollaborative Inhalte – z. B. Taskboards und Dashboards – und wichtige Informationen anzeigen können.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-154">Tabs provide a full-screen web experience in Teams where you can display collaborative content—such task boards and dashboards—and important information.</span></span>

:::image type="content" source="../../assets/images/tabs/design-view-tab.png" alt-text="Das Beispiel zeigt eine Registerkarte mit einer Aufgabenplatine." border="false":::

### <a name="anatomy-tab"></a><span data-ttu-id="d6f0b-156">Anatomie: Tab</span><span class="sxs-lookup"><span data-stu-id="d6f0b-156">Anatomy: Tab</span></span>

:::image type="content" source="../../assets/images/tabs/design-view-tab-anatomy.png" alt-text="Abbildung mit der UI-Anatomie eines Tabs." border="false":::

|<span data-ttu-id="d6f0b-158">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="d6f0b-158">Counter</span></span>|<span data-ttu-id="d6f0b-159">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d6f0b-159">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="d6f0b-160">1</span><span class="sxs-lookup"><span data-stu-id="d6f0b-160">1</span></span>|<span data-ttu-id="d6f0b-161">**Tab-Name**: Navigationsbeschriftung für Ihre Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-161">**Tab name**: Navigation label for your tab.</span></span>|
|<span data-ttu-id="d6f0b-162">2</span><span class="sxs-lookup"><span data-stu-id="d6f0b-162">2</span></span>|<span data-ttu-id="d6f0b-163">**Tab-Überlauf**: Öffnet Tabstoppaktionen, z. B. Umbenennen und Entfernen.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-163">**Tab overflow**: Opens tab actions, such as rename and remove.</span></span>|
|<span data-ttu-id="d6f0b-164">3</span><span class="sxs-lookup"><span data-stu-id="d6f0b-164">3</span></span>|<span data-ttu-id="d6f0b-165">**Tab-Chat**: Öffnet einen Chat-Thread auf der rechten Seite, so dass Benutzer eine Unterhaltung neben dem Inhalt haben.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-165">**Tab chat**: Opens a chat thread on the right, allowing users to have a conversation next to the content.</span></span>|
|<span data-ttu-id="d6f0b-166">4 </span><span class="sxs-lookup"><span data-stu-id="d6f0b-166">4</span></span>|<span data-ttu-id="d6f0b-167">**iframe**: Zeigt den Inhalt Ihrer Registerkarte an.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-167">**iframe**: Displays your tab’s content.</span></span>

### <a name="designing-a-tab-with-ui-templates"></a><span data-ttu-id="d6f0b-168">Entwerfen einer Registerkarte mit UI-Vorlagen</span><span class="sxs-lookup"><span data-stu-id="d6f0b-168">Designing a tab with UI templates</span></span>

<span data-ttu-id="d6f0b-169">Verwenden Sie eine der folgenden Teams UI-Vorlagen, um die Registerkartenzugung zu entwerfen:</span><span class="sxs-lookup"><span data-stu-id="d6f0b-169">Use one of the following Teams UI templates to help design your tab experience:</span></span>

* <span data-ttu-id="d6f0b-170">[Liste](../../concepts/design/design-teams-app-ui-templates.md#list): Listen können verwandte Elemente in einem scannbaren Format anzeigen und Benutzern ermöglichen, Aktionen für eine gesamte Liste oder einzelne Elemente auszuführen.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-170">[List](../../concepts/design/design-teams-app-ui-templates.md#list): Lists can display related items in a scannable format and allow users to take actions on an entire list or individual items.</span></span>
* <span data-ttu-id="d6f0b-171">[Aufgabentafel](../../concepts/design/design-teams-app-ui-templates.md#task-board): Ein Aufgabenbrett, manchmal auch Kanban-Board oder Schwimmbahnen genannt, ist eine Sammlung von Karten, die oft verwendet werden, um den Status von Arbeitsaufgaben oder Tickets zu verfolgen.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-171">[Task board](../../concepts/design/design-teams-app-ui-templates.md#task-board): A task board, sometimes called a kanban board or swim lanes, is a collection of cards often used to track the status of work items or tickets.</span></span>
* <span data-ttu-id="d6f0b-172">[Dashboard](../../concepts/design/design-teams-app-ui-templates.md#dashboard): Ein Dashboard ist ein Canvas mit mehreren Karten, die einen Überblick über Daten oder Inhalte bieten.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-172">[Dashboard](../../concepts/design/design-teams-app-ui-templates.md#dashboard): A dashboard is a canvas containing multiple cards that provide an overview of data or content.</span></span>
* <span data-ttu-id="d6f0b-173">[Formular](../../concepts/design/design-teams-app-ui-templates.md#form): Formulare sind zum Sammeln, Validieren und Übermitteln von Benutzereingaben auf strukturierte Weise.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-173">[Form](../../concepts/design/design-teams-app-ui-templates.md#form): Forms are for collecting, validating, and submitting user input in a structured way.</span></span>
* <span data-ttu-id="d6f0b-174">[Leerer Zustand](../../concepts/design/design-teams-app-ui-templates.md#empty-state): Die leere Statusvorlage kann für viele Szenarien verwendet werden, einschließlich Anmeldung, Erstausführung, Fehlermeldungen und mehr.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-174">[Empty state](../../concepts/design/design-teams-app-ui-templates.md#empty-state): The empty state template can be used for many scenarios, including sign in, first-run experiences, error messages, and more.</span></span>
* <span data-ttu-id="d6f0b-175">[Linkes Navi](../../concepts/design/design-teams-app-ui-templates.md#left-nav): Die linke Navi-Vorlage kann helfen, wenn Ihre Registerkarte eine Gewisse Navigation erfordert.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-175">[Left nav](../../concepts/design/design-teams-app-ui-templates.md#left-nav): The left nav template can help if your tab requires some navigation.</span></span> <span data-ttu-id="d6f0b-176">Im Allgemeinen sollten Sie die Tab-Navigation auf ein Minimum beschränken.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-176">In general, you should keep tab navigation to a minimum.</span></span>

## <a name="use-a-tab-to-collaborate"></a><span data-ttu-id="d6f0b-177">Verwenden einer Registerkarte zum Zusammenarbeiten</span><span class="sxs-lookup"><span data-stu-id="d6f0b-177">Use a tab to collaborate</span></span>

<span data-ttu-id="d6f0b-178">Registerkarten erleichtern Die Unterhaltung von Inhalten an einem zentralen Ort.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-178">Tabs help facilitate conversations about content in a central location.</span></span>

### <a name="thread-discussion"></a><span data-ttu-id="d6f0b-179">Threaddiskussion</span><span class="sxs-lookup"><span data-stu-id="d6f0b-179">Thread discussion</span></span>

<span data-ttu-id="d6f0b-180">Benutzer können automatisch in einen Kanal oder Chat posten, sobald sie eine neue Registerkarte hinzugefügt haben. Dadurch werden die Teammitglieder nicht nur über den neuen Inhalt informiert und ein Link zur Registerkarte zur Verfügung stellen, sondern es ermöglicht den Personen, über die Registerkarte zu sprechen.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-180">Users can automatically post to a channel or chat once they’ve added a new tab. This not only notifies team members of the new content and provides a link to tab, it allows people to start talking about the tab.</span></span>

:::image type="content" source="../../assets/images/tabs/design-use-tab-channel.png" alt-text="Das Beispiel zeigt eine Registerkarte, die in einem Kanalthread besprochen wird." border="false":::

### <a name="side-by-side-discussion"></a><span data-ttu-id="d6f0b-182">Side-by-Side-Diskussion</span><span class="sxs-lookup"><span data-stu-id="d6f0b-182">Side-by-side discussion</span></span>

<span data-ttu-id="d6f0b-183">Benutzer können als nächstes eine Unterhaltung führen, während sie den Inhalt der Registerkarte anzeigen.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-183">Users can have a conversation next while viewing the tab’s content.</span></span>

:::image type="content" source="../../assets/images/tabs/design-use-tab-side-chat.png" alt-text="Beispiel zeigt eine Registerkarte mit einem Chat auf der rechten Seite geöffnet." border="false":::

### <a name="permissions-and-role-based-views"></a><span data-ttu-id="d6f0b-185">Berechtigungen und rollenbasierte Ansichten</span><span class="sxs-lookup"><span data-stu-id="d6f0b-185">Permissions and role-based views</span></span>

<span data-ttu-id="d6f0b-186">Die Registerkartenerfahrung kann für Benutzer je nach ihren Berechtigungen unterschiedlich sein.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-186">The tab experience may be different for users depending on their permissions.</span></span> <span data-ttu-id="d6f0b-187">Beispielsweise kann ein Benutzer auf die Registerkarte zugreifen, ohne sich anmelden zu müssen.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-187">For example, one user can access the tab without having to sign in.</span></span> <span data-ttu-id="d6f0b-188">Ein anderer Benutzer muss jedoch unterschreiben und sieht etwas andere Inhalte.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-188">Another user, however, must sign and will see slightly different content.</span></span>

## <a name="manage-a-tab"></a><span data-ttu-id="d6f0b-189">Verwalten einer Registerkarte</span><span class="sxs-lookup"><span data-stu-id="d6f0b-189">Manage a tab</span></span>

<span data-ttu-id="d6f0b-190">Sie können Optionen zum Umbenennen, Entfernen oder Ändern einer Registerkarte einschließen.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-190">You can include options to rename, remove, or modify a tab.</span></span>

### <a name="anatomy-tab-menu"></a><span data-ttu-id="d6f0b-191">Anatomie: Tab-Menü</span><span class="sxs-lookup"><span data-stu-id="d6f0b-191">Anatomy: Tab menu</span></span>

:::image type="content" source="../../assets/images/tabs/design-manage-tab-menu-anatomy.png" alt-text="Abbildung mit der UI-Anatomie eines Registerkartenmenüs." border="false":::

|<span data-ttu-id="d6f0b-193">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="d6f0b-193">Counter</span></span>|<span data-ttu-id="d6f0b-194">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d6f0b-194">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="d6f0b-195">1</span><span class="sxs-lookup"><span data-stu-id="d6f0b-195">1</span></span>|<span data-ttu-id="d6f0b-196">**Einstellungen**: (Optional) Ermöglicht es Benutzern, die Einstellungen einer Registerkarte zu ändern, nachdem sie hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-196">**Settings**: (Optional) Allows users to modify a tab’s settings after it’s been added.</span></span>|
|<span data-ttu-id="d6f0b-197">2</span><span class="sxs-lookup"><span data-stu-id="d6f0b-197">2</span></span>|<span data-ttu-id="d6f0b-198">**Umbenennen**: Ermöglicht Benutzern, der Registerkarte einen Namen zu geben, der für das Team aussagekräftiger ist.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-198">**Rename**: Allows users to give the tab a name that’s more meaningful to the team.</span></span>|
|<span data-ttu-id="d6f0b-199">3</span><span class="sxs-lookup"><span data-stu-id="d6f0b-199">3</span></span>|<span data-ttu-id="d6f0b-200">**Entfernen**: Entfernt die Registerkarte aus dem Kanal, Chat oder Besprechung.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-200">**Remove**: Removes the tab from the channel, chat, or meeting.</span></span>|

## <a name="tab-notifications-and-deep-linking"></a><span data-ttu-id="d6f0b-201">Tab-Benachrichtigungen und Deep-Linking</span><span class="sxs-lookup"><span data-stu-id="d6f0b-201">Tab notifications and deep linking</span></span>

<span data-ttu-id="d6f0b-202">Sie können eine Nachricht mit einem tiefen Link zu Ihrer Registerkarte senden. Eine Karte zeigt z. B. eine Zusammenfassung der Fehlerdaten an, die ein Benutzer auswählen kann, um den gesamten Fehler auf einer Registerkarte anzuzeigen. Das Senden von Nachrichten über Tab-Aktivität erhöht das Bewusstsein, ohne alle explizit zu benachrichtigen (d. h. Aktivitäten ohne Rauschen).</span><span class="sxs-lookup"><span data-stu-id="d6f0b-202">You can send a message with a deep link to your tab. For example, a card shows a summary of bug data a user can select to see the entire bug in a tab. Sending messages about tab activity increases awareness without explicitly notifying everyone (i.e., activity without noise).</span></span> <span data-ttu-id="d6f0b-203">Bei Bedarf können Sie auch bestimmte Benutzer @mention.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-203">You also can @mention specific users if needed.</span></span>

<span data-ttu-id="d6f0b-204">Benachrichtigen Sie Benutzer über die Registerkartenaktivität auf eine der folgenden Möglichkeiten:</span><span class="sxs-lookup"><span data-stu-id="d6f0b-204">Notify users of tab activity one of the following ways:</span></span>

* <span data-ttu-id="d6f0b-205">**Bot**: Diese Methode wird bevorzugt, insbesondere wenn der Tab-Thread zielgerichtet ist.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-205">**Bot**: This method is preferred especially if the tab thread is targeted.</span></span> <span data-ttu-id="d6f0b-206">Die Threadunterhaltung der Registerkarte wird als kürzlich aktiv in die Ansicht verschoben.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-206">The tab’s threaded conversation is moved into view as recently active.</span></span> <span data-ttu-id="d6f0b-207">Diese Methode ermöglicht auch eine gewisse Raffinesse bei der Art und Weise, wie die Benachrichtigung gesendet wird.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-207">This method also allows for some sophistication in how the notification is sent.</span></span>
* <span data-ttu-id="d6f0b-208">**Meldung**: Eine Meldung wird im Aktivitätsfeed des Benutzers mit einem [tiefen Link zur Registerkarte](../../concepts/build-and-test/deep-links.md?view=msteams-client-js-latest&preserve-view=true)angezeigt.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-208">**Message**: A message shows up in the user’s activity feed with a [deep link to the tab](../../concepts/build-and-test/deep-links.md?view=msteams-client-js-latest&preserve-view=true).</span></span>

## <a name="best-practices"></a><span data-ttu-id="d6f0b-209">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="d6f0b-209">Best practices</span></span>

<span data-ttu-id="d6f0b-210">Verwenden Sie diese Empfehlungen, um eine hochwertige App-Erfahrung zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="d6f0b-210">Use these recommendations to create a quality app experience:</span></span>

### <a name="collaboration"></a><span data-ttu-id="d6f0b-211">Zusammenarbeit</span><span class="sxs-lookup"><span data-stu-id="d6f0b-211">Collaboration</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-collaboration-do.png" alt-text="Die Abbildung zeigt, was mit dem Tab-Navigationsdesign zu tun ist." border="false":::

#### <a name="do-facilitate-conversation"></a><span data-ttu-id="d6f0b-213">Tun: Erleichtern Sie die Unterhaltung</span><span class="sxs-lookup"><span data-stu-id="d6f0b-213">Do: Facilitate conversation</span></span>

<span data-ttu-id="d6f0b-214">Schließen Sie Inhalte und Komponenten ein, über die Menschen sprechen können.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-214">Include content and components people can talk about.</span></span> <span data-ttu-id="d6f0b-215">Wenn es nicht in den Kontext eines Chats, Kanals oder Meetings passt, gehört es nicht zu Ihrer Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-215">If it doesn’t fit within the context of a chat, channel, or meeting, it doesn’t belong in your tab.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-collaboration-dont.png" alt-text="Das Beispiel zeigt, was nicht mit dem Tab-Navigationsdesign zu tun ist." border="false":::

#### <a name="dont-treat-your-tab-like-any-other-webpage"></a><span data-ttu-id="d6f0b-217">Nicht: Behandeln Sie Ihre Registerkarte wie jede andere Webseite</span><span class="sxs-lookup"><span data-stu-id="d6f0b-217">Don't: Treat your tab like any other webpage</span></span>

<span data-ttu-id="d6f0b-218">Eine Registerkarte ist keine Webseite, die jemand einmal anzeigen kann.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-218">A tab isn’t a webpage someone might view once.</span></span> <span data-ttu-id="d6f0b-219">Eine Registerkarte sollte Ihre wichtigsten, relevanten Inhalte anzeigen, die Menschen benötigen, um gemeinsam etwas zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-219">A tab should display your most important, relevant content that people need to accomplish something together.</span></span>

   :::column-end:::
:::row-end:::

### <a name="navigation"></a><span data-ttu-id="d6f0b-220">Navigation</span><span class="sxs-lookup"><span data-stu-id="d6f0b-220">Navigation</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-nav-do.png" alt-text="Beispiel, das zeigt, was mit dem Tab-Navigationsdesign zu tun ist." border="false":::

#### <a name="do-limit-tasks-and-data"></a><span data-ttu-id="d6f0b-222">Tun: Einschränken von Aufgaben und Daten</span><span class="sxs-lookup"><span data-stu-id="d6f0b-222">Do: Limit tasks and data</span></span>

<span data-ttu-id="d6f0b-223">Registerkarten funktionieren am besten, wenn sie auf bestimmte Bedürfnisse eingehen.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-223">Tabs work best when they address specific needs.</span></span> <span data-ttu-id="d6f0b-224">Schließen Sie einen begrenzten Satz von Aufgaben und Daten ein, die für das Team oder die Gruppe relevant sind.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-224">Include a limited set of tasks and data relevant to the team or group.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-nav-dont.png" alt-text="Abbildung zeigt, was nicht mit tab Navigation Design zu tun." border="false":::

#### <a name="dont-embed-your-entire-app"></a><span data-ttu-id="d6f0b-226">Nicht: Einbetten Sie Ihre gesamte App</span><span class="sxs-lookup"><span data-stu-id="d6f0b-226">Don't: Embed your entire app</span></span>

<span data-ttu-id="d6f0b-227">Die Verwendung einer Registerkarte zum Anzeigen einer gesamten App mit mehrstufiger Navigation und komplexen Interaktionen führt zu einer Informationsüberlastung.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-227">Using a tab to display an entire app with multi-level navigation and complex interactions leads to information overload.</span></span>

   :::column-end:::
:::row-end:::

### <a name="setup"></a><span data-ttu-id="d6f0b-228">Setup</span><span class="sxs-lookup"><span data-stu-id="d6f0b-228">Setup</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-setup-do.png" alt-text="Abbildung zeigt, was mit dem Entwurf des Tab-Setups zu tun ist." border="false":::

#### <a name="do-keep-it-simple"></a><span data-ttu-id="d6f0b-230">Tun: Halten Sie es einfach</span><span class="sxs-lookup"><span data-stu-id="d6f0b-230">Do: Keep it simple</span></span>

<span data-ttu-id="d6f0b-231">Wenn Ihre App eine Authentifizierung erfordert, versuchen Sie, Microsoft Single Sign-On (SSO) zu integrieren, um eine nahtlosere Anmeldung zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-231">If your app requires authentication, try integrating Microsoft single sign-on (SSO) for a more seamless sign-in experience.</span></span> <span data-ttu-id="d6f0b-232">Enthalten auch nur wichtige Informationen und Schritte zum Hinzufügen der Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-232">Also, only include essential information and steps to add the tab.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-setup-dont.png" alt-text="Abbildung zeigt, was nicht mit dem Entwurf des Tab-Setups zu tun hat." border="false":::

#### <a name="dont-have-too-many-steps"></a><span data-ttu-id="d6f0b-234">Nicht: Haben Sie zu viele Schritte</span><span class="sxs-lookup"><span data-stu-id="d6f0b-234">Don't: Have too many steps</span></span>

<span data-ttu-id="d6f0b-235">Entfernen Sie alle unnötigen Schritte zum Hinzufügen einer Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-235">Remove any unnecessary steps for adding a tab.</span></span>

   :::column-end:::
:::row-end:::

### <a name="theming"></a><span data-ttu-id="d6f0b-236">Designs</span><span class="sxs-lookup"><span data-stu-id="d6f0b-236">Theming</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-theming-do.png" alt-text="Abbildung zeigt, was mit Tab-Theming zu tun ist." border="false":::

#### <a name="do-take-advantage-of-teams-color-tokens"></a><span data-ttu-id="d6f0b-238">Tun: Nutzen Sie Teams Farbtoken</span><span class="sxs-lookup"><span data-stu-id="d6f0b-238">Do: Take advantage of Teams color tokens</span></span>

<span data-ttu-id="d6f0b-239">Jedes Teams-Thema hat sein eigenes Farbschema.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-239">Each Teams theme has its own color scheme.</span></span> <span data-ttu-id="d6f0b-240">Um Designänderungen automatisch zu behandeln, verwenden Sie <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">Farbtoken (Fluent UI)</a> in Ihrem Entwurf.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-240">To handle theme changes automatically, use <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">color tokens (Fluent UI)</a> in your design.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-theming-dont.png" alt-text="Abbildung zeigt, was nicht mit Tab-Theming zu tun." border="false":::

#### <a name="dont-hard-code-color-values"></a><span data-ttu-id="d6f0b-242">Nicht: Harte Code-Farbwerte</span><span class="sxs-lookup"><span data-stu-id="d6f0b-242">Don't: Hard code color values</span></span>

<span data-ttu-id="d6f0b-243">Wenn Sie keine Teams Farbtoken verwenden, sind Ihre Designs weniger skalierbar und nehmen mehr Zeit in Anspruch.</span><span class="sxs-lookup"><span data-stu-id="d6f0b-243">If you don’t use Teams color tokens, your designs will be less scalable and take more time to manage.</span></span>

   :::column-end:::
:::row-end:::
