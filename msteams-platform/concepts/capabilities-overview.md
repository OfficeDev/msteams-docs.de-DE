---
title: Grundlegendes zu Teams-App-Funktionen
author: heath-hamilton
description: Erläuterte Teams-App-Funktionen
ms.topic: conceptual
ms.author: lajanuar
ms.date: 09/22/2020
ms.openlocfilehash: e7a6fe61fa5c74547ce20cc895afdd044f35e512
ms.sourcegitcommit: 1aa0b172931d0f81db346452788c41dc4a6717b9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "48210275"
---
# <a name="understanding-teams-app-capabilities"></a><span data-ttu-id="2ee51-103">Grundlegendes zu Teams-App-Funktionen</span><span class="sxs-lookup"><span data-stu-id="2ee51-103">Understanding Teams app capabilities</span></span>

<span data-ttu-id="2ee51-104">*Funktionen* sind die Erweiterungspunkte für das Erstellen von apps auf der Microsoft Teams-Plattform.</span><span class="sxs-lookup"><span data-stu-id="2ee51-104">*Capabilities* are the extension points for building apps on the Microsoft Teams platform.</span></span>

<span data-ttu-id="2ee51-105">Es gibt mehrere Möglichkeiten zum Erweitern von Teams, sodass jede APP eindeutig ist: einige verfügen nur über eine Funktion (beispielsweise einen webhook), während andere einige Benutzeroptionen zur Verfügung stellen.</span><span class="sxs-lookup"><span data-stu-id="2ee51-105">There are multiple ways to extend Teams, so every app is unique: Some only have one capability (such as a webhook), while others have a few to give users options.</span></span> <span data-ttu-id="2ee51-106">Beispielsweise könnte Ihre APP Daten an einem zentralen Ort (Tab) anzeigen und diese Informationen über eine Konversations Schnittstelle (bot) präsentieren.</span><span class="sxs-lookup"><span data-stu-id="2ee51-106">For instance, your app could display data in a central location (tab) and present that same information through a conversational interface (bot).</span></span>

<span data-ttu-id="2ee51-107">Ihre Teams-App kann eine oder alle der folgenden Hauptfunktionen haben:</span><span class="sxs-lookup"><span data-stu-id="2ee51-107">Your Teams app can have one or all of the following core capabilities:</span></span>

* [<span data-ttu-id="2ee51-108">Tabs</span><span class="sxs-lookup"><span data-stu-id="2ee51-108">Tabs</span></span>](../tabs/what-are-tabs.md)
* [<span data-ttu-id="2ee51-109">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="2ee51-109">Messaging extensions</span></span>](../messaging-extensions/what-are-messaging-extensions.md)
* [<span data-ttu-id="2ee51-110">Bots</span><span class="sxs-lookup"><span data-stu-id="2ee51-110">Bots</span></span>](../bots/what-are-bots.md)
* [<span data-ttu-id="2ee51-111">Webhooks und Connectors</span><span class="sxs-lookup"><span data-stu-id="2ee51-111">Webhooks and connectors</span></span>](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)

<span data-ttu-id="2ee51-112">Ihre APP kann auch erweiterte Funktionen nutzen, beispielsweise die [Microsoft Graph-API für Teams](https://docs.microsoft.com/graph/teams-concept-overview).</span><span class="sxs-lookup"><span data-stu-id="2ee51-112">Your app can also can take advantage of advanced capabilities, such as the [Microsoft Graph API for Teams](https://docs.microsoft.com/graph/teams-concept-overview).</span></span>

<span data-ttu-id="2ee51-113">In der folgenden Abbildung erfahren Sie, welche Funktionen die gewünschten Features in Ihrer APP bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="2ee51-113">See the following illustration to get an idea which capabilities would provide the features you want in your app.</span></span>

:::image type="content" source="../assets/images/capabilities-overview.png" alt-text="Mind Map illustriert, was Teams-App-Funktionen sind.":::

## <a name="doing-whats-best-for-your-users"></a><span data-ttu-id="2ee51-115">Ausführen des am besten geeigneten für Ihre Benutzer</span><span class="sxs-lookup"><span data-stu-id="2ee51-115">Doing what's best for your users</span></span>

<span data-ttu-id="2ee51-116">Wenn Sie sich mit der APP-Entwicklung von Teams vertraut machen, verstehen Sie die Feinheiten.</span><span class="sxs-lookup"><span data-stu-id="2ee51-116">As you familiarize yourself with Teams app development, you'll begin to understand its subtleties.</span></span> <span data-ttu-id="2ee51-117">Es gibt mehrere Möglichkeiten zum Erstellen bestimmter Features (beispielsweise das Sammeln von Benutzereingaben).</span><span class="sxs-lookup"><span data-stu-id="2ee51-117">There's more than one way to build certain features (such as collecting user input).</span></span> <span data-ttu-id="2ee51-118">Beispielsweise können Sie ein webbasiertes Formular in einer Registerkarte mit einem einbetten `<iframe>` .</span><span class="sxs-lookup"><span data-stu-id="2ee51-118">For example, you could embed a web-based form in a tab using an `<iframe>`.</span></span> <span data-ttu-id="2ee51-119">Sie können dies auch auf einer Registerkarte mithilfe eines Aufgabenmoduls, einer Benutzeroberflächen Konvention für Teams, für eine mehr systemeigene Benutzeroberfläche tun, die Ihren Benutzern möglicherweise lieber ist.</span><span class="sxs-lookup"><span data-stu-id="2ee51-119">You could also do this in a tab using a task module, a Teams UI convention, for a more native experience your users may prefer.</span></span>

<span data-ttu-id="2ee51-120">Wenn Sie die richtigen Funktionen und das richtige Design auswählen, müssen Sie sich zunächst [mit den Anwendungsfällen Ihres Publikums vertraut](../concepts/design/understand-use-cases.md)machen.</span><span class="sxs-lookup"><span data-stu-id="2ee51-120">Choosing the right capabilities and design comes down to first [understanding your audience's use cases](../concepts/design/understand-use-cases.md).</span></span>
