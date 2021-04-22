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
# <a name="send-tenant-id-and-conversation-id-to-the-request-headers-of-the-bot"></a>Senden von Mandanten-ID und Unterhaltungs-ID an die Anforderungskopfzeilen des Bots

Die aktuellen ausgehenden Anforderungen an den Bot enthalten in der Kopfzeile oder URL keine Informationen, die Bots dabei helfen, den Datenverkehr weiter zu routen, ohne die gesamte Nutzlast auszupacken. Die Aktivitäten werden über eine URL wie https://<your_domain>/api/messages an den Bot gesendet. Es werden Anforderungen zum Anzeigen der Unterhaltungs-ID und der Mandanten-ID in den Kopfzeilen empfangen.

## <a name="request-header-fields"></a>Anforderungskopffelder

Allen Anforderungen, die an Bots gesendet werden, werden zwei nicht standardmäßige Anforderungskopffelder hinzugefügt, sowohl für den asynchronen als auch für den synchronen Fluss. Die folgende Tabelle enthält die Anforderungskopffelder und deren Werte.

| Feldtaste | Wert |
|----------------|-----------------|
| x-ms-conversation-id | Die Unterhaltungs-ID, die der Anforderungsaktivität entspricht, sofern zutreffend und bestätigt oder überprüft. |
| x-ms-tenant-id | Die Mandanten-ID, die der Unterhaltung in der Anforderungsaktivität entspricht. |

Wenn der Mandant oder die Unterhaltungs-ID nicht in der Aktivität vorhanden ist oder auf Dienstseite nicht überprüft wurde, ist der Wert leer.

![Anforderungskopffelder](~/assets/images/bots/requestheaderfields.png)
