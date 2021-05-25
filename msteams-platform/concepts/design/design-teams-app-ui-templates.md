---
title: Entwerfen Ihrer App mit Benutzeroberflächenvorlagen
author: heath-hamilton
description: Entwerfen Sie Ihre App schneller mit standardisierten Benutzeroberflächenkomponenten, Layouts und Mustern, die häufig in verschiedenen Microsoft Teams.
ms.author: lajanuar
localization_priority: Normal
ms.topic: reference
ms.openlocfilehash: 5026554070396dcc55390496b6754961e8e037bc
ms.sourcegitcommit: 4224c44d169b1a289cbf1d3353de6bc6de7c7ea8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/25/2021
ms.locfileid: "52644859"
---
# <a name="designing-your-microsoft-teams-app-with-ui-templates"></a><span data-ttu-id="a2203-103">Entwerfen Ihrer Microsoft Teams-App mit Benutzeroberflächenvorlagen</span><span class="sxs-lookup"><span data-stu-id="a2203-103">Designing your Microsoft Teams app with UI templates</span></span>

<span data-ttu-id="a2203-104">Entwerfen Sie Microsoft Teams App schneller mit Benutzeroberflächenvorlagen.</span><span class="sxs-lookup"><span data-stu-id="a2203-104">Design your Microsoft Teams app faster with UI templates.</span></span> <span data-ttu-id="a2203-105">Bei den Vorlagen handelt es sich um eine Sammlung von Benutzeroberflächenbasierten Fluent-Komponenten, die Teams gängigen Verwendungsfällen funktionieren und Ihnen mehr Zeit zum Herausfinden der besten Benutzererfahrung bieten.</span><span class="sxs-lookup"><span data-stu-id="a2203-105">The templates are a collection of Fluent UI-based components that work across common Teams use cases, giving you more time to figure out the best experience for your users.</span></span>

## <a name="getting-started-with-tools-and-samples"></a><span data-ttu-id="a2203-106">Erste Schritte mit Tools und Beispielen</span><span class="sxs-lookup"><span data-stu-id="a2203-106">Getting started with tools and samples</span></span>

<span data-ttu-id="a2203-107">Mit den folgenden Ressourcen können Sie Ihre App mithilfe von Benutzeroberflächenvorlagen entwerfen und entwickeln.</span><span class="sxs-lookup"><span data-stu-id="a2203-107">The following resources can help you design and develop your app using UI templates.</span></span>

### <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="a2203-108">Microsoft Teams-UI-Kit</span><span class="sxs-lookup"><span data-stu-id="a2203-108">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="a2203-109">Greifen Sie ui templates for your app design from the Microsoft Teams UI Kit, which also includes extensive information about usage, anatomy, accessibility, and best practices.</span><span class="sxs-lookup"><span data-stu-id="a2203-109">Grab UI templates for your app design from the Microsoft Teams UI Kit, which also includes extensive information about usage, anatomy, accessibility, and best practices.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a2203-110">Benutzeroberflächenkit (Figma)</span><span class="sxs-lookup"><span data-stu-id="a2203-110">Get the UI kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

### <a name="microsoft-teams-ui-library"></a><span data-ttu-id="a2203-111">Microsoft Teams Benutzeroberflächenbibliothek</span><span class="sxs-lookup"><span data-stu-id="a2203-111">Microsoft Teams UI Library</span></span>

<span data-ttu-id="a2203-112">Anzeigen und Testen einzelner Teams benutzeroberflächenvorlagen und zugehörigen Komponenten in Ihrem Browser.</span><span class="sxs-lookup"><span data-stu-id="a2203-112">View and test individual Teams UI templates and related components in your browser.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a2203-113">Probieren Sie die Benutzeroberflächenbibliothek (Playground) aus.</span><span class="sxs-lookup"><span data-stu-id="a2203-113">Try the UI library (playground)</span></span>](https://dev-int.teams.microsoft.com/storybook/main/index.html)

<span data-ttu-id="a2203-114">Importieren Sie diese Vorlagen und zugehörigen Komponenten direkt in Teams App-Projekt.</span><span class="sxs-lookup"><span data-stu-id="a2203-114">Import these templates and related components directly into your Teams app project.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a2203-115">Benutzeroberflächenbibliothek (GitHub)</span><span class="sxs-lookup"><span data-stu-id="a2203-115">Get the UI library (GitHub)</span></span>](https://github.com/OfficeDev/microsoft-teams-ui-component-library)

### <a name="sample-app"></a><span data-ttu-id="a2203-116">Beispiel-App</span><span class="sxs-lookup"><span data-stu-id="a2203-116">Sample app</span></span>

<span data-ttu-id="a2203-117">Installieren Sie eine Beispiel-App, um zu sehen, wie Benutzeroberflächenvorlagen in Teams aussehen und verhalten.</span><span class="sxs-lookup"><span data-stu-id="a2203-117">Install a sample app to see how UI templates look and behave within Teams contexts.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a2203-118">Die Beispiel-App (GitHub)</span><span class="sxs-lookup"><span data-stu-id="a2203-118">Get the sample app (GitHub)</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-ui-templates/ts)

## <a name="dashboard"></a><span data-ttu-id="a2203-119">Dashboard</span><span class="sxs-lookup"><span data-stu-id="a2203-119">Dashboard</span></span>

<span data-ttu-id="a2203-120">Ein Dashboard zeigt unterschiedliche Inhaltstypen an einem zentralen Speicherort an (Teams persönliche App oder Registerkarte).</span><span class="sxs-lookup"><span data-stu-id="a2203-120">A dashboard displays different types of content in a central location (Teams personal app or tab).</span></span> <span data-ttu-id="a2203-121">Benutzer sollten in der Lage sein, zumindest einige der auf einem Dashboard angezeigten Informationen anzupassen.</span><span class="sxs-lookup"><span data-stu-id="a2203-121">Users should be able to customize at least some of what they see on a dashboard.</span></span>

### <a name="top-use-cases"></a><span data-ttu-id="a2203-122">Die am besten verwendeten Fälle</span><span class="sxs-lookup"><span data-stu-id="a2203-122">Top use cases</span></span>

* <span data-ttu-id="a2203-123">Analysieren von Daten</span><span class="sxs-lookup"><span data-stu-id="a2203-123">Analyze data</span></span>
* <span data-ttu-id="a2203-124">Berichtsmetriken</span><span class="sxs-lookup"><span data-stu-id="a2203-124">Report metrics</span></span>
* <span data-ttu-id="a2203-125">Organisieren verschiedener Informationen an einem Ort</span><span class="sxs-lookup"><span data-stu-id="a2203-125">Organize different information in one place</span></span>

# <a name="desktop"></a>[<span data-ttu-id="a2203-126">Desktop</span><span class="sxs-lookup"><span data-stu-id="a2203-126">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/ui-templates/dashboard.png" alt-text="Beispiel zeigt eine Dashboard-UI-Vorlage auf dem Desktop." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="a2203-128">Mobil</span><span class="sxs-lookup"><span data-stu-id="a2203-128">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/ui-templates/mobile-dashboard.png" alt-text="Beispiel zeigt eine Dashboardbenutzeroberflächenvorlage auf Mobilgeräten." border="false":::

---

## <a name="data-visualization"></a><span data-ttu-id="a2203-130">Datenvisualisierung</span><span class="sxs-lookup"><span data-stu-id="a2203-130">Data visualization</span></span>

<span data-ttu-id="a2203-131">Sie können verschiedene Kartengrößen (einzeln, doppelt und vollständig) verwenden, um Datenvisualisierungen auf derselben Seite zu stapeln und zu organisieren.</span><span class="sxs-lookup"><span data-stu-id="a2203-131">You can use different card sizes (single, double, and full) to stack and organize data visualizations on the same page.</span></span> <span data-ttu-id="a2203-132">Die Karten werden so skaliert, dass sie an das Spaltenlayout passen und leere Leerzeichen ausfüllen.</span><span class="sxs-lookup"><span data-stu-id="a2203-132">The cards scale to fit the column layout and fill in blank spaces.</span></span>

### <a name="top-use-cases"></a><span data-ttu-id="a2203-133">Die am besten verwendeten Fälle</span><span class="sxs-lookup"><span data-stu-id="a2203-133">Top use cases</span></span>

* <span data-ttu-id="a2203-134">Anzeigen komplexer Informationen</span><span class="sxs-lookup"><span data-stu-id="a2203-134">Display complex information</span></span>
* <span data-ttu-id="a2203-135">Erstellen eines Dashboards</span><span class="sxs-lookup"><span data-stu-id="a2203-135">Create a dashboard</span></span>

# <a name="desktop"></a>[<span data-ttu-id="a2203-136">Desktop</span><span class="sxs-lookup"><span data-stu-id="a2203-136">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/ui-templates/data-viz.png" alt-text="Beispiel zeigt eine Benutzeroberflächenvorlage für die Datenvisualisierung auf dem Desktop." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="a2203-138">Mobil</span><span class="sxs-lookup"><span data-stu-id="a2203-138">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/ui-templates/mobile-data-viz.png" alt-text="Beispiel zeigt eine Benutzeroberflächenvorlage für die Datenvisualisierung auf Mobilgeräten." border="false":::

---

## <a name="empty-state"></a><span data-ttu-id="a2203-140">Leerer Status</span><span class="sxs-lookup"><span data-stu-id="a2203-140">Empty state</span></span>

<span data-ttu-id="a2203-141">Die leere Zustandsvorlage kann für viele Szenarien verwendet werden, z. B. für die Anmeldung, die Erstlauferfahrung, Fehlermeldungen und vieles mehr.</span><span class="sxs-lookup"><span data-stu-id="a2203-141">The empty state template can be used for many scenarios, including sign in, first-run experiences, error messages, and more.</span></span> <span data-ttu-id="a2203-142">Es ist äußerst flexibel– passen Sie es an, um eine, einige oder alle Komponenten im folgenden Entwurf zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="a2203-142">It’s highly flexible⁠—adapt it to use one, a few, or all of the components in the following design.</span></span>

### <a name="top-use-cases"></a><span data-ttu-id="a2203-143">Die am besten verwendeten Fälle</span><span class="sxs-lookup"><span data-stu-id="a2203-143">Top use cases</span></span>

* <span data-ttu-id="a2203-144">Anmelden</span><span class="sxs-lookup"><span data-stu-id="a2203-144">Sign in</span></span>
* <span data-ttu-id="a2203-145">Willkommensnachrichten und Erstlauferfahrungen</span><span class="sxs-lookup"><span data-stu-id="a2203-145">Welcome messages and first-run experiences</span></span>
* <span data-ttu-id="a2203-146">Erfolgsmeldungen</span><span class="sxs-lookup"><span data-stu-id="a2203-146">Success messages</span></span>
* <span data-ttu-id="a2203-147">Fehlermeldungen</span><span class="sxs-lookup"><span data-stu-id="a2203-147">Error messages</span></span>

# <a name="desktop"></a>[<span data-ttu-id="a2203-148">Desktop</span><span class="sxs-lookup"><span data-stu-id="a2203-148">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/ui-templates/empty-state.png" alt-text="Beispiel zeigt eine leere Zustands-UI-Vorlage auf dem Desktop." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="a2203-150">Mobil</span><span class="sxs-lookup"><span data-stu-id="a2203-150">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/ui-templates/mobile-empty-state.png" alt-text="Beispiel zeigt eine leere Zustands-UI-Vorlage auf mobilen Geräten." border="false":::

---

## <a name="filter"></a><span data-ttu-id="a2203-152">Filter</span><span class="sxs-lookup"><span data-stu-id="a2203-152">Filter</span></span>

<span data-ttu-id="a2203-153">Mit einem Filter können Sie die angezeigten Informationen basierend auf den ausgewählten Kriterien reduzieren.</span><span class="sxs-lookup"><span data-stu-id="a2203-153">A filter allows you to reduce the information you see based on the criteria selected.</span></span> <span data-ttu-id="a2203-154">Sie können Filter mit Tabellen, Listen, Karten und anderen Komponenten hinzufügen, die Inhalte organisieren.</span><span class="sxs-lookup"><span data-stu-id="a2203-154">You can include filters with tables, lists, cards, and other components that organize content.</span></span>

### <a name="top-use-cases"></a><span data-ttu-id="a2203-155">Die am besten verwendeten Fälle</span><span class="sxs-lookup"><span data-stu-id="a2203-155">Top use cases</span></span>

<span data-ttu-id="a2203-156">Organisieren von Inhalten in:</span><span class="sxs-lookup"><span data-stu-id="a2203-156">Organizing content in:</span></span>

* <span data-ttu-id="a2203-157">Listen</span><span class="sxs-lookup"><span data-stu-id="a2203-157">Lists</span></span>
* <span data-ttu-id="a2203-158">Tabellen</span><span class="sxs-lookup"><span data-stu-id="a2203-158">Tables</span></span>
* <span data-ttu-id="a2203-159">Dashboards</span><span class="sxs-lookup"><span data-stu-id="a2203-159">Dashboards</span></span>
* <span data-ttu-id="a2203-160">Datenvisualisierung</span><span class="sxs-lookup"><span data-stu-id="a2203-160">Data visualization</span></span>

:::image type="content" source="../../assets/images/ui-templates/filter.png" alt-text="Beispiel zeigt eine Filtervorlage." border="false":::

## <a name="form"></a><span data-ttu-id="a2203-162">Formular</span><span class="sxs-lookup"><span data-stu-id="a2203-162">Form</span></span>

<span data-ttu-id="a2203-163">Formulare werden verwendet, um Benutzereingaben strukturiert zu erfassen, zu überprüfen und zu übermitteln.</span><span class="sxs-lookup"><span data-stu-id="a2203-163">Forms are used to collect, validate, and submit user input in a structured way.</span></span> <span data-ttu-id="a2203-164">Klare Bezeichnungen und logische Gruppierungen von Eingabefeldern sind für eine gute Benutzeroberfläche entscheidend.</span><span class="sxs-lookup"><span data-stu-id="a2203-164">Clear labeling and logical groupings of input fields are critical for a good user experience.</span></span>

### <a name="top-use-cases"></a><span data-ttu-id="a2203-165">Die am besten verwendeten Fälle</span><span class="sxs-lookup"><span data-stu-id="a2203-165">Top use cases</span></span>

* <span data-ttu-id="a2203-166">Anmelden</span><span class="sxs-lookup"><span data-stu-id="a2203-166">Sign in</span></span>
* <span data-ttu-id="a2203-167">Benutzerprofile</span><span class="sxs-lookup"><span data-stu-id="a2203-167">User profiles</span></span>
* <span data-ttu-id="a2203-168">Einstellungen</span><span class="sxs-lookup"><span data-stu-id="a2203-168">Settings</span></span>
* <span data-ttu-id="a2203-169">Benutzereingabesammlung</span><span class="sxs-lookup"><span data-stu-id="a2203-169">User input collection</span></span>

# <a name="desktop"></a>[<span data-ttu-id="a2203-170">Desktop</span><span class="sxs-lookup"><span data-stu-id="a2203-170">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/ui-templates/form.png" alt-text="Beispiel zeigt eine Formularbenutzeroberflächenvorlage auf dem Desktop." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="a2203-172">Mobil</span><span class="sxs-lookup"><span data-stu-id="a2203-172">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/ui-templates/mobile-form.png" alt-text="Beispiel zeigt eine Formularbenutzeroberflächenvorlage auf mobilen Geräten." border="false":::

---

## <a name="list"></a><span data-ttu-id="a2203-174">Liste</span><span class="sxs-lookup"><span data-stu-id="a2203-174">List</span></span>

<span data-ttu-id="a2203-175">Sie können eine Liste verwenden, um verwandte Elemente in einem scannierbaren Format anzeigen und Benutzern das Ausführen von Aktionen für eine gesamte Liste oder einzelne Elemente zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="a2203-175">You can use a list to display related items in a scannable format and allow users to take actions on an entire list or individual items.</span></span>

### <a name="top-use-cases"></a><span data-ttu-id="a2203-176">Die am besten verwendeten Fälle</span><span class="sxs-lookup"><span data-stu-id="a2203-176">Top use cases</span></span>

* <span data-ttu-id="a2203-177">Anzeigen von Daten</span><span class="sxs-lookup"><span data-stu-id="a2203-177">Display data</span></span>
* <span data-ttu-id="a2203-178">Kontextbezogene Aktionen für App-Inhalte</span><span class="sxs-lookup"><span data-stu-id="a2203-178">Contextual actions on app content</span></span>

# <a name="desktop"></a>[<span data-ttu-id="a2203-179">Desktop</span><span class="sxs-lookup"><span data-stu-id="a2203-179">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/ui-templates/list.png" alt-text="Beispiel zeigt eine Listenbenutzeroberflächenvorlage auf dem Desktop." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="a2203-181">Mobil</span><span class="sxs-lookup"><span data-stu-id="a2203-181">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/ui-templates/mobile-list.png" alt-text="Beispiel zeigt eine Listenbenutzeroberflächenvorlage auf mobilen Geräten." border="false":::

---

## <a name="sign-in"></a><span data-ttu-id="a2203-183">Anmelden</span><span class="sxs-lookup"><span data-stu-id="a2203-183">Sign in</span></span>

<span data-ttu-id="a2203-184">Sie können App-Anmeldeflüsse für unterschiedliche Teams und Identitätsanbieter entwerfen.</span><span class="sxs-lookup"><span data-stu-id="a2203-184">You can design app sign-in flows for different Teams contexts and identity providers.</span></span> <span data-ttu-id="a2203-185">Das folgende Beispiel enthält einmaliges Anmelden (Single Sign-On, SSO), das für die einfachste Authentifizierung empfohlen wird.</span><span class="sxs-lookup"><span data-stu-id="a2203-185">The following example includes single sign-on (SSO), which we recommend for the simplest authentication experience.</span></span>

### <a name="top-use-case"></a><span data-ttu-id="a2203-186">Top Use Case</span><span class="sxs-lookup"><span data-stu-id="a2203-186">Top use case</span></span>

* <span data-ttu-id="a2203-187">Authentifizieren von Benutzern</span><span class="sxs-lookup"><span data-stu-id="a2203-187">Authenticate users</span></span>

# <a name="desktop"></a>[<span data-ttu-id="a2203-188">Desktop</span><span class="sxs-lookup"><span data-stu-id="a2203-188">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/ui-templates/sign-in.png" alt-text="Beispiel zeigt eine Benutzeroberflächenvorlage für die Anmeldung auf dem Desktop." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="a2203-190">Mobil</span><span class="sxs-lookup"><span data-stu-id="a2203-190">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/ui-templates/mobile-sign-in.png" alt-text="Beispiel zeigt eine Benutzeroberflächenvorlage für die Anmeldung auf mobilen Geräten." border="false":::

---

## <a name="settings"></a><span data-ttu-id="a2203-192">Einstellungen</span><span class="sxs-lookup"><span data-stu-id="a2203-192">Settings</span></span>

<span data-ttu-id="a2203-193">Einstellungen bildschirmen können Benutzer ihre Einstellungen mit Ihrer App konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="a2203-193">Settings screens are where users can configure their preferences with your app.</span></span> <span data-ttu-id="a2203-194">(Hinweis: Einstellungen ist ein Container für [grundlegende Benutzeroberflächenkomponenten](~/concepts/design/design-teams-app-basic-ui-components.md).)</span><span class="sxs-lookup"><span data-stu-id="a2203-194">(Note: Settings is a container for [basic UI components](~/concepts/design/design-teams-app-basic-ui-components.md).)</span></span>

### <a name="top-use-case"></a><span data-ttu-id="a2203-195">Top Use Case</span><span class="sxs-lookup"><span data-stu-id="a2203-195">Top use case</span></span>

* <span data-ttu-id="a2203-196">Verwalten von App-Features</span><span class="sxs-lookup"><span data-stu-id="a2203-196">Manage app features</span></span>

:::image type="content" source="../../assets/images/ui-templates/settings.png" alt-text="Beispiel zeigt eine Einstellungsvorlage." border="false":::

## <a name="task-board"></a><span data-ttu-id="a2203-198">Task Board</span><span class="sxs-lookup"><span data-stu-id="a2203-198">Task board</span></span>

<span data-ttu-id="a2203-199">Ein Aufgabenboard, manchmal auch als Kanbanboard oder Schwimmstreifen bezeichnet, ist eine Sammlung von Karten, die häufig zum Nachverfolgen des Status von Arbeitselementen oder Tickets verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="a2203-199">A task board, sometimes called a kanban board or swim lanes, is a collection of cards often used to track the status of work items or tickets.</span></span> <span data-ttu-id="a2203-200">Es kann auch verwendet werden, um alle Arten von Inhalten in Kategorien zu sortieren.</span><span class="sxs-lookup"><span data-stu-id="a2203-200">It can also be used to sort any type of content into categories.</span></span> <span data-ttu-id="a2203-201">Sie können die Karten zwischen Spalten bearbeiten und verschieben.</span><span class="sxs-lookup"><span data-stu-id="a2203-201">You can edit and move the cards between columns.</span></span>

### <a name="top-use-cases"></a><span data-ttu-id="a2203-202">Die am besten verwendeten Fälle</span><span class="sxs-lookup"><span data-stu-id="a2203-202">Top use cases</span></span>

* <span data-ttu-id="a2203-203">Projektmanagement</span><span class="sxs-lookup"><span data-stu-id="a2203-203">Project management.</span></span> <span data-ttu-id="a2203-204">Zuweisen von Aufgaben und Nachverfolgungsstatus</span><span class="sxs-lookup"><span data-stu-id="a2203-204">Assigning tasks and tracking status</span></span>
* <span data-ttu-id="a2203-205">Brainstorming.</span><span class="sxs-lookup"><span data-stu-id="a2203-205">Brainstorming.</span></span> <span data-ttu-id="a2203-206">Hinzufügen von Ideen in verschiedenen Kategorien</span><span class="sxs-lookup"><span data-stu-id="a2203-206">Adding ideas in different categories</span></span>
* <span data-ttu-id="a2203-207">Sortierübungen.</span><span class="sxs-lookup"><span data-stu-id="a2203-207">Sorting exercises.</span></span> <span data-ttu-id="a2203-208">Organisieren aller Arten von Informationen in Buckets</span><span class="sxs-lookup"><span data-stu-id="a2203-208">Organizing any kind of information into buckets</span></span>

# <a name="desktop"></a>[<span data-ttu-id="a2203-209">Desktop</span><span class="sxs-lookup"><span data-stu-id="a2203-209">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/ui-templates/task-board.png" alt-text="Beispiel zeigt eine Benutzeroberflächenvorlage für Taskboards auf dem Desktop." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="a2203-211">Mobil</span><span class="sxs-lookup"><span data-stu-id="a2203-211">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/ui-templates/mobile-task-board.png" alt-text="Beispiel zeigt eine Benutzeroberflächenvorlage für task board auf mobilen Geräten." border="false":::

---

## <a name="wizard"></a><span data-ttu-id="a2203-213">Assistent</span><span class="sxs-lookup"><span data-stu-id="a2203-213">Wizard</span></span>

<span data-ttu-id="a2203-214">Ein Assistent führt einen Benutzer durch mehrere Bildschirme, um eine Aufgabe auszuführen (z. B. einen Einrichtungsprozess).</span><span class="sxs-lookup"><span data-stu-id="a2203-214">A wizard guides a user through several screens to complete a task (such as a setup process).</span></span>

### <a name="top-use-cases"></a><span data-ttu-id="a2203-215">Die am besten verwendeten Fälle</span><span class="sxs-lookup"><span data-stu-id="a2203-215">Top use cases</span></span>

* <span data-ttu-id="a2203-216">Setup</span><span class="sxs-lookup"><span data-stu-id="a2203-216">Setup</span></span>
* <span data-ttu-id="a2203-217">Onboarding</span><span class="sxs-lookup"><span data-stu-id="a2203-217">Onboarding</span></span>
* <span data-ttu-id="a2203-218">First-Run-Erfahrungen</span><span class="sxs-lookup"><span data-stu-id="a2203-218">First-run experiences</span></span>

# <a name="desktop"></a>[<span data-ttu-id="a2203-219">Desktop</span><span class="sxs-lookup"><span data-stu-id="a2203-219">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/ui-templates/wizard.png" alt-text="Beispiel zeigt eine Benutzeroberflächenvorlage des Assistenten auf dem Desktop." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="a2203-221">Mobil</span><span class="sxs-lookup"><span data-stu-id="a2203-221">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/ui-templates/mobile-wizard.png" alt-text="Beispiel zeigt eine Benutzeroberflächenvorlage des Assistenten auf Mobilgeräten." border="false":::

---
