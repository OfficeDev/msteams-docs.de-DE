---
title: Verstehen von App-Funktionen
author: heath-hamilton
description: Teams-App-Funktionen erläutert
ms.topic: conceptual
localization_priority: Normal
ms.author: lajanuar
ms.date: 09/22/2020
ms.openlocfilehash: 209d187681b1370440931fcd40744965395b13e8
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52565151"
---
# <a name="understand-microsoft-teams-app-capabilities"></a><span data-ttu-id="c095a-103">Verstehen Microsoft Teams App-Funktionen</span><span class="sxs-lookup"><span data-stu-id="c095a-103">Understand Microsoft Teams app capabilities</span></span>

<span data-ttu-id="c095a-104">Erweiterbarkeits- oder Einstiegspunkte sind unterschiedliche Möglichkeiten, wie sich eine App für einen Benutzer manifestieren kann.</span><span class="sxs-lookup"><span data-stu-id="c095a-104">Extensibility or entry points are different ways in which an app can manifest itself to a user.</span></span> <span data-ttu-id="c095a-105">Ein Benutzer kann z. B. mit einer App auf einer Canvas-Registerkarte interagieren, um eine Aktivität zu tun, oder er kann dies auch mithilfe eines Unterhaltungsbots tun.</span><span class="sxs-lookup"><span data-stu-id="c095a-105">For example, a user can interact with an app on a canvas tab to do an activity or might choose to do the same using a conversational bot.</span></span> <span data-ttu-id="c095a-106">Die verschiedenen Funktionen zum Erstellen ihrer Teams ermöglichen es Ihnen, den Nutzungsbereich zu erhöhen.</span><span class="sxs-lookup"><span data-stu-id="c095a-106">The various capabilities used to build your Teams app allow you to increase its usage scope.</span></span>

<span data-ttu-id="c095a-107">Es gibt mehrere Möglichkeiten zum Erweitern Teams, sodass jede App eindeutig ist.</span><span class="sxs-lookup"><span data-stu-id="c095a-107">There are multiple ways to extend Teams, so every app is unique.</span></span> <span data-ttu-id="c095a-108">Einige verfügen nur über eine Funktion, z. B. einen Webhook, während andere über mehr als ein Feature verfügen, um Benutzern verschiedene Optionen zu bieten.</span><span class="sxs-lookup"><span data-stu-id="c095a-108">Some only have one capability, such as a webhook, while others have more than one feature to give users various options.</span></span> <span data-ttu-id="c095a-109">Beispielsweise kann Ihre App Daten an einem zentralen Ort, d. h. der Registerkarte, anzeigen und dieselben Informationen über eine Unterhaltungsschnittstelle, d. h. den **Bot, präsentieren.** </span><span class="sxs-lookup"><span data-stu-id="c095a-109">For example, your app can display data in a central location, that is, the **tab** and present that same information through a conversational interface, that is, the **bot**.</span></span>

## <a name="app-capabilities"></a><span data-ttu-id="c095a-110">App-Funktionen</span><span class="sxs-lookup"><span data-stu-id="c095a-110">App capabilities</span></span>

<span data-ttu-id="c095a-111">Ihre Teams-App verfügt über eine oder alle der folgenden Kernfunktionen:</span><span class="sxs-lookup"><span data-stu-id="c095a-111">Your Teams app have one or all of the following core capabilities:</span></span>

* [<span data-ttu-id="c095a-112">Registerkarten</span><span class="sxs-lookup"><span data-stu-id="c095a-112">Tabs</span></span>](../tabs/what-are-tabs.md)
* [<span data-ttu-id="c095a-113">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="c095a-113">Messaging extensions</span></span>](../messaging-extensions/what-are-messaging-extensions.md)
* [<span data-ttu-id="c095a-114">Bots</span><span class="sxs-lookup"><span data-stu-id="c095a-114">Bots</span></span>](../bots/what-are-bots.md)
* [<span data-ttu-id="c095a-115">Webhooks und Connectors</span><span class="sxs-lookup"><span data-stu-id="c095a-115">Webhooks and connectors</span></span>](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)

<span data-ttu-id="c095a-116">Ihre App kann auch erweiterte Funktionen nutzen, z. B. die [Microsoft Graph-API für Teams](/graph/teams-concept-overview).</span><span class="sxs-lookup"><span data-stu-id="c095a-116">Your app can also take advantage of advanced capabilities, such as the [Microsoft Graph API for Teams](/graph/teams-concept-overview).</span></span>

<span data-ttu-id="c095a-117">In der folgenden Abbildung erhalten Sie eine Vorstellung davon, welche Funktionen die features bereitstellen, die Sie in Ihrer App benötigen:</span><span class="sxs-lookup"><span data-stu-id="c095a-117">The following illustration gives you an idea of which capabilities will provide the features you want in your app:</span></span>

:::image type="content" source="../assets/images/capabilities-overview.png" alt-text="Mindmap, die zeigt, Teams funktionen der App sind.":::

## <a name="always-consider-your-user"></a><span data-ttu-id="c095a-119">Berücksichtigen Sie immer Ihren Benutzer</span><span class="sxs-lookup"><span data-stu-id="c095a-119">Always consider your user</span></span>

<span data-ttu-id="c095a-120">Wenn Sie sich mit der Teams vertraut machen, verstehen Sie die grundlegenden Grundlagen der App.</span><span class="sxs-lookup"><span data-stu-id="c095a-120">As you familiarize yourself with Teams app development, you understand its core fundamentals.</span></span> <span data-ttu-id="c095a-121">Sie wissen, dass es mehr als eine Möglichkeit gibt, bestimmte Features zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="c095a-121">You understand that there is more than one way to build certain features.</span></span> <span data-ttu-id="c095a-122">Überlegen Sie in solchen Szenarien, wie Sie Ihrem Benutzer eine nativere Benutzeroberfläche bereitstellen können.</span><span class="sxs-lookup"><span data-stu-id="c095a-122">In such scenarios, consider how you can provide a more native experience to your user.</span></span>
<span data-ttu-id="c095a-123">Beispielsweise können Sie Benutzereingaben in einem Formular erfassen, das als Registerkarte in der App erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="c095a-123">For example, you can collect user input in a form built as a tab in the app.</span></span> <span data-ttu-id="c095a-124">Sie können dies auch mithilfe eines Aufgabenmoduls tun, ohne Ansichten zu wechseln und den Arbeitsfluss des Benutzers zu unterbrechen.</span><span class="sxs-lookup"><span data-stu-id="c095a-124">You can also do this using a task module without switching views and disrupting user's flow of work.</span></span> <span data-ttu-id="c095a-125">Es ist wichtig, Erweiterungspunkte zu wählen, die die geringste Abweichung vom regulären Arbeitsfluss eines Benutzers bieten.</span><span class="sxs-lookup"><span data-stu-id="c095a-125">It is important to choose extension points that provide least deviation from a user's regular flow of work.</span></span>

## <a name="see-also"></a><span data-ttu-id="c095a-126">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="c095a-126">See also</span></span>

[<span data-ttu-id="c095a-127">Erstellen von Apps für Teams</span><span class="sxs-lookup"><span data-stu-id="c095a-127">Build apps for Teams</span></span>](../overview.md)

## <a name="next-step"></a><span data-ttu-id="c095a-128">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="c095a-128">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c095a-129">Microsoft Teams-App-Einstiegspunkte</span><span class="sxs-lookup"><span data-stu-id="c095a-129">Teams app entry points</span></span>](../concepts/extensibility-points.md)
