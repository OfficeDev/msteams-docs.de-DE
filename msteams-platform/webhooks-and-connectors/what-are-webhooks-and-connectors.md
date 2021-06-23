---
title: Was sind Webhooks und Connectors?
author: surbhigupta
description: Erfahren Sie, wie Webhooks und Connectors Ihre Webdienste mit dem Teams-Client verbinden können.
localization_priority: Normal
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 3e8105c9f069428bf93fb9bc2533895878f5ded1
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "53069041"
---
# <a name="what-are-webhooks-and-connectors"></a>Was sind Webhooks und Connectors?

Webhooks und Connectors sind eine einfache Möglichkeit, um Ihre Webdienste mit Kanälen und Teams in Microsoft Teams zu verbinden. 

## <a name="outgoing-webhooks"></a>Ausgehende Webhooks

Ausgehende Webhooks ermöglichen Benutzern das Senden von Textnachrichten aus einem Kanal an Ihre Webdienste. Nach der Konfiguration können Ihre Benutzer Ihren ausgehenden Webhook @mention und eine Nachricht an Ihren Dienst senden. Ihr Dienst hat fünf Sekunden Zeit, um eine Antwort auf die Nachricht zu senden, die möglicherweise Text oder eine Karte enthält.

Ausgehende Webhooks werden pro Team konfiguriert und können nicht als Teil einer normalen Teams-App eingeschlossen werden. Sie eignen sich am besten zum Abschließen teamspezifischer Workloads, für die keine großen Mengen von Informationen gesammelt oder ausgetauscht werden müssen.

Weitere Informationen finden Sie unter [Erstellen eines ausgehenden Webhooks.](~/webhooks-and-connectors/how-to/add-outgoing-webhook.md)

## <a name="connectors"></a>Connectors

Connectors ermöglichen Benutzern, Benachrichtigungen und Nachrichten von Ihren Webdiensten zu abonnieren. Sie stellen einen HTTPS-Endpunkt für Ihren Dienst bereit, an den Nachrichten gesendet werden sollen – in der Regel in Form von Karten.

### <a name="incoming-webhooks"></a>Eingehende Webhooks

Eingehende Webhooks sind der einfachste Connectortyp. Für jeden Kanal im Team (wenn sie für dieses Team aktiviert sind) können Sie einen HTTPS-Endpunkt verfügbar machen, der korrekt formatierte JSON akzeptiert und Nachrichten in diesen Kanal einfügt. Sie sind eine schnelle und einfache Möglichkeit, einen Kanal mit Ihrem Dienst zu verbinden, und werden am besten für Szenarien verwendet, die für ein bestimmtes Team einzigartig sind. Sie können beispielsweise einen eingehenden Webhook in Ihrem DevOps Kanal erstellen und Ihre Build-, Bereitstellungs- und Überwachungsdienste so konfigurieren, dass Warnungen gesendet werden.

Weitere Informationen finden Sie unter [Erstellen eines eingehenden Webhooks.](~/webhooks-and-connectors/how-to/add-incoming-webhook.md)

### <a name="office-365-connectors"></a>Office 365-Connectors

Office 365 Connectors ermöglichen es Ihnen, eine benutzerdefinierte Konfigurationsseite für Ihren eingehenden Webhook zu erstellen und diese als Teil einer Teams-App zu verpacken. Sie können diese App dann umfassender oder sogar in unserem App Store verteilen. Sie senden Nachrichten in erster Linie mit Office 365 Connectorkarten und können ihnen auch eine begrenzte Anzahl von Kartenaktionen hinzufügen. Ein gutes Beispiel hierfür ist ein Wetterconnector, mit dem Benutzer einen Ort und eine Uhrzeit auswählen können, um Updates über das Wetter von morgen zu erhalten. Sie werden auf Kanalebene konfiguriert, aber auf Teamebene installiert.

Weitere Informationen finden Sie unter [Erstellen eines Office 365 Connectors.](~/webhooks-and-connectors/how-to/connectors-creating.md)
