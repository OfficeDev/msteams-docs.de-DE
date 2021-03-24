---
title: Grundlegendes zu den Funktionen von Teams-Apps
author: heath-hamilton
description: Erläuterte Funktionen der Teams-App
ms.topic: conceptual
ms.author: lajanuar
ms.date: 09/22/2020
ms.openlocfilehash: 5336b36b52cf81be414f18ccaaf9e235c079e626
ms.sourcegitcommit: 49d1ecda14042bf3f368b14c1971618fe979b914
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/23/2021
ms.locfileid: "51034705"
---
# <a name="understanding-teams-app-capabilities"></a><span data-ttu-id="cbd3d-103">Grundlegendes zu den Funktionen von Teams-Apps</span><span class="sxs-lookup"><span data-stu-id="cbd3d-103">Understanding Teams app capabilities</span></span>

<span data-ttu-id="cbd3d-104">*Funktionen* sind die Erweiterungspunkte für das Erstellen von Apps auf der Microsoft Teams-Plattform.</span><span class="sxs-lookup"><span data-stu-id="cbd3d-104">*Capabilities* are the extension points for building apps on the Microsoft Teams platform.</span></span>

<span data-ttu-id="cbd3d-105">Es gibt mehrere Möglichkeiten, Teams zu erweitern, sodass jede App einzigartig ist: Einige haben nur eine Funktion (z. B. einen Webhook), während andere über einige Möglichkeiten verfügen, benutzern Optionen zu geben.</span><span class="sxs-lookup"><span data-stu-id="cbd3d-105">There are multiple ways to extend Teams, so every app is unique: Some only have one capability (such as a webhook), while others have a few to give users options.</span></span> <span data-ttu-id="cbd3d-106">Beispielsweise könnte Ihre App Daten an einem zentralen Ort (Registerkarte) anzeigen und dieselben Informationen über eine Unterhaltungsschnittstelle (Bot) präsentieren.</span><span class="sxs-lookup"><span data-stu-id="cbd3d-106">For instance, your app could display data in a central location (tab) and present that same information through a conversational interface (bot).</span></span>

<span data-ttu-id="cbd3d-107">Ihre Teams-App verfügt über eine oder alle der folgenden Kernfunktionen:</span><span class="sxs-lookup"><span data-stu-id="cbd3d-107">Your Teams app have one or all of the following core capabilities:</span></span>

* [<span data-ttu-id="cbd3d-108">Registerkarten</span><span class="sxs-lookup"><span data-stu-id="cbd3d-108">Tabs</span></span>](../tabs/what-are-tabs.md)
* [<span data-ttu-id="cbd3d-109">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="cbd3d-109">Messaging extensions</span></span>](../messaging-extensions/what-are-messaging-extensions.md)
* [<span data-ttu-id="cbd3d-110">Bots</span><span class="sxs-lookup"><span data-stu-id="cbd3d-110">Bots</span></span>](../bots/what-are-bots.md)
* [<span data-ttu-id="cbd3d-111">Webhooks und Connectors</span><span class="sxs-lookup"><span data-stu-id="cbd3d-111">Webhooks and connectors</span></span>](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)

<span data-ttu-id="cbd3d-112">Ihre App kann auch erweiterte Funktionen nutzen, z. B. die [Microsoft Graph-API für Teams.](https://docs.microsoft.com/graph/teams-concept-overview)</span><span class="sxs-lookup"><span data-stu-id="cbd3d-112">Your app can also take advantage of advanced capabilities, such as the [Microsoft Graph API for Teams](https://docs.microsoft.com/graph/teams-concept-overview).</span></span>

<span data-ttu-id="cbd3d-113">In der folgenden Abbildung finden Sie eine Vorstellung davon, welche Funktionen die features bereitstellen würden, die Sie in Ihrer App wünschen.</span><span class="sxs-lookup"><span data-stu-id="cbd3d-113">See the following illustration to get an idea which capabilities would provide the features you want in your app.</span></span>

:::image type="content" source="../assets/images/capabilities-overview.png" alt-text="Mindmap, die zeigt, welche Teams-App-Funktionen es gibt.":::

## <a name="doing-whats-best-for-your-users"></a><span data-ttu-id="cbd3d-115">Tun, was für Ihre Benutzer am besten ist</span><span class="sxs-lookup"><span data-stu-id="cbd3d-115">Doing what's best for your users</span></span>

<span data-ttu-id="cbd3d-116">Wenn Sie sich mit der Entwicklung von Teams-Apps vertraut machen, beginnen Sie, ihre Feinheiten zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="cbd3d-116">As you familiarize yourself with Teams app development, you'll begin to understand its subtleties.</span></span> <span data-ttu-id="cbd3d-117">Es gibt mehr als eine Möglichkeit, bestimmte Features zu erstellen (z. B. das Sammeln von Benutzereingaben).</span><span class="sxs-lookup"><span data-stu-id="cbd3d-117">There's more than one way to build certain features (such as collecting user input).</span></span> <span data-ttu-id="cbd3d-118">Beispielsweise können Sie ein webbasiertes Formular mithilfe einer in eine Registerkarte `<iframe>` einbetten.</span><span class="sxs-lookup"><span data-stu-id="cbd3d-118">For example, you could embed a web-based form in a tab using an `<iframe>`.</span></span> <span data-ttu-id="cbd3d-119">Sie können dies auch auf einer Registerkarte mithilfe eines Aufgabenmoduls, einer Teams-UI-Konvention, tun, um eine systemeigenere Oberfläche zu erhalten, die Ihren Benutzern vielleicht lieber ist.</span><span class="sxs-lookup"><span data-stu-id="cbd3d-119">You could also do this in a tab using a task module, a Teams UI convention, for a more native experience your users may prefer.</span></span>

<span data-ttu-id="cbd3d-120">Die Auswahl der richtigen Funktionen und des richtigen Designs kommt dazu, zunächst die Verwendungsfälle [Ihrer Zielgruppe zu verstehen.](../concepts/design/understand-use-cases.md)</span><span class="sxs-lookup"><span data-stu-id="cbd3d-120">Choosing the right capabilities and design comes down to first [understanding your audience's use cases](../concepts/design/understand-use-cases.md).</span></span>
