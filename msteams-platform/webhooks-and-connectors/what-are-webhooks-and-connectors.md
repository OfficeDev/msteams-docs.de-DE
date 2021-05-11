---
title: Was sind Webhooks und Connectors?
author: clearab
description: Erfahren Sie, wie Webhooks und Connectors Ihre Webdienste mit dem client Teams können.
localization_priority: Normal
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 6ab1abc33ca7b0280892646bed52d9ee77a8c865
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52018362"
---
# <a name="what-are-webhooks-and-connectors"></a>Was sind Webhooks und Connectors?

Webhooks und Connectors sind eine einfache Möglichkeit, um Ihre Webdienste mit Kanälen und Teams in Microsoft Teams zu verbinden. 

## <a name="outgoing-webhooks"></a>Ausgehende Webhooks

Ausgehende Webhooks ermöglichen Benutzern das Senden von Textnachrichten aus einem Kanal an Ihre Webdienste. Nach der Konfiguration können Ihre Benutzer @mention ausgehenden Webhook senden und eine Nachricht an Ihren Dienst senden. Ihr Dienst hat fünf Sekunden Zeit, um eine Antwort auf die Nachricht zu senden, die möglicherweise Text oder eine Karte enthält.

Ausgehende Webhooks werden pro Team konfiguriert und können nicht als Teil einer normalen Teams werden. Sie eignen sich am besten zum Abschließen teamspezifischer Arbeitsauslastungen, für die keine großen Mengen von Informationen gesammelt oder ausgetauscht werden müssen.

Weitere [Informationen finden Sie unter Create an outgoing webhook](~/webhooks-and-connectors/how-to/add-outgoing-webhook.md).

## <a name="connectors"></a>Connectors

Connectors ermöglichen Benutzern, Benachrichtigungen und Nachrichten von Ihren Webdiensten zu abonnieren. Sie machen einen HTTPS-Endpunkt für Ihren Dienst zum Posten von Nachrichten verfügbar – in der Regel in Form von Karten.

### <a name="incoming-webhooks"></a>Eingehende Webhooks

Eingehende Webhooks sind der einfachste Connectortyp. Für jeden Kanal im Team (sofern er für dieses Team aktiviert ist) können Sie einen HTTPS-Endpunkt verfügbar machen, der korrekt formatierte JSON akzeptiert und Nachrichten in diesen Kanal einfüge. Sie sind eine schnelle und einfache Möglichkeit, einen Kanal mit Ihrem Dienst zu verbinden, und werden am besten für Szenarien verwendet, die für ein bestimmtes Team einzigartig sind. Sie können beispielsweise einen eingehenden Webhook in Ihrem DevOps erstellen und Ihre Build-, Bereitstellungs- und Überwachungsdienste für das Senden von Warnungen konfigurieren.

Weitere [Informationen finden Sie unter Create an incoming webhook](~/webhooks-and-connectors/how-to/add-incoming-webhook.md).

### <a name="office-365-connectors"></a>Office 365-Connectors

Office 365 Mit Connectors können Sie eine benutzerdefinierte Konfigurationsseite für Ihren eingehenden Webhook erstellen und als Teil einer Teams packen. Sie können diese App dann breiter verteilen oder sogar an unseren App Store. Sie senden Nachrichten in erster Linie Office 365 Connectorkarten und können ihnen auch eine begrenzte Anzahl von Kartenaktionen hinzufügen. Ein gutes Beispiel dafür ist ein Wetterconnector, mit dem Benutzer einen Ort und eine Uhrzeit auswählen können, um Updates über das Wetter von morgen zu erhalten. Sie werden auf Kanalebene konfiguriert, aber auf Teamebene installiert.

Weitere [Informationen finden Sie unter](~/webhooks-and-connectors/how-to/connectors-creating.md)Create an Office 365 Connector .
