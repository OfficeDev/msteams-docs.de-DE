---
title: Senden der Mandanten-ID und Konversations-ID an die Anforderungsheader des Bots
description: In diesem Modul erfahren Sie, wie Sie mandanten-ID und Unterhaltungs-ID an die Anforderungsheader des Bots in Teams senden.
ms.topic: conceptual
ms.localizationpriority: medium
ms.openlocfilehash: dab795a65cf1c6d62bd899c9fa5a5948c44fcdfb
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2022
ms.locfileid: "66144124"
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
