---
title: Apps für Teams Besprechungen
author: laujan
description: Übersicht über Apps in Teams Besprechungen basierend auf der Teilnehmer- und Benutzerrolle
ms.topic: overview
ms.author: lajanuar
localization_priority: Normal
keywords: Rollen-API für Teams-Apps-Besprechungen für Benutzerteilnehmer
ms.openlocfilehash: 1fdf3d55219d80d6953ffa0865b223dd626053f6
ms.sourcegitcommit: 999f5c607671e088ea8a461fa7dbb63f8d61c39b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/25/2021
ms.locfileid: "52649664"
---
# <a name="apps-for-teams-meetings"></a><span data-ttu-id="4032d-104">Apps für Teams Besprechungen</span><span class="sxs-lookup"><span data-stu-id="4032d-104">Apps for Teams meetings</span></span>

<span data-ttu-id="4032d-105">Besprechungen ermöglichen Zusammenarbeit, Partnerschaft, informierte Kommunikation und geteiltes Feedback in einem inklusiven und aktiven Forum.</span><span class="sxs-lookup"><span data-stu-id="4032d-105">Meetings enable collaboration, partnership, informed communication, and shared feedback in an inclusive and active forum.</span></span> <span data-ttu-id="4032d-106">Die Besprechungs-App kann je nach Status des Teilnehmers eine Benutzeroberfläche für jede Phase des Besprechungslebenszyklus bereitstellen, einschließlich der Vorbetreff-, Besprechungs- und Post-Meeting-App-Erfahrung.</span><span class="sxs-lookup"><span data-stu-id="4032d-106">The meeting app can deliver a user experience for each stage of the meeting lifecycle including pre-meeting, in-meeting, and post-meeting app experience, depending on the attendee's status.</span></span>

<span data-ttu-id="4032d-107">Die Benutzer können während Besprechungen über den Registerkartenkatalog auf Apps zugreifen, z. B.:</span><span class="sxs-lookup"><span data-stu-id="4032d-107">The users can access apps during meetings using the tab gallery, for example:</span></span>

* <span data-ttu-id="4032d-108">Pre-stage a Kanban board.</span><span class="sxs-lookup"><span data-stu-id="4032d-108">Pre-stage a Kanban board.</span></span>
* <span data-ttu-id="4032d-109">Starten Sie ein Dialogfeld mit Aktionen in Besprechungen.</span><span class="sxs-lookup"><span data-stu-id="4032d-109">Launch an in-meeting actionable dialog.</span></span>
* <span data-ttu-id="4032d-110">Erstellen sie eine Umfrage nach der Besprechung.</span><span class="sxs-lookup"><span data-stu-id="4032d-110">Create a post-meeting survey.</span></span>

> [!VIDEO https://www.youtube-nocookie.com/embed/nKAy5rNDus4]

<span data-ttu-id="4032d-111">Dieser Artikel bietet eine Übersicht über die Erweiterbarkeit von Besprechungs-Apps, API-Verweise, Aktivieren und Konfigurieren von Apps für Besprechungen und den Gemeinsamen Modus in Teams.</span><span class="sxs-lookup"><span data-stu-id="4032d-111">This article provides an overview of meeting app extensibility, API references, enable and configure apps for meetings, and Together Mode in Teams.</span></span>

<span data-ttu-id="4032d-112">Sie können Ihre Besprechungserfahrung verbessern, indem Sie das Feature zur Besprechungsergehnbarkeit verwenden, mit dem Sie Ihre Apps in Besprechungen integrieren können.</span><span class="sxs-lookup"><span data-stu-id="4032d-112">You can enhance your meeting experience by using the meeting extensibility feature, which enables you to integrate your apps within meetings.</span></span> <span data-ttu-id="4032d-113">Sie umfasst auch verschiedene Phasen eines Besprechungslebenszyklus, in dem Sie Registerkarten, Bots und Messagingerweiterungen integrieren können.</span><span class="sxs-lookup"><span data-stu-id="4032d-113">It also includes different stages of a meeting lifecycle, where you can integrate tabs, bots, and messaging extensions.</span></span> <span data-ttu-id="4032d-114">Mit Besprechungs-Erweiterbarkeits-APIs können Sie unterschiedliche Teilnehmerrollen und Benutzertypen identifizieren, Besprechungsereignisse erhalten, Dialoge in Besprechungen generieren und so weiter.</span><span class="sxs-lookup"><span data-stu-id="4032d-114">With meetings extensibility APIs, you can identify different participant roles and user types, get meeting events, generate in-meeting dialogs, and so on.</span></span>

<span data-ttu-id="4032d-115">Zum Anpassen Teams mit Apps für Besprechungen können Sie Ihre Apps für Teams-Besprechungen aktivieren, indem Sie Ihr App-Manifest aktualisieren und Ihre Apps auch für Besprechungsszenarien konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="4032d-115">To customize Teams with apps for meetings, you can enable your apps for Teams meetings by updating your app manifest and you can also configure your apps for meeting scenarios.</span></span>

<span data-ttu-id="4032d-116">Mit dem neuen Feature "Gemeinsamer Modus" können Benutzer an einer Besprechung mit ihrem Team an einem Ort zusammenarbeiten, ohne durch Felder getrennt zu werden.</span><span class="sxs-lookup"><span data-stu-id="4032d-116">The new Together Mode feature enables users to collaborate in a meeting with their team in one place without being separated by boxes.</span></span>

## <a name="see-also"></a><span data-ttu-id="4032d-117">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="4032d-117">See also</span></span>

* [<span data-ttu-id="4032d-118">Tab</span><span class="sxs-lookup"><span data-stu-id="4032d-118">Tab</span></span>](../tabs/what-are-tabs.md#understand-how-tabs-work)
* [<span data-ttu-id="4032d-119">Bot</span><span class="sxs-lookup"><span data-stu-id="4032d-119">Bot</span></span>](../bots/what-are-bots.md)
* [<span data-ttu-id="4032d-120">Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="4032d-120">Messaging extension</span></span>](../messaging-extensions/what-are-messaging-extensions.md)
* [<span data-ttu-id="4032d-121">Entwerfen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="4032d-121">Design your app</span></span>](../apps-in-teams-meetings/design/designing-apps-in-meetings.md)
* [<span data-ttu-id="4032d-122">Voraussetzungen und API-Verweise für Apps in Teams Besprechungen</span><span class="sxs-lookup"><span data-stu-id="4032d-122">Prerequisites and API references for apps in Teams meetings</span></span>](create-apps-for-teams-meetings.md)
* [<span data-ttu-id="4032d-123">Modus "Zusammen"</span><span class="sxs-lookup"><span data-stu-id="4032d-123">Together Mode</span></span>](~/apps-in-teams-meetings/teams-together-mode.md)

## <a name="next-step"></a><span data-ttu-id="4032d-124">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="4032d-124">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4032d-125">Erweiterbarkeit der Besprechungs-App</span><span class="sxs-lookup"><span data-stu-id="4032d-125">Meeting app extensibility</span></span>](meeting-app-extensibility.md)
