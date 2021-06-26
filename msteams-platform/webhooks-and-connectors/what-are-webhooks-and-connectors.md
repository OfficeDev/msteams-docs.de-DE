---
title: Webhooks und Connectors
author: clearab
description: Erfahren Sie, wie Webhooks und Connectors Ihre Webdienste mit dem Teams-Client verbinden können.
localization_priority: Normal
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 2cb763a6637abd3faa500de871119f0b829871bf
ms.sourcegitcommit: 4d9d1542e04abacfb252511c665a7229d8bb7162
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2021
ms.locfileid: "53140054"
---
# <a name="webhooks-and-connectors"></a>Webhooks und Connectors

Webhooks und Connectors helfen beim Verbinden der Webdienste mit Kanälen und Teams in Microsoft Teams. Webhooks sind benutzerdefinierte HTTP-Rückrufe, mit denen Benutzer über alle Aktionen benachrichtigt werden, die im Microsoft Teams Kanal ausgeführt wurden. Es ist eine Möglichkeit für eine App, Echtzeitdaten abzurufen. Connectors ermöglichen Benutzern, Benachrichtigungen und Nachrichten von Ihren Webdiensten zu abonnieren. Sie stellen einen HTTPS-Endpunkt für Ihren Dienst bereit, um Nachrichten in Form von Karten zu posten.

## <a name="outgoing-webhooks"></a>Ausgehende Webhooks

Webhooks helfen Teams bei der Integration in externe Apps. Mit ausgehenden Webhooks können Sie Textnachrichten von einem Kanal an die Webdienste senden. Nach dem Konfigurieren der ausgehenden Webhooks können Benutzer ausgehenden Webhook @mention und eine Nachricht an Webdienste senden. Der Dienst antwortet innerhalb von zehn Sekunden mit einem Text oder einer Karte auf die Nachricht.

> [!NOTE]
> Ausgehende Webhooks werden pro Team konfiguriert und können nicht als Teil einer normalen Teams-App eingeschlossen werden.

## <a name="connectors"></a>Connectors

Connectors ermöglichen Benutzern das Abonnieren von Benachrichtigungen und Nachrichten von webdiensten. Sie machen den HTTPS-Endpunkt für den Dienst verfügbar, um Nachrichten in Teams Kanälen zu posten, in der Regel in Form von Karten.

### <a name="incoming-webhooks"></a>Eingehende Webhooks

Eingehende Webhooks helfen beim Veröffentlichen von Nachrichten von Apps an Teams. Wenn eingehende Webhooks für ein Team in einem beliebigen Kanal aktiviert sind, wird der HTTPS-Endpunkt verfügbar gemacht, der korrekt formatierte JSON akzeptiert und die Nachrichten in diesen Kanal einfügt. Sie können beispielsweise einen eingehenden Webhook in Ihrem DevOps Kanal erstellen, Ihren Build konfigurieren und gleichzeitig Dienste bereitstellen und überwachen, um Warnungen zu senden.

### <a name="office-365-connectors"></a>Office 365-Connectors

Office 365 Mit Connectors können Sie eine benutzerdefinierte Konfigurationsseite für Ihren eingehenden Webhook erstellen und diese als Teil einer Teams-App verpacken. Sie senden Nachrichten in erster Linie mit Office 365 Connectorkarten und haben die Möglichkeit, ihnen eine begrenzte Anzahl von Kartenaktionen hinzuzufügen. Beispielsweise ein Wetterconnector, mit dem Benutzer einen Ort und eine Uhrzeit auswählen können, um Updates über das Wetter von morgen zu erhalten. Sie werden auf Kanalebene konfiguriert, aber auf Teamebene installiert.

> [!NOTE]
> Sie können den Office 365 Connector Teams App an unseren AppStore verteilen.

## <a name="create-and-send-messages"></a>Erstellen und Senden von Nachrichten

Nachrichten mit Aktionen ermöglichen Es Benutzern, Maßnahmen zu ergreifen, ohne ihren E-Mail-Client zu verlassen, was die Benutzerbindung erhöht. Mit Office 365 und eingehenden Webhooks können Sie Nachrichten senden, indem Sie eine JSON-Nutzlast an die Webhook-URL senden.

## <a name="see-also"></a>Siehe auch

* [Erstellen eines eingehenden Webhooks](~/webhooks-and-connectors/how-to/add-incoming-webhook.md)
* [Erstellen eines Office 365-Connectors](~/webhooks-and-connectors/how-to/connectors-creating.md)
* [Erstellen und Senden von Nachrichten](~/webhooks-and-connectors/how-to/connectors-using.md)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erstellen eines ausgehenden Webhooks](~/webhooks-and-connectors/how-to/add-outgoing-webhook.md)
