---
title: Senden der Mandanten-ID und der Konversations-ID an die Anforderungsheader des Bots
description: beschreibt, wie Mandanten-ID und Konversations-ID an die Anforderungsheader des Bots gesendet werden.
ms.topic: conceptual
localization_priority: Normal
ms.openlocfilehash: 76f667453114ab202d43217b9a4c01a6d14cc1a8
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52565893"
---
# <a name="send-tenant-id-and-conversation-id-to-the-request-headers-of-the-bot"></a><span data-ttu-id="eb84e-103">Senden der Mandanten-ID und der Konversations-ID an die Anforderungsheader des Bots</span><span class="sxs-lookup"><span data-stu-id="eb84e-103">Send tenant ID and conversation ID to the request headers of the bot</span></span>

<span data-ttu-id="eb84e-104">Die aktuellen ausgehenden Anforderungen an den Bot enthalten keine Informationen im Header oder URL, die Bots dabei helfen, den Datenverkehr weiterzuleiten, ohne die gesamte Nutzlast zu entpacken.</span><span class="sxs-lookup"><span data-stu-id="eb84e-104">The current outgoing requests to the bot do not contain in the header or URL any information that helps bots route the traffic without unpacking the entire payload.</span></span> <span data-ttu-id="eb84e-105">Die Aktivitäten werden über eine URL ähnlich https://<your_domain>/api/messages an den Bot gesendet.</span><span class="sxs-lookup"><span data-stu-id="eb84e-105">The activities are sent to the bot through a URL similar to https://<your_domain>/api/messages.</span></span> <span data-ttu-id="eb84e-106">Es werden Anforderungen empfangen, um die Konversations- und Mandanten-ID in den Kopfzeilen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="eb84e-106">Requests are received to show the conversation ID and tenant ID in the headers.</span></span>

## <a name="request-header-fields"></a><span data-ttu-id="eb84e-107">Anforderungskopffelder</span><span class="sxs-lookup"><span data-stu-id="eb84e-107">Request header fields</span></span>

<span data-ttu-id="eb84e-108">Allen Anfordern, die an Bots gesendet werden, werden zwei nicht standardmäßige Anforderungsheaderfelder hinzugefügt, sowohl für den asynchronen- als auch für den synchronen Fluss.</span><span class="sxs-lookup"><span data-stu-id="eb84e-108">Two non-standard request header fields are added to all the requests sent to bots, for both asynchronous flow and synchronous flow.</span></span> <span data-ttu-id="eb84e-109">Die folgende Tabelle enthält die Anforderungsheaderfelder und deren Werte:</span><span class="sxs-lookup"><span data-stu-id="eb84e-109">The following table provides the request header fields and their values:</span></span>

| <span data-ttu-id="eb84e-110">Feldschlüssel</span><span class="sxs-lookup"><span data-stu-id="eb84e-110">Field key</span></span> | <span data-ttu-id="eb84e-111">Wert</span><span class="sxs-lookup"><span data-stu-id="eb84e-111">Value</span></span> |
|----------------|-----------------|
| <span data-ttu-id="eb84e-112">x-ms-conversation-id</span><span class="sxs-lookup"><span data-stu-id="eb84e-112">x-ms-conversation-id</span></span> | <span data-ttu-id="eb84e-113">Die Gesprächs-ID, die ggf. der Anforderungsaktivität entspricht, und bestätigt oder überprüft.</span><span class="sxs-lookup"><span data-stu-id="eb84e-113">The conversation ID corresponding to the request activity if applicable and confirmed or verified.</span></span> |
| <span data-ttu-id="eb84e-114">x-ms-tenant-id</span><span class="sxs-lookup"><span data-stu-id="eb84e-114">x-ms-tenant-id</span></span> | <span data-ttu-id="eb84e-115">Die Mandanten-ID, die der Unterhaltung in der Anforderungsaktivität entspricht.</span><span class="sxs-lookup"><span data-stu-id="eb84e-115">The tenant ID corresponding to the conversation in the request activity.</span></span> |

<span data-ttu-id="eb84e-116">Wenn der Mandant oder die Unterhaltungs-ID in der Aktivität nicht vorhanden ist oder auf der Dienstseite nicht überprüft wurde, ist der Wert leer.</span><span class="sxs-lookup"><span data-stu-id="eb84e-116">If the tenant or conversation ID is not present in the activity or was not validated on the service side, the value is empty.</span></span>

![Anforderungskopffelder](~/assets/images/bots/requestheaderfields.png)
