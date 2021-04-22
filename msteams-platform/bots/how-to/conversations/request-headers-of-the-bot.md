---
title: Senden von Mandanten-ID und Unterhaltungs-ID an die Anforderungskopfzeilen des Bots
description: beschreibt, wie Mandanten-ID und Unterhaltungs-ID an die Anforderungskopfzeilen des Bots gesendet werden.
ms.topic: conceptual
localization_priority: Normal
ms.openlocfilehash: b3938b3011e09016f8594b2b17ba627d4922947b
ms.sourcegitcommit: 35bc2a31b92f3f7c6524373108f095a870d9ad09
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/21/2021
ms.locfileid: "51922528"
---
# <a name="send-tenant-id-and-conversation-id-to-the-request-headers-of-the-bot"></a><span data-ttu-id="d6f90-103">Senden von Mandanten-ID und Unterhaltungs-ID an die Anforderungskopfzeilen des Bots</span><span class="sxs-lookup"><span data-stu-id="d6f90-103">Send tenant ID and conversation ID to the request headers of the bot</span></span>

<span data-ttu-id="d6f90-104">Die aktuellen ausgehenden Anforderungen an den Bot enthalten in der Kopfzeile oder URL keine Informationen, die Bots dabei helfen, den Datenverkehr weiter zu routen, ohne die gesamte Nutzlast auszupacken.</span><span class="sxs-lookup"><span data-stu-id="d6f90-104">The current outgoing requests to the bot do not contain in the header or URL any information that helps bots route the traffic without unpacking the entire payload.</span></span> <span data-ttu-id="d6f90-105">Die Aktivitäten werden über eine URL wie https://<your_domain>/api/messages an den Bot gesendet.</span><span class="sxs-lookup"><span data-stu-id="d6f90-105">The activities are sent to the bot through a URL similar to https://<your_domain>/api/messages.</span></span> <span data-ttu-id="d6f90-106">Es werden Anforderungen zum Anzeigen der Unterhaltungs-ID und der Mandanten-ID in den Kopfzeilen empfangen.</span><span class="sxs-lookup"><span data-stu-id="d6f90-106">Requests are received to show the conversation ID and tenant ID in the headers.</span></span>

## <a name="request-header-fields"></a><span data-ttu-id="d6f90-107">Anforderungskopffelder</span><span class="sxs-lookup"><span data-stu-id="d6f90-107">Request header fields</span></span>

<span data-ttu-id="d6f90-108">Allen Anforderungen, die an Bots gesendet werden, werden zwei nicht standardmäßige Anforderungskopffelder hinzugefügt, sowohl für den asynchronen als auch für den synchronen Fluss.</span><span class="sxs-lookup"><span data-stu-id="d6f90-108">Two non-standard request header fields are added to all the requests sent to bots, for both asynchronous flow and synchronous flow.</span></span> <span data-ttu-id="d6f90-109">Die folgende Tabelle enthält die Anforderungskopffelder und deren Werte.</span><span class="sxs-lookup"><span data-stu-id="d6f90-109">The following table provides the request header fields and their values.</span></span>

| <span data-ttu-id="d6f90-110">Feldtaste</span><span class="sxs-lookup"><span data-stu-id="d6f90-110">Field key</span></span> | <span data-ttu-id="d6f90-111">Wert</span><span class="sxs-lookup"><span data-stu-id="d6f90-111">Value</span></span> |
|----------------|-----------------|
| <span data-ttu-id="d6f90-112">x-ms-conversation-id</span><span class="sxs-lookup"><span data-stu-id="d6f90-112">x-ms-conversation-id</span></span> | <span data-ttu-id="d6f90-113">Die Unterhaltungs-ID, die der Anforderungsaktivität entspricht, sofern zutreffend und bestätigt oder überprüft.</span><span class="sxs-lookup"><span data-stu-id="d6f90-113">The conversation ID corresponding to the request activity if applicable and confirmed or verified.</span></span> |
| <span data-ttu-id="d6f90-114">x-ms-tenant-id</span><span class="sxs-lookup"><span data-stu-id="d6f90-114">x-ms-tenant-id</span></span> | <span data-ttu-id="d6f90-115">Die Mandanten-ID, die der Unterhaltung in der Anforderungsaktivität entspricht.</span><span class="sxs-lookup"><span data-stu-id="d6f90-115">The tenant ID corresponding to the conversation in the request activity.</span></span> |

<span data-ttu-id="d6f90-116">Wenn der Mandant oder die Unterhaltungs-ID nicht in der Aktivität vorhanden ist oder auf Dienstseite nicht überprüft wurde, ist der Wert leer.</span><span class="sxs-lookup"><span data-stu-id="d6f90-116">If the tenant or conversation ID is not present in the activity or was not validated on the service side, the value is empty.</span></span>

![Anforderungskopffelder](~/assets/images/bots/requestheaderfields.png)
