---
title: Entwerfen von Aufgabenmodulen
author: heath-hamilton
description: Erfahren Sie, wie Sie Aufgabenmodule für Teams entwerfen und das Microsoft Teams UI Kit erhalten.
localization_priority: Normal
ms.author: lajanuar
ms.topic: reference
ms.openlocfilehash: 48e47a6c0bde0f0a3fefb8fcbfb362687ce58947
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2021
ms.locfileid: "52629921"
---
# <a name="designing-task-modules-for-your-microsoft-teams-app"></a><span data-ttu-id="cf842-103">Entwerfen von Aufgabenmodulen für Microsoft Teams App</span><span class="sxs-lookup"><span data-stu-id="cf842-103">Designing task modules for your Microsoft Teams app</span></span>

<span data-ttu-id="cf842-104">Sie können modale Popuperfahrungen in Ihrer Teams mit Aufgabenmodulen erstellen.</span><span class="sxs-lookup"><span data-stu-id="cf842-104">You can create modal popup experiences in your Teams app with task modules.</span></span> <span data-ttu-id="cf842-105">Verwenden Sie diese Funktion zum Anzeigen von Rich Media und Informationen oder zum Abschließen einer komplexen Aufgabe.</span><span class="sxs-lookup"><span data-stu-id="cf842-105">Use this capability to display rich media and information or complete a complex task.</span></span>

:::image type="content" source="../../assets/images/task-module/task-module-overview.png" alt-text="Beispiel zeigt ein Aufgabenmodul." border="false":::

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="cf842-107">Microsoft Teams-UI-Kit</span><span class="sxs-lookup"><span data-stu-id="cf842-107">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="cf842-108">Umfassendere Entwurfsrichtlinien für Aufgabenmodule, einschließlich Elemente, die Sie bei Bedarf packen und ändern können, finden Sie im Microsoft Teams UI Kit.</span><span class="sxs-lookup"><span data-stu-id="cf842-108">You can find more comprehensive task module design guidelines, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cf842-109">Holen Sie sich das Microsoft Teams-UI-Kit (Figma)</span><span class="sxs-lookup"><span data-stu-id="cf842-109">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="open-a-task-module"></a><span data-ttu-id="cf842-110">Öffnen eines Aufgabenmoduls</span><span class="sxs-lookup"><span data-stu-id="cf842-110">Open a task module</span></span>

<span data-ttu-id="cf842-111">Aufgabenmodule können von fast überall in Ihrer App gestartet werden.</span><span class="sxs-lookup"><span data-stu-id="cf842-111">Task modules can be launched from almost anywhere in your app.</span></span>

* <span data-ttu-id="cf842-112">**Registerkarte**: Ein Aufgabenmodul kann über einen beliebigen Link innerhalb einer Registerkarte gestartet werden. Wird in Szenarien verwendet, in denen der Benutzer sich auf eine Interaktion konzentrieren soll.</span><span class="sxs-lookup"><span data-stu-id="cf842-112">**Tab**: A task module can be launched from any link within a tab. Use in scenarios where you want the user to focus on an interaction.</span></span>
* <span data-ttu-id="cf842-113">**Bot**: Ein Aufgabenmodul kann über einen Link innerhalb einer Botnachricht gestartet werden.</span><span class="sxs-lookup"><span data-stu-id="cf842-113">**Bot**: A task module can be launched from a link inside a bot message.</span></span>
* <span data-ttu-id="cf842-114">**Adaptive Karte:** Ein Aufgabenmodul kann von einer adaptiven Karte (gesendet mit einer Messagingerweiterung oder von einem Bot) gestartet werden, wenn ein Benutzer eine Schaltfläche auswählt.</span><span class="sxs-lookup"><span data-stu-id="cf842-114">**Adaptive Card**: A task module can be launched from an Adaptive Card (sent with a messaging extension or by a bot) when a user selects a button.</span></span>
* <span data-ttu-id="cf842-115">**Messagingerweiterung (Aktionsbefehle):** Mit Messagingerweiterungen können Sie eine bestimmte Aktion für Nachrichteninhalte ausführen.</span><span class="sxs-lookup"><span data-stu-id="cf842-115">**Messaging extension (action commands)**: Messaging extensions allow you to take a particular action on message content.</span></span> <span data-ttu-id="cf842-116">Wenn Sie eine Aktion auswählen, wird ein Aufgabenmodul geöffnet.</span><span class="sxs-lookup"><span data-stu-id="cf842-116">Selecting an action opens a task module.</span></span>
* <span data-ttu-id="cf842-117">**Messagingerweiterung (Kontext des Verfassenfelds):** Im Verfassenfeld können Sie eine Messagingerweiterung entwerfen, um ein Aufgabenmodul anstelle des typischen Flyouts zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="cf842-117">**Messaging extension (compose box context)**: In the compose box, you can design a messaging extension to open a task module instead of the typical flyout.</span></span> <span data-ttu-id="cf842-118">Reservieren Sie Aufgabenmodule für komplexe Interaktionen, z. B. das Ausfüllen eines Formulars.</span><span class="sxs-lookup"><span data-stu-id="cf842-118">Reserve task modules for complex interactions, such as completing a form.</span></span>

## <a name="anatomy"></a><span data-ttu-id="cf842-119">Anatomie</span><span class="sxs-lookup"><span data-stu-id="cf842-119">Anatomy</span></span>

<span data-ttu-id="cf842-120">Aufgabenmodule bieten eine flexible Oberfläche für gehostete App-Oberflächen.</span><span class="sxs-lookup"><span data-stu-id="cf842-120">Task modules provide a flexible surface for hosted app experiences.</span></span> <span data-ttu-id="cf842-121">Sie werden mit einem iframe (Desktop) oder webview (mobil) erstellt, sodass Sie Aufgabenmodule mit unseren Benutzeroberflächenvorlagen (empfohlen) oder von Grund auf neu entwerfen können.</span><span class="sxs-lookup"><span data-stu-id="cf842-121">They're built using an iframe (desktop) or webview (mobile), so you can design task modules with our UI templates (recommended) or from scratch.</span></span>

<span data-ttu-id="cf842-122">Sie können auch mit dem [Adaptive Cards-Framework](../../task-modules-and-cards/cards/design-effective-cards.md) erstellt werden. Dies kann eine einfachere und schnellere Möglichkeit sein, gängige Szenarien (z. B. Formulare) zu erleichtern.</span><span class="sxs-lookup"><span data-stu-id="cf842-122">They can also be built with the [Adaptive Cards](../../task-modules-and-cards/cards/design-effective-cards.md) framework, which can be a simpler and faster way to facilitate common scenarios (such as forms).</span></span>

# <a name="desktop"></a>[<span data-ttu-id="cf842-123">Desktop</span><span class="sxs-lookup"><span data-stu-id="cf842-123">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/task-module/task-module-anatomy.png" alt-text="Abbildung der Ui-Anatomie eines Aufgabenmoduls." border="false":::

|<span data-ttu-id="cf842-125">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="cf842-125">Counter</span></span>|<span data-ttu-id="cf842-126">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="cf842-126">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="cf842-127">1</span><span class="sxs-lookup"><span data-stu-id="cf842-127">1</span></span>|<span data-ttu-id="cf842-128">**App-Symbol**</span><span class="sxs-lookup"><span data-stu-id="cf842-128">**App icon**</span></span>|
|<span data-ttu-id="cf842-129">2</span><span class="sxs-lookup"><span data-stu-id="cf842-129">2</span></span>|<span data-ttu-id="cf842-130">**App-Name**: Vollständiger Name Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="cf842-130">**App name**: Full name of your app.</span></span>|
|<span data-ttu-id="cf842-131">3</span><span class="sxs-lookup"><span data-stu-id="cf842-131">3</span></span>|<span data-ttu-id="cf842-132">**Kopfzeile**: Kopfzeilen klar und prägnant machen.</span><span class="sxs-lookup"><span data-stu-id="cf842-132">**Header**: Make headers clear and concise.</span></span> <span data-ttu-id="cf842-133">Beschreiben Sie die Aufgabe, die Benutzer abschließen möchten.</span><span class="sxs-lookup"><span data-stu-id="cf842-133">Describe the task you want users to complete.</span></span>
|<span data-ttu-id="cf842-134">4 </span><span class="sxs-lookup"><span data-stu-id="cf842-134">4</span></span>|<span data-ttu-id="cf842-135">**Schaltfläche Schließen**: Schließt das Aufgabenmodul.</span><span class="sxs-lookup"><span data-stu-id="cf842-135">**Close button**: Closes the task module.</span></span> <span data-ttu-id="cf842-136">Nicht gespeicherte Änderungen werden nicht in den App-Inhalten angewendet.</span><span class="sxs-lookup"><span data-stu-id="cf842-136">Does not apply unsaved changes in the app content.</span></span>|
|<span data-ttu-id="cf842-137">5 </span><span class="sxs-lookup"><span data-stu-id="cf842-137">5</span></span>|<span data-ttu-id="cf842-138">**iframe**: Responsive space that hosts your app content.</span><span class="sxs-lookup"><span data-stu-id="cf842-138">**iframe**: Responsive space that hosts your app content.</span></span>|
|<span data-ttu-id="cf842-139">6 </span><span class="sxs-lookup"><span data-stu-id="cf842-139">6</span></span>|<span data-ttu-id="cf842-140">**Aktionen (optional):** Schaltflächen im Zusammenhang mit Ihrem App-Inhalt.</span><span class="sxs-lookup"><span data-stu-id="cf842-140">**Actions (optional)**: Buttons related to your app content.</span></span>|

# <a name="mobile"></a>[<span data-ttu-id="cf842-141">Mobil</span><span class="sxs-lookup"><span data-stu-id="cf842-141">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/task-module/mobile-task-module-anatomy.png" alt-text="Abbildung der Benutzeroberflächenanatomie eines Aufgabenmoduls auf mobilen Geräten." border="false":::

|<span data-ttu-id="cf842-143">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="cf842-143">Counter</span></span>|<span data-ttu-id="cf842-144">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="cf842-144">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="cf842-145">1</span><span class="sxs-lookup"><span data-stu-id="cf842-145">1</span></span>|<span data-ttu-id="cf842-146">**Kopfzeile**: Kopfzeilen klar und prägnant machen.</span><span class="sxs-lookup"><span data-stu-id="cf842-146">**Header**: Make headers clear and concise.</span></span> <span data-ttu-id="cf842-147">Beschreiben Sie die Aufgabe, die Benutzer abschließen möchten.</span><span class="sxs-lookup"><span data-stu-id="cf842-147">Describe the task you want users to complete.</span></span>
|<span data-ttu-id="cf842-148">2</span><span class="sxs-lookup"><span data-stu-id="cf842-148">2</span></span>|<span data-ttu-id="cf842-149">**App-Name**: Vollständiger Name Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="cf842-149">**App name**: Full name of your app.</span></span>|
|<span data-ttu-id="cf842-150">3</span><span class="sxs-lookup"><span data-stu-id="cf842-150">3</span></span>|<span data-ttu-id="cf842-151">**Schaltfläche Schließen**: Schließt das Aufgabenmodul.</span><span class="sxs-lookup"><span data-stu-id="cf842-151">**Close button**: Closes the task module.</span></span> <span data-ttu-id="cf842-152">Nicht gespeicherte Änderungen werden nicht in den App-Inhalten angewendet.</span><span class="sxs-lookup"><span data-stu-id="cf842-152">Does not apply unsaved changes in the app content.</span></span>|
|<span data-ttu-id="cf842-153">4 </span><span class="sxs-lookup"><span data-stu-id="cf842-153">4</span></span>|<span data-ttu-id="cf842-154">**webview**: Responsive space that hosts your app content.</span><span class="sxs-lookup"><span data-stu-id="cf842-154">**webview**: Responsive space that hosts your app content.</span></span>|
|<span data-ttu-id="cf842-155">5 </span><span class="sxs-lookup"><span data-stu-id="cf842-155">5</span></span>|<span data-ttu-id="cf842-156">**Aktionen (optional):** Schaltflächen im Zusammenhang mit Ihrem App-Inhalt.</span><span class="sxs-lookup"><span data-stu-id="cf842-156">**Actions (optional)**: Buttons related to your app content.</span></span>|

---

## <a name="designing-with-ui-templates"></a><span data-ttu-id="cf842-157">Entwerfen mit Benutzeroberflächenvorlagen</span><span class="sxs-lookup"><span data-stu-id="cf842-157">Designing with UI templates</span></span>

<span data-ttu-id="cf842-158">Erwägen Sie die Verwendung von Vorlagen für allgemeine Layouts in Ihren Aufgabenmodulen.</span><span class="sxs-lookup"><span data-stu-id="cf842-158">Consider using templates for common layouts inside your task modules.</span></span> <span data-ttu-id="cf842-159">Jede besteht aus kleineren Komponenten, um ein elegantes, ansprechendes Design zu erstellen, das von vorn oder für Ihr Szenario oder Ihr Markendesign angepasst werden kann.</span><span class="sxs-lookup"><span data-stu-id="cf842-159">Each one is made up of smaller components to create an elegant, responsive design that can be used out of the box or customized for your scenario or with your brand look and feel.</span></span>

* <span data-ttu-id="cf842-160">[Liste](../../concepts/design/design-teams-app-ui-templates.md#list): Listen können verwandte Elemente in einem scannierbaren Format anzeigen und Benutzern das Ausführen von Aktionen für eine gesamte Liste oder einzelne Elemente ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="cf842-160">[List](../../concepts/design/design-teams-app-ui-templates.md#list): Lists can display related items in a scannable format and allow users to take actions on an entire list or individual items.</span></span>
* <span data-ttu-id="cf842-161">[Formular](../../concepts/design/design-teams-app-ui-templates.md#form): Formulare sind für die strukturierte Erfassung, Validierung und Übermittlung von Benutzereingaben.</span><span class="sxs-lookup"><span data-stu-id="cf842-161">[Form](../../concepts/design/design-teams-app-ui-templates.md#form): Forms are for collecting, validating, and submitting user input in a structured way.</span></span>
* <span data-ttu-id="cf842-162">[Leerer](../../concepts/design/design-teams-app-ui-templates.md#empty-state)Zustand: Die Vorlage für den leeren Zustand kann für viele Szenarien verwendet werden, z. B. für die Anmeldung, die Erstlauferfahrung, Fehlermeldungen und vieles mehr.</span><span class="sxs-lookup"><span data-stu-id="cf842-162">[Empty state](../../concepts/design/design-teams-app-ui-templates.md#empty-state): The empty state template can be used for many scenarios, including sign in, first-run experiences, error messages, and more.</span></span>

## <a name="examples"></a><span data-ttu-id="cf842-163">Beispiele</span><span class="sxs-lookup"><span data-stu-id="cf842-163">Examples</span></span>

### <a name="list"></a><span data-ttu-id="cf842-164">Liste</span><span class="sxs-lookup"><span data-stu-id="cf842-164">List</span></span>

<span data-ttu-id="cf842-165">Listen funktionieren in einem Aufgabenmodul gut, da sie einfach zu scannen sind.</span><span class="sxs-lookup"><span data-stu-id="cf842-165">Lists work nicely in a task module because they're easy to scan.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="cf842-166">Desktop</span><span class="sxs-lookup"><span data-stu-id="cf842-166">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/task-module/list.png" alt-text="Beispielliste in einem Aufgabenmodul." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="cf842-168">Mobil</span><span class="sxs-lookup"><span data-stu-id="cf842-168">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/task-module/mobile-list.png" alt-text="Beispielliste in einem Aufgabenmodul auf Mobilgeräten." border="false":::

---

### <a name="form"></a><span data-ttu-id="cf842-170">Formular</span><span class="sxs-lookup"><span data-stu-id="cf842-170">Form</span></span>

<span data-ttu-id="cf842-171">Aufgabenmodule sind ein hervorragender Ort, um Formulare mit sequenziellen Benutzereingaben und Inlineüberprüfungen zu benutzeroberflächen.</span><span class="sxs-lookup"><span data-stu-id="cf842-171">Task modules are a great place to surface forms with sequential user inputs and inline validation.</span></span> <span data-ttu-id="cf842-172">Sie können adaptive Karten als Möglichkeit zum Einbetten von Formularelementen verwenden.</span><span class="sxs-lookup"><span data-stu-id="cf842-172">You can leverage Adaptive Cards as a way to embed form elements.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="cf842-173">Desktop</span><span class="sxs-lookup"><span data-stu-id="cf842-173">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/task-module/form.png" alt-text="Beispielformular in einem Aufgabenmodul." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="cf842-175">Mobil</span><span class="sxs-lookup"><span data-stu-id="cf842-175">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/task-module/mobile-form.png" alt-text="Beispielformular in einem Aufgabenmodul auf mobilen Geräten." border="false":::

---

### <a name="sign-in"></a><span data-ttu-id="cf842-177">Anmelden</span><span class="sxs-lookup"><span data-stu-id="cf842-177">Sign in</span></span>

<span data-ttu-id="cf842-178">Erstellen Sie einen fokussierten Anmelde- oder Anmeldefluss mit einer Reihe von Aufgabenmodulen, mit der benutzer sich problemlos durch sequenzielle Schritte bewegen können.</span><span class="sxs-lookup"><span data-stu-id="cf842-178">Create a focused sign in or sign-up flow with a series of task modules, letting users move easily through sequential steps.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="cf842-179">Desktop</span><span class="sxs-lookup"><span data-stu-id="cf842-179">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/task-module/sign-in.png" alt-text="Beispiel für die Anmeldeerfahrung in einem Aufgabenmodul." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="cf842-181">Mobil</span><span class="sxs-lookup"><span data-stu-id="cf842-181">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/task-module/mobile-sign-in.png" alt-text="Beispiel für die Anmeldeerfahrung in einem Aufgabenmodul auf Mobilgeräten." border="false":::

---

### <a name="media"></a><span data-ttu-id="cf842-183">Medien</span><span class="sxs-lookup"><span data-stu-id="cf842-183">Media</span></span>

<span data-ttu-id="cf842-184">Einbetten von Medieninhalten in ein Aufgabenmodul für eine fokussierte Anzeige.</span><span class="sxs-lookup"><span data-stu-id="cf842-184">Embed media content in a task module for a focused viewing experience.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="cf842-185">Desktop</span><span class="sxs-lookup"><span data-stu-id="cf842-185">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/task-module/media.png" alt-text="Beispiel für Medieninhalte in einem Aufgabenmodul." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="cf842-187">Mobil</span><span class="sxs-lookup"><span data-stu-id="cf842-187">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/task-module/mobile-media.png" alt-text="Beispiel für Medieninhalte in einem Aufgabenmodul auf Mobilgeräten." border="false":::

---

### <a name="empty-state"></a><span data-ttu-id="cf842-189">Leerer Status</span><span class="sxs-lookup"><span data-stu-id="cf842-189">Empty state</span></span>

<span data-ttu-id="cf842-190">Wird für Willkommens-, Fehler- und Erfolgsmeldungen verwendet.</span><span class="sxs-lookup"><span data-stu-id="cf842-190">Use for welcome, error, and success messages.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="cf842-191">Desktop</span><span class="sxs-lookup"><span data-stu-id="cf842-191">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/task-module/empty-state.png" alt-text="Beispiel leerer Zustand in einem Aufgabenmodul." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="cf842-193">Mobil</span><span class="sxs-lookup"><span data-stu-id="cf842-193">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/task-module/mobile-empty-state.png" alt-text="Beispiel leerer Zustand in einem Aufgabenmodul auf mobilen Geräten." border="false":::

---

### <a name="image-gallery"></a><span data-ttu-id="cf842-195">Bildergalerie</span><span class="sxs-lookup"><span data-stu-id="cf842-195">Image gallery</span></span>

<span data-ttu-id="cf842-196">Ein Katalog karussell in einen iframe (Desktop) oder webview (mobil) einbetten.</span><span class="sxs-lookup"><span data-stu-id="cf842-196">Embed a gallery carousel in an iframe (desktop) or webview (mobile).</span></span>

# <a name="desktop"></a>[<span data-ttu-id="cf842-197">Desktop</span><span class="sxs-lookup"><span data-stu-id="cf842-197">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/task-module/image-gallery.png" alt-text="Beispielbildkatalog in einem Aufgabenmodul." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="cf842-199">Mobil</span><span class="sxs-lookup"><span data-stu-id="cf842-199">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/task-module/mobile-image-gallery.png" alt-text="Beispielbildkatalog in einem Aufgabenmodul auf Mobilgeräten." border="false":::

---

### <a name="poll"></a><span data-ttu-id="cf842-201">Umfrage</span><span class="sxs-lookup"><span data-stu-id="cf842-201">Poll</span></span>

<span data-ttu-id="cf842-202">In diesem Beispiel werden Umfrageergebnisse gezeigt, die von einer adaptiven Karte gestartet wurden.</span><span class="sxs-lookup"><span data-stu-id="cf842-202">This example shows poll results launched from an Adaptive Card.</span></span> <span data-ttu-id="cf842-203">Die Abfrage kann auch in einem Aufgabenmodul platziert werden.</span><span class="sxs-lookup"><span data-stu-id="cf842-203">The poll can be placed inside a task module, too.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="cf842-204">Desktop</span><span class="sxs-lookup"><span data-stu-id="cf842-204">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/task-module/poll.png" alt-text="Beispielumfrage in einem Aufgabenmodul." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="cf842-206">Mobil</span><span class="sxs-lookup"><span data-stu-id="cf842-206">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/task-module/mobile-poll.png" alt-text="Beispielumfrage in einem Aufgabenmodul auf Mobilgeräten." border="false":::

---

## <a name="best-practices"></a><span data-ttu-id="cf842-208">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="cf842-208">Best practices</span></span>

<span data-ttu-id="cf842-209">Verwenden Sie diese Empfehlungen, um eine hochwertige App-Erfahrung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="cf842-209">Use these recommendations to create a quality app experience.</span></span>

### <a name="usability"></a><span data-ttu-id="cf842-210">Benutzerfreundlichkeit</span><span class="sxs-lookup"><span data-stu-id="cf842-210">Usability</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/usability-do.png" alt-text="Beispiel für eine bewährte Methode für ein Aufgabenmodul (ein Aufgabenmodul nach dem anderen)." border="false":::

#### <a name="do-use-one-task-module-at-a-time"></a><span data-ttu-id="cf842-212">Do: Verwenden eines Aufgabenmoduls gleichzeitig</span><span class="sxs-lookup"><span data-stu-id="cf842-212">Do: Use one task module at a time</span></span>

<span data-ttu-id="cf842-213">Ziel ist es, den Benutzer auf das Abschließen einer Aufgabe zu konzentrieren.</span><span class="sxs-lookup"><span data-stu-id="cf842-213">The goal is to focus the user on completing a task after all!</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/usability-dont.png" alt-text="Beispiel für eine bewährte Methode für ein Aufgabenmodul (Öffnen eines Dialogfelds über einem Aufgabenmodul)." border="false":::

#### <a name="dont-pop-a-dialog-on-top-of-a-task-module"></a><span data-ttu-id="cf842-215">Don't: Pop a dialog on top of a task module</span><span class="sxs-lookup"><span data-stu-id="cf842-215">Don't: Pop a dialog on top of a task module</span></span>

<span data-ttu-id="cf842-216">Dies führt zu einer unkonzentrierten, verwirrenden Benutzeroberfläche.</span><span class="sxs-lookup"><span data-stu-id="cf842-216">This creates an unfocused, confusing user experience.</span></span>

   :::column-end:::
:::row-end:::

### <a name="responsive"></a><span data-ttu-id="cf842-217">Reaktionsfähig</span><span class="sxs-lookup"><span data-stu-id="cf842-217">Responsive</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/responsive-do.png" alt-text="Beispiel für eine bewährte Methode für ein Aufgabenmodul (Stellen Sie sicher, dass der Inhalt reaktionsfähig ist)." border="false":::

#### <a name="do-make-sure-the-content-is-responsive"></a><span data-ttu-id="cf842-219">Do: Stellen Sie sicher, dass der Inhalt reaktionsfähig ist</span><span class="sxs-lookup"><span data-stu-id="cf842-219">Do: Make sure the content is responsive</span></span>

<span data-ttu-id="cf842-220">Während adaptive Karten, die in einem Aufgabenmodul gehostet werden, auf mobilen Geräten gut gerendert werden, stellen Sie sicher, dass die Benutzeroberfläche reaktionsfähig ist und geräteübergreifend gut funktioniert, wenn Sie einen iframe zum Hosten von App-Inhalten verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="cf842-220">While Adaptive Cards hosted in a task module render well on mobile devices, if you choose to use an iframe to host app content, make sure the UI is responsive and works well across devices.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/responsive-dont.png" alt-text="Beispiel für eine bewährte Methode für ein Aufgabenmodul (verwenden Sie keine horizontalen Bildlaufleisten)." border="false":::

#### <a name="dont-use-horizontal-scroll-bars"></a><span data-ttu-id="cf842-222">Don't: Verwenden horizontaler Bildlaufleisten</span><span class="sxs-lookup"><span data-stu-id="cf842-222">Don't: Use horizontal scroll bars</span></span>

<span data-ttu-id="cf842-223">Es ist eine bewährte Methode, inhalte fokussiert und nicht zu langwierig zu halten.</span><span class="sxs-lookup"><span data-stu-id="cf842-223">It's a best practice to keep content focused and not too lengthy.</span></span> <span data-ttu-id="cf842-224">Wenn ein Bildlauf erforderlich ist, scrollen Sie vertikal und nicht horizontal.</span><span class="sxs-lookup"><span data-stu-id="cf842-224">If a scroll is necessary, scroll vertically and not horizontally.</span></span>

   :::column-end:::
:::row-end:::

### <a name="simplicity"></a><span data-ttu-id="cf842-225">Einfachheit</span><span class="sxs-lookup"><span data-stu-id="cf842-225">Simplicity</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/simplicity-do.png" alt-text="Beispiel für eine bewährte Methode für ein Aufgabenmodul (kurz)." border="false":::

#### <a name="do-keep-it-short"></a><span data-ttu-id="cf842-227">Do: Keep it short</span><span class="sxs-lookup"><span data-stu-id="cf842-227">Do: Keep it short</span></span>

<span data-ttu-id="cf842-228">Sie können ganz einfach einen mehrstufigen Assistenten erstellen, aber das bedeutet nicht unbedingt, dass Sie es sollten!</span><span class="sxs-lookup"><span data-stu-id="cf842-228">You can easily create a multi-step wizard, but that doesn't necessarily mean you should!</span></span> <span data-ttu-id="cf842-229">Ein Aufgabenmodul mit mehreren Bildschirmen kann problematisch sein, da eingehende Nachrichten abgelenkt werden und Benutzer zum Beenden verleiten.</span><span class="sxs-lookup"><span data-stu-id="cf842-229">A multi-screen task module can be problematic because incoming messages are distracting and tempt users to exit.</span></span> <span data-ttu-id="cf842-230">Wenn Ihre Aufgabe wirklich beteiligt ist, wird anstelle eines Aufgabenmoduls eine vollständige Webseite angezeigt.</span><span class="sxs-lookup"><span data-stu-id="cf842-230">If your task is really involved, pop out to a full webpage instead of a task module.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/simplicity-dont.png" alt-text="Beispiel für bewährte Vorgehensweise für ein Aufgabenmodul (keine langen Interaktionen)." border="false":::

#### <a name="dont-have-long-interactions"></a><span data-ttu-id="cf842-232">Don't: Have long interactions</span><span class="sxs-lookup"><span data-stu-id="cf842-232">Don't: Have long interactions</span></span>

<span data-ttu-id="cf842-233">Versuchen Sie, Ihre Interaktionen kurz und auf den Punkt zu halten.</span><span class="sxs-lookup"><span data-stu-id="cf842-233">Try to keep your interactions short and to the point.</span></span>

   :::column-end:::
:::row-end:::

### <a name="error-messages"></a><span data-ttu-id="cf842-234">Fehlermeldungen</span><span class="sxs-lookup"><span data-stu-id="cf842-234">Error messages</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/error-messages-do.png" alt-text="Beispiel für eine bewährte Methode für ein Aufgabenmodul (Verwenden von Inlinefehlermeldungen)." border="false":::

#### <a name="do-use-inline-error-messages"></a><span data-ttu-id="cf842-236">Do: Verwenden von Inlinefehlermeldungen</span><span class="sxs-lookup"><span data-stu-id="cf842-236">Do: Use inline error messages</span></span>

<span data-ttu-id="cf842-237">Richtlinien zur Inlinefehlerbehandlung finden Sie in der Formularbenutzeroberflächenvorlage.</span><span class="sxs-lookup"><span data-stu-id="cf842-237">See the forms UI template for guidelines on inline error handling.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/error-messages-dont.png" alt-text="Beispiel für eine bewährte Methode für ein Aufgabenmodul (Setzen Sie Fehlermeldungen in Dialogfelder ein)." border="false":::

#### <a name="dont-put-error-messages-in-dialogs"></a><span data-ttu-id="cf842-239">Don't: Setzen von Fehlermeldungen in Dialogfelder</span><span class="sxs-lookup"><span data-stu-id="cf842-239">Don't: Put error messages in dialogs</span></span>

<span data-ttu-id="cf842-240">Geben Sie in einem Dialogfeld über einem Aufgabenmodul keine Fehlermeldung ein.</span><span class="sxs-lookup"><span data-stu-id="cf842-240">Don't pop an error message in a dialog on top of a task module.</span></span> <span data-ttu-id="cf842-241">Dadurch wird eine verwirrende Benutzeroberfläche erstellt.</span><span class="sxs-lookup"><span data-stu-id="cf842-241">It creates a confusing user experience.</span></span>

   :::column-end:::
:::row-end:::
