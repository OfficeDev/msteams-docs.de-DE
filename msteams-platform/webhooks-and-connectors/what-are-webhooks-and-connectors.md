---
title: Was sind Webhooks und Connectors?
author: clearab
description: Verstehen Sie, wie Webhooks und Connectors Ihre Webdienste mit dem Teams Client verbinden können.
localization_priority: Normal
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: e36b73c0eaed5068311dae6c1ef8fdc073432334
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566803"
---
# <a name="what-are-webhooks-and-connectors"></a>Was sind Webhooks und Connectors?

Webhooks und Connectors sind eine einfache Möglichkeit, um Ihre Webdienste mit Kanälen und Teams in Microsoft Teams zu verbinden. 

## <a name="outgoing-webhooks"></a>Ausgehende Webhooks

Ausgehende Webhooks ermöglichen Benutzern das Senden von Textnachrichten aus einem Kanal an Ihre Webdienste. Nach der Konfiguration können Ihre Benutzer Ihren ausgehenden Webhook @mention und eine Nachricht an Ihren Dienst senden. Ihr Dienst hat fünf Sekunden Zeit, um eine Antwort auf die Nachricht zu senden, die möglicherweise Text oder eine Karte enthält.

Ausgehende Webhooks werden pro Team konfiguriert und können nicht als Teil einer normalen Teams App aufgenommen werden. Sie eignen sich am besten zum Abschließen teamspezifischer Workloads, für die keine großen Mengen an Informationen gesammelt oder ausgetauscht werden müssen.

Weitere Informationen finden Sie unter [Erstellen eines ausgehenden Webhooks](~/webhooks-and-connectors/how-to/add-outgoing-webhook.md).

## <a name="connectors"></a>Connectors

Connectors ermöglichen Benutzern, Benachrichtigungen und Nachrichten von Ihren Webdiensten zu abonnieren. Sie machen einen HTTPS-Endpunkt verfügbar, an den Ihr Dienst Nachrichten senden kann - in der Regel in Form von Karten.

### <a name="incoming-webhooks"></a>Eingehende Webhooks

Eingehende Webhooks sind der einfachste Connectortyp. Für jeden Kanal im Team (wenn sie für dieses Team aktiviert sind) können Sie einen HTTPS-Endpunkt verfügbar machen, der korrekt formatierte JSON akzeptiert und Nachrichten in diesen Kanal einfügt. Sie sind eine schnelle und einfache Möglichkeit, einen Kanal mit Ihrem Dienst zu verbinden, und eignen sich am besten für Szenarien, die für ein bestimmtes Team einzigartig sind. Sie können z. B. einen eingehenden Webhook in Ihrem DevOps Kanal erstellen und Ihre Build-, Bereitstellungs- und Überwachungsdienste so konfigurieren, dass Warnungen gesendet werden.

Weitere Informationen finden Sie unter [Erstellen eines eingehenden Webhooks](~/webhooks-and-connectors/how-to/add-incoming-webhook.md).

### <a name="office-365-connectors"></a>Office 365-Connectors

Office 365 Mit Connectors können Sie eine benutzerdefinierte Konfigurationsseite für Ihren eingehenden Webhook erstellen und als Teil einer Teams-App verpacken. Sie können diese App dann breiter oder sogar in unserem App Store verteilen. Sie senden Nachrichten hauptsächlich mit Office 365 Connectorkarten und haben die Möglichkeit, ihnen auch einen begrenzten Satz von Kartenaktionen hinzuzufügen. Ein gutes Beispiel dafür ist ein Wetteranschluss, mit dem Benutzer einen Ort und eine Tageszeit auswählen können, um Updates über das Wetter von morgen zu erhalten. Sie sind auf Kanalebene konfiguriert, werden jedoch auf Teamebene installiert.

Weitere Informationen finden Sie unter [Erstellen eines Office 365 Connectors](~/webhooks-and-connectors/how-to/connectors-creating.md).
