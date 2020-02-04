---
title: Was sind webhooks und Connectors?
author: clearab
description: Erfahren Sie, wie webhooks und Connectors ihre Webdienste mit dem Microsoft Teams-Client verbinden können.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 2be6f82bba0efe05a22a8da9da0acc1e0ad6fa00
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674071"
---
# <a name="what-are-webhooks-and-connectors"></a>Was sind webhooks und Connectors?

Webhooks und Connectors sind eine einfache Möglichkeit, um Ihre Webdienste mit Kanälen und Teams in Microsoft Teams zu verbinden. 

## <a name="outgoing-webhooks"></a>Ausgehende webhooks

Ausgehende webhooks ermöglichen Ihren Benutzern das Senden von Textnachrichten von einem Kanal an Ihre Webdienste. Nachdem die Benutzer konfiguriert wurden, können Sie Ihren ausgehenden webhook @mention und eine Nachricht an Ihren Dienst senden. Ihr Dienst kann fünf Sekunden lang eine Antwort auf die Nachricht senden, die möglicherweise Text oder eine Karte enthält.

Ausgehende webhooks werden pro Team konfiguriert, können nicht als Teil einer normalen Teams-App eingeschlossen werden. Sie eignen sich am besten für die Ausführung Team spezifischer Arbeitsauslastungen, für die keine großen Datenmengen gesammelt oder ausgetauscht werden müssen.

Weitere Informationen finden Sie unter [Create an Outgoing webhook](~/webhooks-and-connectors/how-to/add-outgoing-webhook.md).

## <a name="connectors"></a>Connectors

Connectors ermöglichen Benutzern das Abonnieren von Benachrichtigungen und Nachrichten von ihren Webdiensten. Sie stellen einen HTTPS-Endpunkt für Ihren Dienst zur Verfügung, um Nachrichten in der Regel in Form von Karten zu veröffentlichen.

### <a name="incoming-webhooks"></a>Eingehende webhooks

Eingehende webhooks sind die einfachste Art von Connector. Für jeden Kanal im Team (wenn diese für dieses Team aktiviert sind) können Sie einen HTTPS-Endpunkt verfügbar machen, der ordnungsgemäß formatierte JSON akzeptiert und Nachrichten in diesen Kanal einfügt. Sie stellen eine schnelle und einfache Möglichkeit dar, einen Kanal mit Ihrem Dienst zu verbinden, und werden am besten für Szenarien verwendet, die für ein bestimmtes Team eindeutig sind. Sie können beispielsweise einen eingehenden webhook in Ihrem DevOps-Kanal erstellen und ihre Build-, Bereitstellungs-und Überwachungsdienste so konfigurieren, dass Warnungen gesendet werden.

Siehe [Erstellen eines eingehenden webhooks](~/webhooks-and-connectors/how-to/add-incoming-webhook.md).

### <a name="office-365-connectors"></a>Office 365-Connectors

Office 365-Konnektoren ermöglichen es Ihnen, eine benutzerdefinierte Konfigurationsseite für den eingehenden webhook zu erstellen und diese als Teil einer Teams-APP zu verpacken. Sie können diese APP dann breiter oder sogar in unserem App-Store verteilen. Sie senden Nachrichten in erster Linie mit Office 365-connectorkarten und haben auch die Möglichkeit, Ihnen eine Reihe von Karten Aktionen hinzuzufügen. Ein gutes Beispiel hierfür ist ein Wetter-Konnektor, mit dem Benutzer einen Standort und eine Tageszeit auswählen können, um Updates über das Wetter von morgen zu erhalten. Sie werden auf Kanalebene konfiguriert, aber auf Teamebene installiert.

Weitere Informationen finden Sie unter [Erstellen eines Office 365-Konnektors](~/webhooks-and-connectors/how-to/connectors-creating.md).