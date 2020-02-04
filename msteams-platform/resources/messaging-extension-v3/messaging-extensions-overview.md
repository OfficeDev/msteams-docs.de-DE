---
title: Entwickeln von Messaging Erweiterungen
description: Beschreibt, wie Sie mit den ersten Schritten mit Messaging-Erweiterungen in Microsoft Teams beginnen
keywords: Messaging Erweiterungen für Microsoft Teams-Messaging Erweiterungen
ms.openlocfilehash: 6ba8f73d40f795a83f28707ef89c207c5d51d67c
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674108"
---
# <a name="develop-messaging-extensions-for-microsoft-teams"></a><span data-ttu-id="09e0b-104">Entwickeln von Messaging Erweiterungen für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="09e0b-104">Develop messaging extensions for Microsoft Teams</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-me.md)]

<span data-ttu-id="09e0b-105">Messaging Erweiterungen sind eine leistungsstarke Möglichkeit für Benutzer, mit Ihrer APP von Microsoft Teams zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="09e0b-105">Messaging extensions are a powerful way for users to engage with your app from Microsoft Teams.</span></span> <span data-ttu-id="09e0b-106">Mit dieser Funktion können Benutzerinformationen zu und von Ihrem Dienst Abfragen oder bereitstellen und diese Informationen in Form von Karten rechts in eine Nachricht Posten.</span><span class="sxs-lookup"><span data-stu-id="09e0b-106">With this capability, users can query or post information to and from your service and post that information, in the form of cards, right into a message.</span></span>

![Beispiel für eine Messaging Erweiterungskarte](~/assets/images/compose-extensions/ceexample.png)

<span data-ttu-id="09e0b-108">Messaging Erweiterungen werden am unteren Rand des Felds verfassen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="09e0b-108">Messaging extensions appear along the bottom of the compose box.</span></span> <span data-ttu-id="09e0b-109">Einige sind eingebaut, wie Emoji, Giphy und Aufkleber.</span><span class="sxs-lookup"><span data-stu-id="09e0b-109">A few are built in, such as Emoji, Giphy, and Sticker.</span></span> <span data-ttu-id="09e0b-110">Klicken Sie auf die Schaltfläche **Weitere Optionen** (**&#8943;**), um weitere Messaging Erweiterungen anzuzeigen, einschließlich derer, die Sie aus dem App-Katalog hinzufügen oder sich selbst hochladen.</span><span class="sxs-lookup"><span data-stu-id="09e0b-110">Choose the **More Options** (**&#8943;**) button to see other messaging extensions, including those you add from the app gallery or upload yourself.</span></span>

<span data-ttu-id="09e0b-111">Wie würden Sie Messaging-Erweiterungen verwenden?</span><span class="sxs-lookup"><span data-stu-id="09e0b-111">How would you use messaging extensions?</span></span> <span data-ttu-id="09e0b-112">Es folgen einige Möglichkeiten:</span><span class="sxs-lookup"><span data-stu-id="09e0b-112">Here are a few possibilities:</span></span>

* <span data-ttu-id="09e0b-113">Arbeitsaufgaben und Fehler</span><span class="sxs-lookup"><span data-stu-id="09e0b-113">Work items and bugs</span></span>
* <span data-ttu-id="09e0b-114">Kundensupport Tickets</span><span class="sxs-lookup"><span data-stu-id="09e0b-114">Customer support tickets</span></span>
* <span data-ttu-id="09e0b-115">Verwendungs Diagramme und-Berichte</span><span class="sxs-lookup"><span data-stu-id="09e0b-115">Usage charts and reports</span></span>
* <span data-ttu-id="09e0b-116">Bilder und Medieninhalte</span><span class="sxs-lookup"><span data-stu-id="09e0b-116">Images and media content</span></span>
* <span data-ttu-id="09e0b-117">Verkaufschancen und Leads</span><span class="sxs-lookup"><span data-stu-id="09e0b-117">Sales opportunities and leads</span></span>

## <a name="types-of-messaging-extensions"></a><span data-ttu-id="09e0b-118">Typen von Messaging Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="09e0b-118">Types of messaging extensions</span></span>

<span data-ttu-id="09e0b-119">Es gibt in erster Linie zwei Arten von Messaging Erweiterungen, die Sie für Microsoft Teams heute erstellen können.</span><span class="sxs-lookup"><span data-stu-id="09e0b-119">There's primarily two kinds of messaging extensions you can create for Teams today.</span></span> <span data-ttu-id="09e0b-120">In den folgenden Themen werden Sie durch den Prozess der Erstellung dieser Schritte geleitet:</span><span class="sxs-lookup"><span data-stu-id="09e0b-120">The following topics will guide you through the process of creating them:</span></span>

* <span data-ttu-id="09e0b-121">[Suchbasierte Messaging Erweiterungen](~/resources/messaging-extension-v3/search-extensions.md): Fragen Sie Ihren Dienst nach Informationen, und fügen Sie diesen in eine Nachricht ein.</span><span class="sxs-lookup"><span data-stu-id="09e0b-121">[Search based messaging extensions](~/resources/messaging-extension-v3/search-extensions.md): Query your service for information and insert that into a message.</span></span> <span data-ttu-id="09e0b-122">Beispiel: Suchen einer Arbeitsaufgabe</span><span class="sxs-lookup"><span data-stu-id="09e0b-122">Example: Lookup a work item</span></span>
* <span data-ttu-id="09e0b-123">[Aktionsbasierte Messaging Erweiterungen](~/resources/messaging-extension-v3/create-extensions.md): Sammeln von Informationen vom Benutzer und Bereitstellen eines Drittanbieter Diensts.</span><span class="sxs-lookup"><span data-stu-id="09e0b-123">[Action-based messaging extensions](~/resources/messaging-extension-v3/create-extensions.md): Collect information from the user and post to a 3rd party service.</span></span> <span data-ttu-id="09e0b-124">Beispiel: Erstellen einer Arbeitsaufgabe</span><span class="sxs-lookup"><span data-stu-id="09e0b-124">Example: Create a work item</span></span>
