---
title: Referenz zu Entwurfsrichtlinien
description: Beschreibt die Richtlinien für das Entwerfen einer persönlichen app.
keywords: Teams-Entwurfsrichtlinien – Referenzrahmen für persönliche apps
ms.openlocfilehash: 6a07b618d78a3ad79850713052c88ef178c1ecc1
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674154"
---
# <a name="personal-apps"></a><span data-ttu-id="881d9-104">Persönliche apps</span><span class="sxs-lookup"><span data-stu-id="881d9-104">Personal apps</span></span>

> [!Important]
> <span data-ttu-id="881d9-105">Die vollständige Unterstützung für Registerkarten auf mobilen Clients wird in Kürze verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="881d9-105">Full support for tabs on mobile clients is coming soon.</span></span> <span data-ttu-id="881d9-106">Zur Vorbereitung auf diese Änderung sollten Sie die [Anleitungen für Registerkarten auf mobilen Geräten](~/tabs/design/tabs-mobile.md) beim Erstellen Ihrer Registerkarten befolgten.</span><span class="sxs-lookup"><span data-stu-id="881d9-106">To prepare for this change you should follow the [guidance for tabs on mobile](~/tabs/design/tabs-mobile.md) when creating your tabs.</span></span> <span data-ttu-id="881d9-107">Persönliche Apps (statische Registerkarten) sind derzeit in der [Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md)verfügbar.</span><span class="sxs-lookup"><span data-stu-id="881d9-107">Personal apps (static tabs) are currently available in [developer preview](~/resources/dev-preview/developer-preview-intro.md).</span></span>
>
> <span data-ttu-id="881d9-108">Wenn die vollständige Unterstützung für Tabs freigegeben wird:</span><span class="sxs-lookup"><span data-stu-id="881d9-108">When full support for tabs is released:</span></span>
>
> * <span data-ttu-id="881d9-109">Alle Registerkarten sind auf mobilen Geräten immer verfügbar.</span><span class="sxs-lookup"><span data-stu-id="881d9-109">All tabs will always be available on mobile</span></span>
> * <span data-ttu-id="881d9-110">Ihr `contentUrl` **wird in den Mobile Teams-Client geladen**.</span><span class="sxs-lookup"><span data-stu-id="881d9-110">Your `contentUrl` **will be loaded in the mobile Teams client**.</span></span>
> * <span data-ttu-id="881d9-111">Bei Kanälen/Gruppenregisterkarten können Benutzer ihre Registerkarte weiterhin in einem separaten Browser öffnen `websiteUrl`, jedoch werden Sie `contentUrl` zuerst geladen.</span><span class="sxs-lookup"><span data-stu-id="881d9-111">For channel/group tabs, users can still open your tab in a separate browser via your `websiteUrl`, however your `contentUrl` will be loaded first.</span></span>

<span data-ttu-id="881d9-112">Eine persönliche APP ist eine APP mit einem persönlichen Bereich.</span><span class="sxs-lookup"><span data-stu-id="881d9-112">A personal app is an app with a personal scope.</span></span> <span data-ttu-id="881d9-113">Als App-Entwickler haben Sie die Möglichkeit, eine Version Ihrer APP bereitzustellen, die für den jeweiligen Benutzer erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="881d9-113">As an app developer, you have the option to provide a version of your app that is built for the individual user.</span></span> <span data-ttu-id="881d9-114">In dieser Version ist die Sammlung von Registerkarten (und der bot, wenn Sie einen enthalten haben) für die Person konzipiert.</span><span class="sxs-lookup"><span data-stu-id="881d9-114">In this version, the collection of tabs (and the bot, if you've included one), are designed for the person.</span></span> <span data-ttu-id="881d9-115">Auf diese Weise können Sie eine 1:1-Interaktion mit ihren Benutzern erstellen.</span><span class="sxs-lookup"><span data-stu-id="881d9-115">This way, you're able to create a one-on-one interaction with your users.</span></span>

<span data-ttu-id="881d9-116">Eine persönliche APP ist, wo jemand alles, was Ihnen gehört, und alle Elemente, die Sie zuletzt in der App angezeigt haben, angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="881d9-116">A personal app is where someone can see everything that's theirs, and all the items they've recently viewed in the app.</span></span> <span data-ttu-id="881d9-117">Alles wird an einer Stelle platziert.</span><span class="sxs-lookup"><span data-stu-id="881d9-117">It puts everything in one place.</span></span> <span data-ttu-id="881d9-118">Im folgenden Screenshot ist Contoso eine persönliche App im Flyout für persönliche apps.</span><span class="sxs-lookup"><span data-stu-id="881d9-118">In the following screenshot, Contoso is a personal app in the personal app flyout.</span></span>

![Bild des Menüs "App-Überlauf"](~/assets/images/Personal-apps-App-flyout.png)

---

## <a name="guidelines"></a><span data-ttu-id="881d9-120">Anleitungen</span><span class="sxs-lookup"><span data-stu-id="881d9-120">Guidelines</span></span>

<span data-ttu-id="881d9-121">Eine persönliche app enthält normalerweise die folgenden Registerkarten:</span><span class="sxs-lookup"><span data-stu-id="881d9-121">A personal app typically contains the following tabs:</span></span>

### <a name="your-tab"></a><span data-ttu-id="881d9-122">Ihre Registerkarte</span><span class="sxs-lookup"><span data-stu-id="881d9-122">Your tab</span></span>

<span data-ttu-id="881d9-123">Hier werden Ihre Benutzer alle Ihre Inhalte sehen.</span><span class="sxs-lookup"><span data-stu-id="881d9-123">This is where your users will see all their stuff.</span></span> <span data-ttu-id="881d9-124">Es ist Ihr persönlicher Raum.</span><span class="sxs-lookup"><span data-stu-id="881d9-124">It's their personal space.</span></span> <span data-ttu-id="881d9-125">Die Registerkarte kann als Liste, als Raster, als Spalten oder als einzelne Leinwand angeordnet werden... Was auch immer am besten für Ihre Anwendung geeignet ist.</span><span class="sxs-lookup"><span data-stu-id="881d9-125">The tab can be arranged as a list, a grid, columns, or a single canvas...whatever works best for your application.</span></span> <span data-ttu-id="881d9-126">Weitere Informationen zum Entwerfen effektiver Registerkarten finden Sie unter: [Tabs Design (~/Tabs/Design/Tabs.MD).</span><span class="sxs-lookup"><span data-stu-id="881d9-126">For additional information on designing effective tabs see: [Tabs design(~/tabs/design/tabs.md).</span></span>

<span data-ttu-id="881d9-127">Da auf dieser Registerkarte Elemente aus mehreren Kanälen angezeigt werden können, sollte jedes Element ein eigenes Team, einen eigenen Kanal und eine eigene Registerkarte anzeigen, damit der Benutzer leicht erkennen kann, woher er stammt.</span><span class="sxs-lookup"><span data-stu-id="881d9-127">Since this tab can show items from multiple channels, each item should display its own team, channel, and tab so the user can easily see where it originated.</span></span>

![Registerkarte "persönliche Vorgänge"](~/assets/images/Personal-apps-MY-tab.png)

### <a name="recent"></a><span data-ttu-id="881d9-129">Neuesten</span><span class="sxs-lookup"><span data-stu-id="881d9-129">Recent</span></span>

<span data-ttu-id="881d9-130">Auf der Registerkarte " **zuletzt** verwendet" kann ein Benutzer alle zuletzt in Ihrer APP angezeigten Elemente durchsuchen.</span><span class="sxs-lookup"><span data-stu-id="881d9-130">The **Recent** tab lets someone browse everything they've recently viewed in your app.</span></span> <span data-ttu-id="881d9-131">Er wird in chronologischer Reihenfolge (von den meisten bis zuletzt jüngsten) aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="881d9-131">It's listed in chronological order (from most to least recent).</span></span> <span data-ttu-id="881d9-132">Durch Klicken auf ein Element in dieser Liste wird der Benutzer zum Kanal und zur Registerkarte des Elements navigiert.</span><span class="sxs-lookup"><span data-stu-id="881d9-132">Clicking on an item in this list will navigate the user to that item's channel and tab.</span></span>

![Registerkarte "zuletzt verwendet"](~/assets/images/Personal-apps-Recent-tab.png)

### <a name="all"></a><span data-ttu-id="881d9-134">Alle</span><span class="sxs-lookup"><span data-stu-id="881d9-134">All</span></span>

<span data-ttu-id="881d9-135">Hierbei handelt es sich um eine Liste aller Registerkarten in der Organisation der Person (auf die Sie Zugriff haben, auf jeden Fall).</span><span class="sxs-lookup"><span data-stu-id="881d9-135">This is a list of all your tabs in the person's organization (the ones they have access to, anyway).</span></span> <span data-ttu-id="881d9-136">Das heißt, Sie werden überall angezeigt, wo die APP verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="881d9-136">In other words, it shows them everywhere the app is being used.</span></span> <span data-ttu-id="881d9-137">Wie bei der **letzten** Registerkarte wird der Benutzer durch Auswählen eines Elements in der Liste direkt auf den entsprechenden Kanal und die entsprechende Registerkarte gebracht.</span><span class="sxs-lookup"><span data-stu-id="881d9-137">As with the **Recent** tab, selecting something in the list will bring the user straight to the relevant channel and tab.</span></span>

### <a name="bot"></a><span data-ttu-id="881d9-138">Bot</span><span class="sxs-lookup"><span data-stu-id="881d9-138">Bot</span></span>

<span data-ttu-id="881d9-139">Ein Bot ist nicht erforderlich, ist aber eine großartige Möglichkeit, direkt und privat mit ihren Benutzern zu kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="881d9-139">A bot isn't required, but it's a great way to communicate directly and privately with your users.</span></span> <span data-ttu-id="881d9-140">Die Benachrichtigung ist eine der wichtigsten Funktionen einer persönlichen APP, und welche bessere Möglichkeit gibt es, als bei der direkten Kommunikation zu Benachrichtigen?</span><span class="sxs-lookup"><span data-stu-id="881d9-140">Notification is one of the most important functions of a personal app, and what better way to notify than with direct communication?</span></span>

<span data-ttu-id="881d9-141">Bots liefern Nachrichten in Form von Karten, die spezifische Informationen (wie eine Warnung, dass neue Inhalte verfügbar sind) oder umfassende Updates (wie eine tägliche to-do-Liste) bereitstellen können.</span><span class="sxs-lookup"><span data-stu-id="881d9-141">Bots deliver messages in the form of cards, which can provide specific information (like an alert that new content is available) or broad updates (like a daily to-do list).</span></span> <span data-ttu-id="881d9-142">Weitere Informationen zum Entwerfen effektiver Bots finden Sie unter: [Bot Design (~/Bots/Design/Bots.MD).</span><span class="sxs-lookup"><span data-stu-id="881d9-142">For additional information on designing effective bots see: [Bot design(~/bots/design/bots.md).</span></span>

![Bot-Begrüßung](~/assets/images/Personal-apps-Bot.png)

### <a name="help-and-settings"></a><span data-ttu-id="881d9-144">Hilfe und Einstellungen</span><span class="sxs-lookup"><span data-stu-id="881d9-144">Help and Settings</span></span>

<span data-ttu-id="881d9-145">Mithilfe von Inhalten können Benutzer die Nuancen ihrer App ermitteln.</span><span class="sxs-lookup"><span data-stu-id="881d9-145">Help content enables users to discover the nuances of your app.</span></span> <span data-ttu-id="881d9-146">Fügen Sie eine Registerkarte **Einstellungen** hinzu, damit Sie Sie weiter anpassen können.</span><span class="sxs-lookup"><span data-stu-id="881d9-146">Add a **Settings** tab to give them the ability to further customize it.</span></span>

### <a name="about"></a><span data-ttu-id="881d9-147">Info</span><span class="sxs-lookup"><span data-stu-id="881d9-147">About</span></span>

<span data-ttu-id="881d9-148">Schließen Sie die Registerkarte **Info** ein, um Informationen wie Versionsnummer, Funktionen, Datenschutz und Berechtigungs Links bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="881d9-148">Include an **About** tab to provide information like version number, capabilities, privacy, and permissions links.</span></span>

## <a name="best-practices"></a><span data-ttu-id="881d9-149">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="881d9-149">Best practices</span></span>

### <a name="communicate-directly-with-your-users"></a><span data-ttu-id="881d9-150">Direkte Kommunikation mit ihren Benutzern</span><span class="sxs-lookup"><span data-stu-id="881d9-150">Communicate directly with your users</span></span>

<span data-ttu-id="881d9-151">Verwenden Sie einen bot, um Benutzer über Änderungen und neue Features zu informieren.</span><span class="sxs-lookup"><span data-stu-id="881d9-151">Use a bot to notify users of changes and new features.</span></span>

### <a name="customize-your-tabs"></a><span data-ttu-id="881d9-152">Passen Sie Ihre Registerkarten an...</span><span class="sxs-lookup"><span data-stu-id="881d9-152">Customize your tabs...</span></span>

<span data-ttu-id="881d9-153">Fühlen Sie sich frei, weitere Registerkarten hinzuzufügen, die Ihre Benutzer bei der Ausführung bestimmter Aufgaben unterstützen sollen.</span><span class="sxs-lookup"><span data-stu-id="881d9-153">Feel free to add other tabs that will help your users accomplish specific tasks.</span></span>

### <a name="and-make-them-relevant-to-every-user"></a><span data-ttu-id="881d9-154">... und Sie für jeden Benutzer relevant zu machen.</span><span class="sxs-lookup"><span data-stu-id="881d9-154">...and make them relevant to every user</span></span>

<span data-ttu-id="881d9-155">Jede Registerkarte, die Sie in Ihrem App-Manifest deklarieren, ist für alle Benutzer sichtbar.</span><span class="sxs-lookup"><span data-stu-id="881d9-155">Every tab you declare in your app manifest will be visible to all users.</span></span> <span data-ttu-id="881d9-156">Wenn es sich bei Ihrer persönlichen App beispielsweise um ein Spesen abrechnungstool handelt, das sowohl von Managern als auch von Mitarbeitern verwendet wird, sollte eine **Genehmigungs** Registerkarte Inhalte bereitstellen, die für beide Rollen sinnvoll sind.</span><span class="sxs-lookup"><span data-stu-id="881d9-156">For example, if your personal app is an expense reporting tool that is used by both managers and employees, an **Approval** tab should provide content that is meaningful to both roles.</span></span>
