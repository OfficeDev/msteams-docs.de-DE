---
title: Senden von Mandanten-ID und Unterhaltungs-ID an die Anforderungsheader des Bots
description: beschreibt, wie Mandant-ID und Unterhaltungs-ID an die Anforderungsheader des Bots gesendet werden.
ms.topic: conceptual
localization_priority: Normal
ms.openlocfilehash: a775c09589f59a6d487bf403544afccd5b59f797ac12cf60a9deb1fc2de16644
ms.sourcegitcommit: 3ab1cbec41b9783a7abba1e0870a67831282c3b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2021
ms.locfileid: "57706670"
---
# <a name="send-tenant-id-and-conversation-id-to-the-request-headers-of-the-bot"></a>Senden von Mandanten-ID und Unterhaltungs-ID an die Anforderungsheader des Bots

Die aktuellen ausgehenden Anforderungen an den Bot enthalten keine Informationen in der Kopfzeile oder URL, die Bots dabei helfen, den Datenverkehr weiterzuleiten, ohne die gesamte Nutzlast zu entpacken. Die Aktivitäten werden über eine URL wie https://<your_domain>/api/messages an den Bot gesendet. Es werden Anforderungen empfangen, um die Unterhaltungs-ID und mandanten-ID in den Kopfzeilen anzuzeigen.

## <a name="request-header-fields"></a>Anforderungsheaderfelder

Allen an Bots gesendeten Anforderungen werden zwei nicht standardmäßige Anforderungsheaderfelder hinzugefügt, sowohl für den asynchronen als auch für den synchronen Fluss. Die folgende Tabelle enthält die Anforderungsheaderfelder und deren Werte:

| Feldtaste | Wert |
|----------------|-----------------|
| x-ms-conversation-id | Die Unterhaltungs-ID, die der Anforderungsaktivität entspricht, falls zutreffend und bestätigt oder bestätigt. |
| x-ms-tenant-id | Die Mandanten-ID, die der Unterhaltung in der Anforderungsaktivität entspricht. |

Wenn der Mandant oder die Unterhaltungs-ID in der Aktivität nicht vorhanden ist oder auf Dienstseite nicht überprüft wurde, ist der Wert leer.

![Anforderungsheaderfelder](~/assets/images/bots/requestheaderfields.png)
