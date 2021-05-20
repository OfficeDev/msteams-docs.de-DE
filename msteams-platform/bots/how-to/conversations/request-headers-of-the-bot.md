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
# <a name="send-tenant-id-and-conversation-id-to-the-request-headers-of-the-bot"></a>Senden der Mandanten-ID und der Konversations-ID an die Anforderungsheader des Bots

Die aktuellen ausgehenden Anforderungen an den Bot enthalten keine Informationen im Header oder URL, die Bots dabei helfen, den Datenverkehr weiterzuleiten, ohne die gesamte Nutzlast zu entpacken. Die Aktivitäten werden über eine URL ähnlich https://<your_domain>/api/messages an den Bot gesendet. Es werden Anforderungen empfangen, um die Konversations- und Mandanten-ID in den Kopfzeilen anzuzeigen.

## <a name="request-header-fields"></a>Anforderungskopffelder

Allen Anfordern, die an Bots gesendet werden, werden zwei nicht standardmäßige Anforderungsheaderfelder hinzugefügt, sowohl für den asynchronen- als auch für den synchronen Fluss. Die folgende Tabelle enthält die Anforderungsheaderfelder und deren Werte:

| Feldschlüssel | Wert |
|----------------|-----------------|
| x-ms-conversation-id | Die Gesprächs-ID, die ggf. der Anforderungsaktivität entspricht, und bestätigt oder überprüft. |
| x-ms-tenant-id | Die Mandanten-ID, die der Unterhaltung in der Anforderungsaktivität entspricht. |

Wenn der Mandant oder die Unterhaltungs-ID in der Aktivität nicht vorhanden ist oder auf der Dienstseite nicht überprüft wurde, ist der Wert leer.

![Anforderungskopffelder](~/assets/images/bots/requestheaderfields.png)
