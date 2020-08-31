---
title: Was sind Messaging-Erweiterungen?
author: clearab
description: Eine Übersicht über Messaging-Erweiterungen auf der Microsoft Teams-Plattform
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 3e80c965fb8cb2c4da2af6f6bf0709e7c8bd1d88
ms.sourcegitcommit: 9fbc701a9a039ecdc360aefbe86df52b9c3593f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/12/2020
ms.locfileid: "46652000"
---
# <a name="what-are-messaging-extensions"></a><span data-ttu-id="4e772-103">Was sind Messaging-Erweiterungen?</span><span class="sxs-lookup"><span data-stu-id="4e772-103">What are messaging extensions?</span></span>

<span data-ttu-id="4e772-104">Messaging-Erweiterungen ermöglichen Benutzern die Interaktion mit Ihrem Webdienst über Schaltflächen und Formulare im Microsoft Teams-Client.</span><span class="sxs-lookup"><span data-stu-id="4e772-104">Messaging extensions allow users to interact with your web service through buttons and forms in the Microsoft Teams client.</span></span> <span data-ttu-id="4e772-105">Sie können Aktionen in einem externen System aus dem Bereich zum Verfassen von Nachrichten, dem Befehlsfeld oder direkt aus einer Nachricht durchsuchen oder initiieren.</span><span class="sxs-lookup"><span data-stu-id="4e772-105">They can search or initiate actions in an external system from the compose message area, the command box, or directly from a message.</span></span> <span data-ttu-id="4e772-106">Sie können dann die Ergebnisse dieser Interaktion an den Microsoft Teams-Client zurücksenden, normalerweise in Form einer reich formatierten Karte.</span><span class="sxs-lookup"><span data-stu-id="4e772-106">You can then send the results of that interaction back to the Microsoft Teams client, typically in the form of a richly formatted card.</span></span>

<span data-ttu-id="4e772-107">Der folgende Screenshot zeigt die Orte, von denen aus Messaging Erweiterungen aufgerufen werden können.</span><span class="sxs-lookup"><span data-stu-id="4e772-107">The screenshot below shows the locations where messaging extensions can be invoked from.</span></span>

![Speicherorte für Messaging Erweiterungs Aufrufe](~/assets/images/messaging-extension-invoke-locations.png)

## <a name="user-scenarios"></a><span data-ttu-id="4e772-109">Benutzerszenarien</span><span class="sxs-lookup"><span data-stu-id="4e772-109">User scenarios</span></span>

<span data-ttu-id="4e772-110">**Szenario:** Ich benötige ein externes System, um etwas zu tun, und ich möchte, dass das Ergebnis der Aktion an meine Unterhaltung zurückgesendet wird. </span><span class="sxs-lookup"><span data-stu-id="4e772-110">**Scenario:** I need some external system to do something and I want the result of the action to be sent back to my conversation.</span></span>\
<span data-ttu-id="4e772-111">**Beispiel:** Reservieren Sie eine Ressource, und lassen Sie den Kanal wissen, für welchen Tag/welche Zeit Sie ihn reserviert haben.</span><span class="sxs-lookup"><span data-stu-id="4e772-111">**Example:** Reserve a resource and let the channel know what day/time you reserved it for.</span></span>

<span data-ttu-id="4e772-112">**Szenario:** Ich muss etwas in einem externen System finden, und ich möchte die Ergebnisse mit meiner Unterhaltung teilen. </span><span class="sxs-lookup"><span data-stu-id="4e772-112">**Scenario:** I need to find something in an external system, and I want to share the results with my conversation.</span></span>\
<span data-ttu-id="4e772-113">**Beispiel:**  Suchen Sie in Azure DevOps nach einer Arbeitsaufgabe, und teilen Sie Sie mit der Gruppe als Adaptive Karte.</span><span class="sxs-lookup"><span data-stu-id="4e772-113">**Example:**  Search for a work item in Azure DevOps, and share it with the group as an adaptive card.</span></span>

<span data-ttu-id="4e772-114">**Szenario:** Ich muss eine komplexe Aufgabe mit mehreren Schritten (oder vielen Informationen) in einem externen System ausführen, und die Ergebnisse sollten für eine Unterhaltung freigegeben werden. </span><span class="sxs-lookup"><span data-stu-id="4e772-114">**Scenario:** I need to complete a complex task involving multiple steps (or lots of information) in an external system, and the results should be shared with a conversation.</span></span>\
<span data-ttu-id="4e772-115">**Beispiel:** Erstellen Sie einen Fehler in Ihrem Tracking System basierend auf einer Microsoft Teams-Nachricht, weisen Sie diesen Fehler Bob zu, und senden Sie dann eine Karte an den Unterhaltungsthread mit den Details des Fehlers.</span><span class="sxs-lookup"><span data-stu-id="4e772-115">**Example:** Create a bug in your tracking system based on a Teams message, assign that bug to Bob, then send a card to the conversation thread with the bug's details.</span></span>

## <a name="how-do-messaging-extensions-work"></a><span data-ttu-id="4e772-116">Wie funktionieren Messaging-Erweiterungen?</span><span class="sxs-lookup"><span data-stu-id="4e772-116">How do messaging extensions work?</span></span>

<span data-ttu-id="4e772-117">Eine Messaging Erweiterung besteht aus einem Webdienst, den Sie hosten, und dem App-Manifest, das definiert, wo Ihr Webdienst aus dem Microsoft Teams-Client aufgerufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="4e772-117">A messaging extension consists of a web service you host and your app manifest which defines where your web service can be invoked from in the Microsoft Teams client.</span></span> <span data-ttu-id="4e772-118">Sie nutzen das Messaging-Schema und das sichere Kommunikationsprotokoll des Bot-Frameworks, so dass Sie Ihren Webdienst auch als Bot im Bot-Framework registrieren müssen.</span><span class="sxs-lookup"><span data-stu-id="4e772-118">They take advantage of the Bot Framework's messaging schema and secure communication protocol, so you'll also need to register your web service as a bot in the Bot Framework.</span></span> <span data-ttu-id="4e772-119">Sie können den Webdienst zwar vollständig manuell erstellen, aber es wird empfohlen, dass Sie das [bot Framework SDK](https://github.com/microsoft/botframework) nutzen, um das Arbeiten mit dem Protokoll zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="4e772-119">Although you can create your web service completely by hand, we recommend you take advantage of the [Bot Framework SDK](https://github.com/microsoft/botframework) to make working with the protocol simpler.</span></span>

<span data-ttu-id="4e772-120">Im App-Manifest für Ihre Microsoft Teams-app definieren Sie eine einzelne Messaging Erweiterung mit bis zu zehn unterschiedlichen Befehlen.</span><span class="sxs-lookup"><span data-stu-id="4e772-120">In the app manifest for your Microsoft Teams app you'll define a single messaging extension with up to ten different commands.</span></span> <span data-ttu-id="4e772-121">Jeder Befehl definiert einen Typ (Aktion oder Suche) und die Speicherorte im Client, aus dem er aufgerufen werden kann (Verfassen des Nachrichtenbereichs, der Befehlsleiste und/oder der Nachricht).</span><span class="sxs-lookup"><span data-stu-id="4e772-121">Each command defines a type (action or search), and the locations in the client it can be invoked from (compose message area, command bar, and/or message).</span></span> <span data-ttu-id="4e772-122">Nachdem der Webdienst aufgerufen wurde, erhält er eine HTTPS-Nachricht mit einer JSON-Nutzlast einschließlich aller relevanten Informationen.</span><span class="sxs-lookup"><span data-stu-id="4e772-122">Once invoked, your web service will receive an HTTPS message with a JSON payload including all the relevant information.</span></span> <span data-ttu-id="4e772-123">Sie Antworten mit einer JSON-Nutzlast, sodass der Microsoft Teams-Client wissen kann, welche Interaktion als nächstes aktiviert werden soll.</span><span class="sxs-lookup"><span data-stu-id="4e772-123">You'll respond with a JSON payload, letting the Teams client know what interaction to enable next.</span></span>

## <a name="types-of-messaging-extensions"></a><span data-ttu-id="4e772-124">Typen von Messaging Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="4e772-124">Types of messaging extensions</span></span>

<span data-ttu-id="4e772-125">Der Typ des Messaging Erweiterungs Befehls definiert die Benutzeroberflächenelemente und Interaktions Flüsse, die Ihrem Webdienst zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="4e772-125">The type of messaging extension command defines the UI elements and interaction flows available to your web service.</span></span> <span data-ttu-id="4e772-126">Einige Interaktionen, wie Authentifizierung und Konfiguration, stehen für beide Befehlstypen zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="4e772-126">Some interactions, like authentication and configuration, are available for both types of commands.</span></span>

### <a name="action-commands"></a><span data-ttu-id="4e772-127">Aktionsbefehle</span><span class="sxs-lookup"><span data-stu-id="4e772-127">Action commands</span></span>

<span data-ttu-id="4e772-128">Mit Aktions Befehlen können Sie Ihren Benutzern ein modales Popup-Fenster zum Erfassen oder Anzeigen von Informationen präsentieren.</span><span class="sxs-lookup"><span data-stu-id="4e772-128">Action commands allow you to present your users with a modal popup to collect or display information.</span></span> <span data-ttu-id="4e772-129">Wenn Sie das Formular übermitteln, kann Ihr Webdienst Antworten, indem er eine Nachricht direkt in die Unterhaltung einfügt, oder indem er eine Nachricht in den Bereich zum Verfassen von Nachrichten einfügt und es dem Benutzer ermöglicht, die Nachricht zu übermitteln.</span><span class="sxs-lookup"><span data-stu-id="4e772-129">When they submit the form, your web service can respond by inserting a message into the conversation directly, or by inserting a message into the compose message area and allowing the user to submit the message.</span></span> <span data-ttu-id="4e772-130">Sie können sogar mehrere Formulare für komplexere Workflows miteinander verketten.</span><span class="sxs-lookup"><span data-stu-id="4e772-130">You can even chain multiple forms together for more complex workflows.</span></span>

<span data-ttu-id="4e772-131">Sie können aus dem Bereich zum Verfassen von Nachrichten, dem Befehlsfeld oder aus einer Nachricht ausgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="4e772-131">They can be triggered from the compose message area, the command box, or from a message.</span></span> <span data-ttu-id="4e772-132">Wenn Sie aus einer Nachricht aufgerufen wird, enthält die anfängliche JSON-Nutzlast, die an Ihren bot gesendet wird, die gesamte Nachricht, von der Sie aufgerufen wurde.</span><span class="sxs-lookup"><span data-stu-id="4e772-132">When invoked from a message, the initial JSON payload sent to your bot will include the entire message it was invoked from.</span></span>

![Befehls Aufgabenmodul für Messaging Erweiterungsaktionen](~/assets/images/task-module.png)

### <a name="search-commands"></a><span data-ttu-id="4e772-134">Suchbefehle</span><span class="sxs-lookup"><span data-stu-id="4e772-134">Search commands</span></span>

<span data-ttu-id="4e772-135">Suchbefehle ermöglichen es Ihren Benutzern, ein externes System nach Informationen zu durchsuchen (entweder manuell über ein Suchfeld oder durch Einfügen eines Links zu einer überwachten Domäne in den Nachrichtenbereich „Verfassen“) und anschließend die Ergebnisse der Suche in eine Nachricht einzufügen.</span><span class="sxs-lookup"><span data-stu-id="4e772-135">Search commands allow your users to search an external system for information (either manually through a search box, or by pasting a link to a monitored domain into the compose message area), then insert the results of the search into a message.</span></span> <span data-ttu-id="4e772-136">Im einfachsten Suchbefehlsfluss enthält die anfängliche „invoke“-Nachricht die vom Benutzer übermittelte Suchzeichenfolge.</span><span class="sxs-lookup"><span data-stu-id="4e772-136">In the most basic search command flow, the initial invoke message will include the search string the user submitted.</span></span> <span data-ttu-id="4e772-137">Sie antworten mit einer Liste von Karten und Kartenvorschauen.</span><span class="sxs-lookup"><span data-stu-id="4e772-137">You'll respond with a list of cards and card previews.</span></span> <span data-ttu-id="4e772-138">Der Microsoft Teams-Client rendert die Kartenvorschau in einer Liste, aus der der Endbenutzer auswählen kann.</span><span class="sxs-lookup"><span data-stu-id="4e772-138">The Teams client will render the card previews in a list for the end user to select from.</span></span> <span data-ttu-id="4e772-139">Wenn der Benutzer eine Karte auswählt, wird sie in voller Größe in den Nachrichtenbereich „Verfassen“ eingefügt.</span><span class="sxs-lookup"><span data-stu-id="4e772-139">When the user selects a card, the full-size card will be inserted into the compose message area.</span></span>

<span data-ttu-id="4e772-140">Sie können aus dem Nachrichtenbereich "Verfassen" oder aus dem Befehlsfeld ausgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="4e772-140">They can be triggered from the compose message area or the command box.</span></span> <span data-ttu-id="4e772-141">Im Gegensatz zu Aktions Befehlen können Sie nicht aus einer Nachricht ausgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="4e772-141">Unlike action commands, they cannot be triggered from a message.</span></span>

![Suchbefehl für Messaging Erweiterung](~/assets/images/search-extension.png)

### <a name="link-unfurling"></a><span data-ttu-id="4e772-143">Entfalten von Links</span><span class="sxs-lookup"><span data-stu-id="4e772-143">Link unfurling</span></span>

<span data-ttu-id="4e772-144">Sie können den Dienst auch aufrufen, wenn eine URL im Bereich zum Verfassen von Nachrichten eingefügt wird.</span><span class="sxs-lookup"><span data-stu-id="4e772-144">You also can invoke your service when a URL is pasted in the compose message area.</span></span> <span data-ttu-id="4e772-145">Mit dieser Funktion, die als **Link-Entfaltung**bezeichnet wird, können Sie abonnieren, um einen Aufruf zu erhalten, wenn URLs, die eine bestimmte Domäne enthalten, in den Bereich zum Verfassen von Nachrichten eingefügt werden.</span><span class="sxs-lookup"><span data-stu-id="4e772-145">This functionality, known as **link unfurling**, allows you to subscribe to receive an invoke when URLs containing a particular domain are pasted into the compose message area.</span></span> <span data-ttu-id="4e772-146">Ihr Webdienst kann die URL in eine detaillierte Karte "aufteilen" und bietet mehr Informationen als die standardmäßige Website-Vorschau Karte.</span><span class="sxs-lookup"><span data-stu-id="4e772-146">Your web service can "unfurl" the URL into a detailed card, providing more information than the standard website preview card.</span></span> <span data-ttu-id="4e772-147">Sie können sogar Schaltflächen hinzufügen, damit Benutzeraktionen ausführen können, ohne Teams zu verlassen.</span><span class="sxs-lookup"><span data-stu-id="4e772-147">You can even add buttons so users can take action without leaving Teams.</span></span>

## <a name="get-started"></a><span data-ttu-id="4e772-148">Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="4e772-148">Get started</span></span>

<span data-ttu-id="4e772-149">Können Sie mit dem Erstellen beginnen?</span><span class="sxs-lookup"><span data-stu-id="4e772-149">Ready to get started building?</span></span> <span data-ttu-id="4e772-150">Versuchen Sie es mit einem unserer Schnellstarts:</span><span class="sxs-lookup"><span data-stu-id="4e772-150">Try one of our quickstarts:</span></span>

### <a name="c"></a><span data-ttu-id="4e772-151">C#</span><span class="sxs-lookup"><span data-stu-id="4e772-151">C#</span></span>
* [<span data-ttu-id="4e772-152">Messaging-Erweiterung mit Aktions basierten Befehlen</span><span class="sxs-lookup"><span data-stu-id="4e772-152">Messaging extension with action-based commands</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action)
* [<span data-ttu-id="4e772-153">Messaging-Erweiterung mit suchbasierten Befehlen</span><span class="sxs-lookup"><span data-stu-id="4e772-153">Messaging extension with search-based commands</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search)

### <a name="javascript"></a><span data-ttu-id="4e772-154">JavaScript</span><span class="sxs-lookup"><span data-stu-id="4e772-154">JavaScript</span></span>
* [<span data-ttu-id="4e772-155">Messaging-Erweiterung mit Aktions basierten Befehlen</span><span class="sxs-lookup"><span data-stu-id="4e772-155">Messaging extension with action-based commands</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action)
* [<span data-ttu-id="4e772-156">Messaging-Erweiterung mit suchbasierten Befehlen</span><span class="sxs-lookup"><span data-stu-id="4e772-156">Messaging extension with search-based commands</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search)

## <a name="learn-more"></a><span data-ttu-id="4e772-157">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="4e772-157">Learn more</span></span>

* [<span data-ttu-id="4e772-158">Erstellen einer Nachrichten-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="4e772-158">Create a messaging extension</span></span>](~/messaging-extensions/how-to/create-messaging-extension.md)
* [<span data-ttu-id="4e772-159">Aktions-Messaging-Erweiterungs Befehl definieren</span><span class="sxs-lookup"><span data-stu-id="4e772-159">Define action messaging extension command</span></span>](~/messaging-extensions/how-to/action-commands/define-action-command.md)
* [<span data-ttu-id="4e772-160">Definieren des Befehls für die Suchnachrichten Erweiterung</span><span class="sxs-lookup"><span data-stu-id="4e772-160">Define search messaging extension command</span></span>](~/messaging-extensions/how-to/search-commands/define-search-command.md)
* [<span data-ttu-id="4e772-161">Planen Ihrer APP</span><span class="sxs-lookup"><span data-stu-id="4e772-161">Planning your app</span></span>](../../concepts/extensibility-points.md)
* [<span data-ttu-id="4e772-162">Erstellen Ihrer APP</span><span class="sxs-lookup"><span data-stu-id="4e772-162">Building your app</span></span>](../../concepts/building-an-app.md)
* [<span data-ttu-id="4e772-163">Veröffentlichen Ihrer APP</span><span class="sxs-lookup"><span data-stu-id="4e772-163">Publishing your app</span></span>](../../concepts/deploy-and-publish/overview.md)