---
title: Apps für Teams Besprechungen
author: surbhigupta
description: Übersicht über Apps in Teams Besprechungen basierend auf Teilnehmer- und Benutzerrolle
ms.topic: overview
ms.author: lajanuar
localization_priority: Normal
keywords: Teams-Apps – Benutzerteilnehmer-Rollen-API für Besprechungen
ms.openlocfilehash: 0ba475e852b8dc673d33ac818077b3b0951ac5f9
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "53068568"
---
# <a name="apps-for-teams-meetings"></a><span data-ttu-id="dd36a-104">Apps für Teams Besprechungen</span><span class="sxs-lookup"><span data-stu-id="dd36a-104">Apps for Teams meetings</span></span>

<span data-ttu-id="dd36a-105">Besprechungen ermöglichen Zusammenarbeit, Partnerschaft, informierte Kommunikation und gemeinsames Feedback in einem inklusiven und aktiven Forum.</span><span class="sxs-lookup"><span data-stu-id="dd36a-105">Meetings enable collaboration, partnership, informed communication, and shared feedback in an inclusive and active forum.</span></span> <span data-ttu-id="dd36a-106">Die Besprechungs-App kann je nach Status des Teilnehmers eine Benutzererfahrung für jede Phase des Besprechungslebenszyklus bereitstellen, einschließlich der App-Erfahrung vor der Besprechung, in besprechungsbesprechung und nach der Besprechung.</span><span class="sxs-lookup"><span data-stu-id="dd36a-106">The meeting app can deliver a user experience for each stage of the meeting lifecycle including pre-meeting, in-meeting, and post-meeting app experience, depending on the attendee's status.</span></span>

<span data-ttu-id="dd36a-107">Die Benutzer können während Besprechungen über den Registerkartenkatalog auf Apps zugreifen, z. B.:</span><span class="sxs-lookup"><span data-stu-id="dd36a-107">The users can access apps during meetings using the tab gallery, for example:</span></span>

* <span data-ttu-id="dd36a-108">Vorabphase eines Boards für Diess.</span><span class="sxs-lookup"><span data-stu-id="dd36a-108">Pre-stage a Kanban board.</span></span>
* <span data-ttu-id="dd36a-109">Starten Sie ein Dialogfeld, in dem Aktionen ausgeführt werden können.</span><span class="sxs-lookup"><span data-stu-id="dd36a-109">Launch an in-meeting actionable dialog.</span></span>
* <span data-ttu-id="dd36a-110">Erstellen Sie eine Umfrage nach der Besprechung.</span><span class="sxs-lookup"><span data-stu-id="dd36a-110">Create a post-meeting survey.</span></span>

> [!VIDEO https://www.youtube-nocookie.com/embed/nKAy5rNDus4]

<span data-ttu-id="dd36a-111">Dieser Artikel bietet eine Übersicht über die Erweiterbarkeit von Besprechungs-Apps, API-Referenzen, das Aktivieren und Konfigurieren von Apps für Besprechungen und benutzerdefinierte Szenen im Gemeinsamen Modus in Teams.</span><span class="sxs-lookup"><span data-stu-id="dd36a-111">This article provides an overview of meeting app extensibility, API references, enable and configure apps for meetings, and custom Together Mode scenes in Teams.</span></span>

<span data-ttu-id="dd36a-112">Sie können Ihre Besprechungserfahrung verbessern, indem Sie das Feature zur Besprechungserweiterung verwenden, mit dem Sie Ihre Apps in Besprechungen integrieren können.</span><span class="sxs-lookup"><span data-stu-id="dd36a-112">You can enhance your meeting experience by using the meeting extensibility feature, which enables you to integrate your apps within meetings.</span></span> <span data-ttu-id="dd36a-113">Es umfasst auch verschiedene Phasen eines Besprechungslebenszyklus, in denen Sie Registerkarten, Bots und Messaging-Erweiterungen integrieren können.</span><span class="sxs-lookup"><span data-stu-id="dd36a-113">It also includes different stages of a meeting lifecycle, where you can integrate tabs, bots, and messaging extensions.</span></span> <span data-ttu-id="dd36a-114">Mit Besprechungserweiterungs-APIs können Sie unterschiedliche Teilnehmerrollen und Benutzertypen identifizieren, Besprechungsereignisse abrufen, In-Meeting-Dialogfelder generieren usw.</span><span class="sxs-lookup"><span data-stu-id="dd36a-114">With meetings extensibility APIs, you can identify different participant roles and user types, get meeting events, generate in-meeting dialogs, and so on.</span></span>

<span data-ttu-id="dd36a-115">Um Teams mit Apps für Besprechungen anzupassen, können Sie Ihre Apps für Teams Besprechungen aktivieren, indem Sie Ihr App-Manifest aktualisieren und Ihre Apps auch für Besprechungsszenarien konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="dd36a-115">To customize Teams with apps for meetings, you can enable your apps for Teams meetings by updating your app manifest and you can also configure your apps for meeting scenarios.</span></span>

<span data-ttu-id="dd36a-116">Mit der neuen benutzerdefinierten Szenenfunktion für den gemeinsamen Modus können Benutzer in einer Besprechung mit ihrem Team an einem Ort zusammenarbeiten, ohne durch Felder getrennt zu sein.</span><span class="sxs-lookup"><span data-stu-id="dd36a-116">The new custom Together Mode scenes feature enables users to collaborate in a meeting with their team in one place without being separated by boxes.</span></span>

## <a name="see-also"></a><span data-ttu-id="dd36a-117">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="dd36a-117">See also</span></span>

* [<span data-ttu-id="dd36a-118">Tab</span><span class="sxs-lookup"><span data-stu-id="dd36a-118">Tab</span></span>](../tabs/what-are-tabs.md#understand-how-tabs-work)
* [<span data-ttu-id="dd36a-119">Bot</span><span class="sxs-lookup"><span data-stu-id="dd36a-119">Bot</span></span>](../bots/what-are-bots.md)
* [<span data-ttu-id="dd36a-120">Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="dd36a-120">Messaging extension</span></span>](../messaging-extensions/what-are-messaging-extensions.md)
* [<span data-ttu-id="dd36a-121">Entwerfen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="dd36a-121">Design your app</span></span>](../apps-in-teams-meetings/design/designing-apps-in-meetings.md)
* [<span data-ttu-id="dd36a-122">Voraussetzungen und API-Verweise für Apps in Teams-Besprechungen</span><span class="sxs-lookup"><span data-stu-id="dd36a-122">Prerequisites and API references for apps in Teams meetings</span></span>](create-apps-for-teams-meetings.md)
* [<span data-ttu-id="dd36a-123">Szenen des benutzerdefinierten Zusammen-Modus</span><span class="sxs-lookup"><span data-stu-id="dd36a-123">Custom Together Mode scenes</span></span>](~/apps-in-teams-meetings/teams-together-mode.md)

## <a name="next-step"></a><span data-ttu-id="dd36a-124">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="dd36a-124">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="dd36a-125">Erweiterbarkeit der Besprechungs-App</span><span class="sxs-lookup"><span data-stu-id="dd36a-125">Meeting app extensibility</span></span>](meeting-app-extensibility.md)
