---
title: Senden der Mandanten-ID und Konversations-ID an die Anforderungsheader des Bots
description: Erfahren Sie, wie Sie den Bot-Datenverkehr weiterleiten, ohne die gesamte Nutzlast mithilfe der Mandanten-ID und Unterhaltungs-ID auszupacken, die in Anforderungsheadern des Bots in Teams vorhanden sind.
ms.topic: conceptual
ms.localizationpriority: medium
ms.openlocfilehash: 3132d91d4b3d0b290ee8e1fb35ebeea076217fe8
ms.sourcegitcommit: 75d0072c021609af33ce584d671f610d78b3aaef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2022
ms.locfileid: "68100147"
---
# <a name="request-headers-of-the-bot"></a>Anfordern von Kopfzeilen des Bots

Die aktuellen ausgehenden Anforderungen an den Bot enthalten in der Kopfzeile oder URL keine Informationen, die Bots dabei helfen, den Datenverkehr weiterzuleiten, ohne die gesamte Nutzlast auszupacken. Die Aktivitäten werden über eine URL ähnlich wie https://<Ihre_Domäne>/api/messages an den Bot gesendet. Anforderungen werden empfangen, um die Unterhaltungs-ID und Mandanten-ID in den Headern anzuzeigen.

## <a name="request-header-fields"></a>Anforderungsheaderfelder

Zwei nicht standardmäßige Anforderungsheaderfelder werden allen Anforderungen hinzugefügt, die an Bots gesendet werden, sowohl für asynchronen Fluss als auch für synchronen Fluss. Die folgende Tabelle enthält die Anforderungsheaderfelder und deren Werte:

| Feldschlüssel | Wert |
|----------------|-----------------|
| x-ms-conversation-id | Die Unterhaltungs-ID, die der Anforderungsaktivität entspricht, falls zutreffend und bestätigt oder überprüft. |
| x-ms-tenant-id | Die Mandanten-ID, die der Unterhaltung in der Anforderungsaktivität entspricht. |

Wenn der Mandant oder die Unterhaltungs-ID in der Aktivität nicht vorhanden ist oder auf dienstseitiger Seite nicht überprüft wurde, ist der Wert leer.

![Anforderungsheaderfelder](~/assets/images/bots/requestheaderfields.png)
