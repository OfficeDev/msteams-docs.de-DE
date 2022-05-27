---
title: Senden der Mandanten-ID und Konversations-ID an die Anforderungsheader des Bots
description: Beschreibt, wie die Mandanten-ID und Unterhaltungs-ID an die Anforderungsheader des Bots gesendet werden.
ms.topic: conceptual
ms.localizationpriority: medium
ms.openlocfilehash: 8aca2c11dbdfc84abe8c4d0ec40e2748d04f6301
ms.sourcegitcommit: eeaa8cbb10b9dfa97e9c8e169e9940ddfe683a7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2022
ms.locfileid: "65757290"
---
# <a name="send-tenant-id-and-conversation-id-to-the-request-headers-of-the-bot"></a>Senden der Mandanten-ID und Konversations-ID an die Anforderungsheader des Bots

Die aktuellen ausgehenden Anforderungen an den Bot enthalten in der Kopfzeile oder URL keine Informationen, die Bots dabei helfen, den Datenverkehr weiterzuleiten, ohne die gesamte Nutzlast auszupacken. Die Aktivitäten werden über eine URL ähnlich wie https://<Ihre_Domäne>/api/messages an den Bot gesendet. Anforderungen werden empfangen, um die Unterhaltungs-ID und Mandanten-ID in den Headern anzuzeigen.

## <a name="request-header-fields"></a>Anforderungsheaderfelder

Zwei nicht standardmäßige Anforderungsheaderfelder werden allen Anforderungen hinzugefügt, die an Bots gesendet werden, sowohl für asynchronen Fluss als auch für synchronen Fluss. Die folgende Tabelle enthält die Anforderungsheaderfelder und deren Werte:

| Feldschlüssel | Wert |
|----------------|-----------------|
| x-ms-conversation-id | Die Unterhaltungs-ID, die der Anforderungsaktivität entspricht, falls zutreffend und bestätigt oder überprüft. |
| x-ms-tenant-id | Die Mandanten-ID, die der Unterhaltung in der Anforderungsaktivität entspricht. |

Wenn der Mandant oder die Unterhaltungs-ID in der Aktivität nicht vorhanden ist oder auf dienstseitiger Seite nicht überprüft wurde, ist der Wert leer.

![Anforderungsheaderfelder](~/assets/images/bots/requestheaderfields.png)
