---
title: Referenz zu Entwurfsrichtlinien
description: Beschreibt die Richtlinien für das Entwerfen einer persönlichen app.
keywords: Teams-Entwurfsrichtlinien – Referenzrahmen für persönliche apps
ms.openlocfilehash: f66691234149afa56a6753dd51379c9f2355318e
ms.sourcegitcommit: 61c93b22490526b1de87c0b14a3c7eb6e046caf6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/31/2020
ms.locfileid: "44455499"
---
# <a name="personal-apps"></a><span data-ttu-id="0b6b6-104">Persönliche Apps</span><span class="sxs-lookup"><span data-stu-id="0b6b6-104">Personal apps</span></span>

> [!NOTE]
> <span data-ttu-id="0b6b6-105">Die vollständige Unterstützung für Registerkarten auf mobilen Clients wird in Microsoft Teams unterstützt.</span><span class="sxs-lookup"><span data-stu-id="0b6b6-105">Full support for tabs on mobile clients is supported in Teams.</span></span> <span data-ttu-id="0b6b6-106">Beachten Sie beim Erstellen von Registerkarten für mobile Plattformen die [Anleitungen für Registerkarten auf mobilen Geräten](../../tabs/design/tabs-mobile.md) .</span><span class="sxs-lookup"><span data-stu-id="0b6b6-106">You should follow the [guidance for tabs on mobile](../../tabs/design/tabs-mobile.md) when creating tabs for mobile platforms.</span></span>

<span data-ttu-id="0b6b6-107">Eine persönliche APP ist eine Microsoft Teams-Anwendung mit einem persönlichen Bereich.</span><span class="sxs-lookup"><span data-stu-id="0b6b6-107">A personal app is a Teams application with a personal scope.</span></span>  <span data-ttu-id="0b6b6-108">Als App-Entwickler haben Sie die Möglichkeit, eine Version Ihrer APP bereitzustellen, die sich auf Interaktionen mit einem einzelnen Benutzer konzentriert.</span><span class="sxs-lookup"><span data-stu-id="0b6b6-108">As an app developer, you have the option to provide a version of your app that focuses on interactions with a single user.</span></span> <span data-ttu-id="0b6b6-109">Es kann sich um einen [Unterhaltungs bot](../../bots/what-are-bots.md) handeln, der sich mit einem Benutzer oder einer [persönlichen Registerkarte](../../tabs/what-are-tabs.md) , die ein eingebettetes Weberlebnis bereitstellt, in eins-zu-eins-Gesprächen beschäftigt.</span><span class="sxs-lookup"><span data-stu-id="0b6b6-109">It can be a [conversational bot](../../bots/what-are-bots.md) to engage in one-to-one conversations with a user or a [personal tab](../../tabs/what-are-tabs.md) providing an embedded web experience.</span></span> <span data-ttu-id="0b6b6-110">Mit persönlichen Apps können Benutzer Ihre ausgewählten Inhalte an einer Stelle anzeigen.</span><span class="sxs-lookup"><span data-stu-id="0b6b6-110">Personal apps enable users to view their select content in one place.</span></span> <span data-ttu-id="0b6b6-111">Im folgenden Screenshot ist Contoso eine persönliche App im Flyout für persönliche apps.</span><span class="sxs-lookup"><span data-stu-id="0b6b6-111">In the following screenshot, Contoso is a personal app in the personal app flyout.</span></span>

![Bild des Menüs "App-Überlauf"](~/assets/images/Personal-apps-App-flyout.png)

---

## <a name="guidelines"></a><span data-ttu-id="0b6b6-113">Anleitungen</span><span class="sxs-lookup"><span data-stu-id="0b6b6-113">Guidelines</span></span>

<span data-ttu-id="0b6b6-114">Eine persönliche app enthält normalerweise die folgenden Registerkarten:</span><span class="sxs-lookup"><span data-stu-id="0b6b6-114">A personal app typically contains the following tabs:</span></span>

### <a name="your-tab"></a><span data-ttu-id="0b6b6-115">Ihre Registerkarte</span><span class="sxs-lookup"><span data-stu-id="0b6b6-115">Your tab</span></span>

<span data-ttu-id="0b6b6-116">Hier werden Ihre Benutzer alle Ihre Inhalte sehen.</span><span class="sxs-lookup"><span data-stu-id="0b6b6-116">This is where your users will see all their stuff.</span></span> <span data-ttu-id="0b6b6-117">Es ist Ihr persönlicher Raum.</span><span class="sxs-lookup"><span data-stu-id="0b6b6-117">It's their personal space.</span></span> <span data-ttu-id="0b6b6-118">Die Registerkarte kann als Liste, als Raster, als Spalten oder als einzelne Leinwand angeordnet werden... Was auch immer am besten für Ihre Anwendung geeignet ist.</span><span class="sxs-lookup"><span data-stu-id="0b6b6-118">The tab can be arranged as a list, a grid, columns, or a single canvas...whatever works best for your application.</span></span> <span data-ttu-id="0b6b6-119">Weitere Informationen zum Entwerfen effektiver Registerkarten finden Sie unter: [Tabs Design](../../tabs/design/tabs.md).</span><span class="sxs-lookup"><span data-stu-id="0b6b6-119">For additional information on designing effective tabs see: [Tabs design](../../tabs/design/tabs.md).</span></span>

<span data-ttu-id="0b6b6-120">Da auf dieser Registerkarte Elemente aus mehreren Kanälen angezeigt werden können, sollte jedes Element ein eigenes Team, einen eigenen Kanal und eine eigene Registerkarte anzeigen, damit der Benutzer leicht erkennen kann, woher er stammt.</span><span class="sxs-lookup"><span data-stu-id="0b6b6-120">Since this tab can show items from multiple channels, each item should display its own team, channel, and tab so the user can easily see where it originated.</span></span>

![Registerkarte "persönliche Vorgänge"](~/assets/images/Personal-apps-MY-tab.png)

### <a name="recent"></a><span data-ttu-id="0b6b6-122">Neuesten</span><span class="sxs-lookup"><span data-stu-id="0b6b6-122">Recent</span></span>

<span data-ttu-id="0b6b6-123">Auf der Registerkarte " **zuletzt** verwendet" kann ein Benutzer alle zuletzt in Ihrer APP angezeigten Elemente durchsuchen.</span><span class="sxs-lookup"><span data-stu-id="0b6b6-123">The **Recent** tab lets someone browse everything they've recently viewed in your app.</span></span> <span data-ttu-id="0b6b6-124">Er wird in chronologischer Reihenfolge (von den meisten bis zuletzt jüngsten) aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="0b6b6-124">It's listed in chronological order (from most to least recent).</span></span> <span data-ttu-id="0b6b6-125">Durch Klicken auf ein Element in dieser Liste wird der Benutzer zum Kanal und zur Registerkarte des Elements navigiert.</span><span class="sxs-lookup"><span data-stu-id="0b6b6-125">Clicking on an item in this list will navigate the user to that item's channel and tab.</span></span>

![Registerkarte "zuletzt verwendet"](~/assets/images/Personal-apps-Recent-tab.png)

### <a name="all"></a><span data-ttu-id="0b6b6-127">Alle</span><span class="sxs-lookup"><span data-stu-id="0b6b6-127">All</span></span>

<span data-ttu-id="0b6b6-128">Hierbei handelt es sich um eine Liste aller Registerkarten in der Organisation der Person (auf die Sie Zugriff haben, auf jeden Fall).</span><span class="sxs-lookup"><span data-stu-id="0b6b6-128">This is a list of all your tabs in the person's organization (the ones they have access to, anyway).</span></span> <span data-ttu-id="0b6b6-129">Das heißt, Sie werden überall angezeigt, wo die APP verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="0b6b6-129">In other words, it shows them everywhere the app is being used.</span></span> <span data-ttu-id="0b6b6-130">Wie bei der **letzten** Registerkarte wird der Benutzer durch Auswählen eines Elements in der Liste direkt auf den entsprechenden Kanal und die entsprechende Registerkarte gebracht.</span><span class="sxs-lookup"><span data-stu-id="0b6b6-130">As with the **Recent** tab, selecting something in the list will bring the user straight to the relevant channel and tab.</span></span>

### <a name="bot"></a><span data-ttu-id="0b6b6-131">Bot</span><span class="sxs-lookup"><span data-stu-id="0b6b6-131">Bot</span></span>

<span data-ttu-id="0b6b6-132">Ein Bot ist nicht erforderlich, ist aber eine großartige Möglichkeit, direkt und privat mit ihren Benutzern zu kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="0b6b6-132">A bot isn't required, but it's a great way to communicate directly and privately with your users.</span></span> <span data-ttu-id="0b6b6-133">Die Benachrichtigung ist eine der wichtigsten Funktionen einer persönlichen APP, und welche bessere Möglichkeit gibt es, als bei der direkten Kommunikation zu Benachrichtigen?</span><span class="sxs-lookup"><span data-stu-id="0b6b6-133">Notification is one of the most important functions of a personal app, and what better way to notify than with direct communication?</span></span>

<span data-ttu-id="0b6b6-134">Bots liefern Nachrichten in Form von Karten, die spezifische Informationen (wie eine Warnung, dass neue Inhalte verfügbar sind) oder umfassende Updates (wie eine tägliche to-do-Liste) bereitstellen können.</span><span class="sxs-lookup"><span data-stu-id="0b6b6-134">Bots deliver messages in the form of cards, which can provide specific information (like an alert that new content is available) or broad updates (like a daily to-do list).</span></span> <span data-ttu-id="0b6b6-135">Weitere Informationen zum Entwerfen effektiver Bots finden Sie unter: [bot-Design](../../bots/design/bots.md).</span><span class="sxs-lookup"><span data-stu-id="0b6b6-135">For additional information on designing effective bots see: [Bot design](../../bots/design/bots.md).</span></span>

![Bot-Begrüßung](~/assets/images/Personal-apps-Bot.png)

### <a name="help-and-settings"></a><span data-ttu-id="0b6b6-137">Hilfe und Einstellungen</span><span class="sxs-lookup"><span data-stu-id="0b6b6-137">Help and Settings</span></span>

<span data-ttu-id="0b6b6-138">Mithilfe von Inhalten können Benutzer die Nuancen ihrer App ermitteln.</span><span class="sxs-lookup"><span data-stu-id="0b6b6-138">Help content enables users to discover the nuances of your app.</span></span> <span data-ttu-id="0b6b6-139">Fügen Sie eine Registerkarte **Einstellungen** hinzu, damit Sie Sie weiter anpassen können.</span><span class="sxs-lookup"><span data-stu-id="0b6b6-139">Add a **Settings** tab to give them the ability to further customize it.</span></span>

### <a name="about"></a><span data-ttu-id="0b6b6-140">Info</span><span class="sxs-lookup"><span data-stu-id="0b6b6-140">About</span></span>

<span data-ttu-id="0b6b6-141">Schließen Sie die Registerkarte **Info** ein, um Informationen wie Versionsnummer, Funktionen, Datenschutz und Berechtigungs Links bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="0b6b6-141">Include an **About** tab to provide information like version number, capabilities, privacy, and permissions links.</span></span>

## <a name="best-practices"></a><span data-ttu-id="0b6b6-142">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="0b6b6-142">Best practices</span></span>

### <a name="communicate-directly-with-your-users"></a><span data-ttu-id="0b6b6-143">Direkte Kommunikation mit ihren Benutzern</span><span class="sxs-lookup"><span data-stu-id="0b6b6-143">Communicate directly with your users</span></span>

<span data-ttu-id="0b6b6-144">Verwenden Sie einen bot, um Benutzer über Änderungen und neue Features zu informieren.</span><span class="sxs-lookup"><span data-stu-id="0b6b6-144">Use a bot to notify users of changes and new features.</span></span>

### <a name="customize-your-tabs"></a><span data-ttu-id="0b6b6-145">Passen Sie Ihre Registerkarten an...</span><span class="sxs-lookup"><span data-stu-id="0b6b6-145">Customize your tabs...</span></span>

<span data-ttu-id="0b6b6-146">Fühlen Sie sich frei, weitere Registerkarten hinzuzufügen, die Ihre Benutzer bei der Ausführung bestimmter Aufgaben unterstützen sollen.</span><span class="sxs-lookup"><span data-stu-id="0b6b6-146">Feel free to add other tabs that will help your users accomplish specific tasks.</span></span>

### <a name="and-make-them-relevant-to-every-user"></a><span data-ttu-id="0b6b6-147">... und Sie für jeden Benutzer relevant zu machen.</span><span class="sxs-lookup"><span data-stu-id="0b6b6-147">...and make them relevant to every user</span></span>

<span data-ttu-id="0b6b6-148">Jede Registerkarte, die Sie in Ihrem App-Manifest deklarieren, ist für alle Benutzer sichtbar.</span><span class="sxs-lookup"><span data-stu-id="0b6b6-148">Every tab you declare in your app manifest will be visible to all users.</span></span> <span data-ttu-id="0b6b6-149">Wenn es sich bei Ihrer persönlichen App beispielsweise um ein Spesen abrechnungstool handelt, das sowohl von Managern als auch von Mitarbeitern verwendet wird, sollte eine **Genehmigungs** Registerkarte Inhalte bereitstellen, die für beide Rollen sinnvoll sind.</span><span class="sxs-lookup"><span data-stu-id="0b6b6-149">For example, if your personal app is an expense reporting tool that is used by both managers and employees, an **Approval** tab should provide content that is meaningful to both roles.</span></span>
