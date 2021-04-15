---
title: Entwickeln von Messagingerweiterungen
description: Beschreibt, wie Sie mit Messagingerweiterungen in Microsoft Teams beginnen
ms.topic: overview
keywords: Messagingerweiterungen für Teams
ms.openlocfilehash: 1eb75371b1a8adbeadbcbdbc0d06c7d88f2f1ccc
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2021
ms.locfileid: "51696549"
---
# <a name="develop-messaging-extensions-for-microsoft-teams"></a><span data-ttu-id="65d78-104">Entwickeln von Messagingerweiterungen für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="65d78-104">Develop messaging extensions for Microsoft Teams</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-me.md)]

<span data-ttu-id="65d78-105">Messagingerweiterungen sind eine leistungsstarke Möglichkeit für Benutzer, sich über Microsoft Teams mit Ihrer App zu beschäftigen.</span><span class="sxs-lookup"><span data-stu-id="65d78-105">Messaging extensions are a powerful way for users to engage with your app from Microsoft Teams.</span></span> <span data-ttu-id="65d78-106">Mit dieser Funktion können Benutzer Informationen an Und von Ihrem Dienst abfragen oder posten und diese Informationen in Form von Karten direkt in eine Nachricht posten.</span><span class="sxs-lookup"><span data-stu-id="65d78-106">With this capability, users can query or post information to and from your service and post that information, in the form of cards, right into a message.</span></span>

![Beispiel für Eine Messaging-Erweiterungskarte](~/assets/images/compose-extensions/ceexample.png)

<span data-ttu-id="65d78-108">Messagingerweiterungen werden am unteren Rand des Verfassenfelds angezeigt.</span><span class="sxs-lookup"><span data-stu-id="65d78-108">Messaging extensions appear along the bottom of the compose box.</span></span> <span data-ttu-id="65d78-109">Einige sind integrierte, z. B. Emoji, Giphy und Aufkleber.</span><span class="sxs-lookup"><span data-stu-id="65d78-109">A few are built in, such as Emoji, Giphy, and Sticker.</span></span> <span data-ttu-id="65d78-110">Wählen Sie **die Schaltfläche** Weitere Optionen (**&#8943;**) aus, um andere Messagingerweiterungen anzuzeigen, einschließlich derer, die Sie aus dem App-Katalog hinzufügen oder sich selbst hochladen.</span><span class="sxs-lookup"><span data-stu-id="65d78-110">Choose the **More Options** (**&#8943;**) button to see other messaging extensions, including those you add from the app gallery or upload yourself.</span></span>

<span data-ttu-id="65d78-111">Wie würden Sie Messagingerweiterungen verwenden?</span><span class="sxs-lookup"><span data-stu-id="65d78-111">How would you use messaging extensions?</span></span> <span data-ttu-id="65d78-112">Hier sind einige Möglichkeiten:</span><span class="sxs-lookup"><span data-stu-id="65d78-112">Here are a few possibilities:</span></span>

* <span data-ttu-id="65d78-113">Arbeitsaufgaben und Fehler</span><span class="sxs-lookup"><span data-stu-id="65d78-113">Work items and bugs</span></span>
* <span data-ttu-id="65d78-114">Kundensupporttickets</span><span class="sxs-lookup"><span data-stu-id="65d78-114">Customer support tickets</span></span>
* <span data-ttu-id="65d78-115">Verwendungsdiagramme und -berichte</span><span class="sxs-lookup"><span data-stu-id="65d78-115">Usage charts and reports</span></span>
* <span data-ttu-id="65d78-116">Bilder und Medieninhalte</span><span class="sxs-lookup"><span data-stu-id="65d78-116">Images and media content</span></span>
* <span data-ttu-id="65d78-117">Verkaufschancen und Leads</span><span class="sxs-lookup"><span data-stu-id="65d78-117">Sales opportunities and leads</span></span>

## <a name="types-of-messaging-extensions"></a><span data-ttu-id="65d78-118">Arten von Messagingerweiterungen</span><span class="sxs-lookup"><span data-stu-id="65d78-118">Types of messaging extensions</span></span>

<span data-ttu-id="65d78-119">Es gibt in erster Linie zwei Arten von Messagingerweiterungen, die Sie für Teams heute erstellen können.</span><span class="sxs-lookup"><span data-stu-id="65d78-119">There's primarily two kinds of messaging extensions you can create for Teams today.</span></span> <span data-ttu-id="65d78-120">Die folgenden Themen führen Sie durch den Erstellungsprozess:</span><span class="sxs-lookup"><span data-stu-id="65d78-120">The following topics will guide you through the process of creating them:</span></span>

* <span data-ttu-id="65d78-121">[Suchbasierte Messagingerweiterungen:](~/resources/messaging-extension-v3/search-extensions.md)Fragen Sie Ihren Dienst nach Informationen ab, und fügen Sie diese in eine Nachricht ein.</span><span class="sxs-lookup"><span data-stu-id="65d78-121">[Search based messaging extensions](~/resources/messaging-extension-v3/search-extensions.md): Query your service for information and insert that into a message.</span></span> <span data-ttu-id="65d78-122">Beispiel: Suchen einer Arbeitsaufgabe</span><span class="sxs-lookup"><span data-stu-id="65d78-122">Example: Lookup a work item</span></span>
* <span data-ttu-id="65d78-123">[Aktionsbasierte Messagingerweiterungen:](~/resources/messaging-extension-v3/create-extensions.md)Sammeln von Informationen vom Benutzer und Veröffentlichen an einen Drittanbieterdienst.</span><span class="sxs-lookup"><span data-stu-id="65d78-123">[Action-based messaging extensions](~/resources/messaging-extension-v3/create-extensions.md): Collect information from the user and post to a 3rd party service.</span></span> <span data-ttu-id="65d78-124">Beispiel: Erstellen einer Arbeitsaufgabe</span><span class="sxs-lookup"><span data-stu-id="65d78-124">Example: Create a work item</span></span>
