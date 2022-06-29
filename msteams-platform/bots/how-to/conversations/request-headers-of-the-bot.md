---
title: Senden der Mandanten-ID und Konversations-ID an die Anforderungsheader des Bots
description: In diesem Modul erfahren Sie, wie Sie Mandanten-ID und Unterhaltungs-ID an die Anforderungsheader des Bots in Teams senden.
ms.topic: conceptual
ms.localizationpriority: medium
ms.openlocfilehash: b292db11ced764bbe235bee0f6f8f4829ba7b6c9
ms.sourcegitcommit: ffc57e128f0ae21ad2144ced93db7c78a5ae25c4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2022
ms.locfileid: "66503774"
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
