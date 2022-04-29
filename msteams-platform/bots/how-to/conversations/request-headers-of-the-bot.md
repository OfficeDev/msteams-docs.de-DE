---
title: Senden der Mandanten-ID und Konversations-ID an die Anforderungsheader des Bots
description: Beschreibt, wie die Mandanten-ID und Unterhaltungs-ID an die Anforderungsheader des Bots gesendet werden.
ms.topic: conceptual
ms.localizationpriority: high
ms.openlocfilehash: 9b63dd81eeccbf78989a31a06baa5d678916acef
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111290"
---
# <a name="send-tenant-id-and-conversation-id-to-the-request-headers-of-the-bot"></a>Senden der Mandanten-ID und Konversations-ID an die Anforderungsheader des Bots

Die aktuellen ausgehenden Anforderungen an den Bot enthalten im Header oder in der URL keine Informationen, die Bots beim Weiterleiten des Datenverkehrs unterstützen, ohne die gesamte Nutzlast zu entpacken. Die Aktivitäten werden über eine URL ähnlich wie https://<Ihre_Domäne>/api/messages an den Bot gesendet. Anforderungen werden empfangen, um die Unterhaltungs-ID und Mandanten-ID in den Headern anzuzeigen.

## <a name="request-header-fields"></a>Anforderungsheaderfelder

Zwei nicht standardmäßige Anforderungsheaderfelder werden allen Anforderungen hinzugefügt, die an Bots gesendet werden, sowohl für asynchronen Fluss als auch für synchronen Fluss. Die folgende Tabelle enthält die Anforderungsheaderfelder und deren Werte:

| Feldschlüssel | Wert |
|----------------|-----------------|
| x-ms-conversation-id | Die Unterhaltungs-ID, die der Anforderungsaktivität entspricht, falls zutreffend und bestätigt oder überprüft. |
| x-ms-tenant-id | Die Mandanten-ID, die der Unterhaltung in der Anforderungsaktivität entspricht. |

Wenn die Mandanten- oder Unterhaltungs-ID nicht in der Aktivität vorhanden ist oder auf Dienstseite nicht überprüft wurde, ist der Wert leer.

![Anforderungsheaderfelder](~/assets/images/bots/requestheaderfields.png)
