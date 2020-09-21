---
title: Grundlegendes zu Teams-App-Funktionen
author: heath-hamilton
description: Übersicht über die Plattformfunktionen von Teams, die die Erweiterungspunkte für das Erstellen von Microsoft Teams-apps darstellen.
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: 9bb94d2cfd5c30b2245c5ccf580d374972315e72
ms.sourcegitcommit: d3bb4bbcdff9545c9869647dcdbe563a2db868be
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/18/2020
ms.locfileid: "47964564"
---
# <a name="understanding-teams-app-capabilities"></a><span data-ttu-id="0e119-103">Grundlegendes zu Teams-App-Funktionen</span><span class="sxs-lookup"><span data-stu-id="0e119-103">Understanding Teams app capabilities</span></span>

<span data-ttu-id="0e119-104">*Funktionen* sind die Erweiterungspunkte für das Erstellen von apps auf der Microsoft Teams-Plattform.</span><span class="sxs-lookup"><span data-stu-id="0e119-104">*Capabilities* are the extension points for building apps on the Microsoft Teams platform.</span></span>

<span data-ttu-id="0e119-105">Es gibt mehrere Möglichkeiten, den Microsoft Teams-Client zu erweitern, sodass jede APP eindeutig ist: einige haben nur eine Funktion (beispielsweise einen webhook), während andere einige Benutzeroptionen haben.</span><span class="sxs-lookup"><span data-stu-id="0e119-105">There are multiple ways to extend the Teams client, so every app is unique: Some only have one capability (such as a webhook), while others have a few to give users options.</span></span> <span data-ttu-id="0e119-106">Beispielsweise könnte Ihre APP Daten an einem zentralen Ort (Tab) anzeigen und diese Informationen über eine Konversations Schnittstelle (bot) präsentieren.</span><span class="sxs-lookup"><span data-stu-id="0e119-106">For instance, your app could display data in a central location (tab) and present that same information through a conversational interface (bot).</span></span>

<span data-ttu-id="0e119-107">Ihre Teams-App kann eine oder alle der folgenden Hauptfunktionen haben:</span><span class="sxs-lookup"><span data-stu-id="0e119-107">Your Teams app can have one or all of the following core capabilities:</span></span>

* [<span data-ttu-id="0e119-108">Tabs</span><span class="sxs-lookup"><span data-stu-id="0e119-108">Tabs</span></span>](../tabs/what-are-tabs.md)
* [<span data-ttu-id="0e119-109">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="0e119-109">Messaging extensions</span></span>](../messaging-extensions/what-are-messaging-extensions.md)
* [<span data-ttu-id="0e119-110">Webhooks und Connectors</span><span class="sxs-lookup"><span data-stu-id="0e119-110">Webhooks and connectors</span></span>](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)
* [<span data-ttu-id="0e119-111">Bots</span><span class="sxs-lookup"><span data-stu-id="0e119-111">Bots</span></span>](../bots/what-are-bots.md)

<span data-ttu-id="0e119-112">Ihre APP kann auch erweiterte Funktionen nutzen, beispielsweise die [Microsoft Graph-Rest-API](../graph-api/rsc/resource-specific-consent.md).</span><span class="sxs-lookup"><span data-stu-id="0e119-112">Your app can also can take advantage of advanced capabilities, such as the [Microsoft Graph REST API](../graph-api/rsc/resource-specific-consent.md).</span></span>

<span data-ttu-id="0e119-113">In der folgenden Abbildung erfahren Sie, welche Funktionen die gewünschten Features in Ihrer APP bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="0e119-113">See the following illustration to get an idea which capabilities would provide the features you want in your app.</span></span>

![Mind Map veranschaulicht, welche Teams-App-Funktionen](doc-links/images/capabilities-overview.png)

## <a name="doing-whats-best-for-your-users"></a><span data-ttu-id="0e119-115">Ausführen des am besten geeigneten für Ihre Benutzer</span><span class="sxs-lookup"><span data-stu-id="0e119-115">Doing what's best for your users</span></span>

<span data-ttu-id="0e119-116">Wenn Sie sich mit der APP-Entwicklung von Teams vertraut machen, verstehen Sie die Feinheiten.</span><span class="sxs-lookup"><span data-stu-id="0e119-116">As you familiarize yourself with Teams app development, you'll begin to understand its subtleties.</span></span> <span data-ttu-id="0e119-117">Es gibt mehrere Möglichkeiten zum Erstellen bestimmter Features (beispielsweise das Sammeln von Benutzereingaben).</span><span class="sxs-lookup"><span data-stu-id="0e119-117">There's more than one way to build certain features (such as collecting user input).</span></span> <span data-ttu-id="0e119-118">Beispielsweise können Sie ein webbasiertes Formular in einer Registerkarte mit einem einbetten `<iframe>` .</span><span class="sxs-lookup"><span data-stu-id="0e119-118">For example, you could embed a web-based form in a tab using an `<iframe>`.</span></span> <span data-ttu-id="0e119-119">Sie können dies auch auf einer Registerkarte mithilfe eines Aufgabenmoduls, einer Benutzeroberflächen Konvention für Teams, für eine mehr systemeigene Benutzeroberfläche tun, die Ihren Benutzern möglicherweise lieber ist.</span><span class="sxs-lookup"><span data-stu-id="0e119-119">You could also do this in a tab using a task module, a Teams UI convention, for a more native experience your users may prefer.</span></span>

<span data-ttu-id="0e119-120">Bei der Auswahl der richtigen Kombination von Funktionen und Benutzeroberflächen Konventionen, Steuerelementen und Elementen wird zunächst die [Anwendungsfälle der Benutzergruppen verstanden](../concepts/design/understand-use-cases.md).</span><span class="sxs-lookup"><span data-stu-id="0e119-120">Choosing the right combination of capabilities and UI conventions, controls, and elements comes down to first [understanding your audience's use cases](../concepts/design/understand-use-cases.md).</span></span>

## <a name="learn-more"></a><span data-ttu-id="0e119-121">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="0e119-121">Learn more</span></span>

* [<span data-ttu-id="0e119-122">Starten der Planung Ihrer APP</span><span class="sxs-lookup"><span data-stu-id="0e119-122">Start planning your app</span></span>](../concepts/extensibility-points.md)
