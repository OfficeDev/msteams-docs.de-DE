---
title: Webhooks und Connectors
author: clearab
description: In diesem Modul erfahren Sie, wie Webhooks und Connectors Ihre Webdienste mit dem Teams-Client verbinden können.
ms.localizationpriority: high
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: fc65046c0bcbecb6ed4c0f15ea81beac77195256
ms.sourcegitcommit: 7bbb7caf729a00b267ceb8af7defffc91903d945
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/21/2022
ms.locfileid: "66190035"
---
# <a name="webhooks-and-connectors"></a>Webhooks und Connectors

Webhooks und Connectors helfen beim Verbinden der Webdienste mit Kanälen und Teams in Microsoft Teams. Webhooks sind benutzerdefinierte HTTP-Rückrufe, mit denen Benutzer über alle Aktionen benachrichtigt werden, die im Teams-Kanal ausgeführt wurden. Es ist eine Möglichkeit für eine App, Echtzeitdaten abzurufen. Connectors ermöglichen Benutzern, Benachrichtigungen und Nachrichten von Ihren Webdiensten zu abonnieren. Sie stellen einen HTTPS-Endpunkt für Ihren Dienst bereit, um Nachrichten in Form von Karten zu posten.

## <a name="outgoing-webhooks"></a>Ausgehende Webhooks

Webhooks hilft Teams bei der Integration in externe Apps. Mit ausgehenden Webhooks können Sie Textnachrichten von einem Kanal an die Webdienste senden. Nach dem Konfigurieren der ausgehenden Webhooks können Benutzer Outgoing Webhook via @mention erwähnen und eine Nachricht an Webdienste senden. Der Dienst antwortet innerhalb von zehn Sekunden mit einem Text oder einer Karte auf die Nachricht.

> [!NOTE]
> Ausgehende Webhooks werden pro Team konfiguriert und können nicht als Teil einer normalen Teams-App eingeschlossen werden.

## <a name="connectors"></a>Connectors

Connectors ermöglichen Benutzern das Abonnieren von Benachrichtigungen und Nachrichten von den Webdiensten. Sie machen den HTTPS-Endpunkt für den Dienst verfügbar, um Nachrichten in Teams Kanälen zu posten, in der Regel in Form von Karten.

### <a name="incoming-webhooks"></a>Eingehende Webhooks

Eingehende Webhooks helfen beim Veröffentlichen von Nachrichten aus Apps in Teams. Wenn eingehende Webhooks für ein Team in einem beliebigen Kanal aktiviert sind, wird der HTTPS-Endpunkt verfügbar gemacht, der korrekt formatierte JSON akzeptiert und die Nachrichten in diesen Kanal einfügt. Sie können z. B. einen eingehenden Webhook in Ihrem DevOps-Kanal erstellen, Ihren Build konfigurieren und gleichzeitig Dienste bereitstellen und überwachen, um Warnungen zu senden.

### <a name="office-365-connectors"></a>Office 365-Connectors

Mit Office 365 Connectors können Sie eine benutzerdefinierte Konfigurationsseite für Ihren eingehenden Webhook erstellen und diese als Teil einer Teams-App zusammenfassen. Sie senden Nachrichten in erster Linie mit Office 365 Connectorkarten und haben die Möglichkeit, ihnen einen begrenzten Satz von Kartenaktionen hinzuzufügen. Beispielsweise ein Wetterconnector, mit dem Benutzer einen Ort und eine Uhrzeit auswählen können, um Updates über das Wetter von morgen zu erhalten. Sie werden auf Kanalebene konfiguriert, aber auf einer Teamebene installiert.

> [!NOTE]
> Sie können die Office 365-Connector Teams-App an unseren AppStore leiten.

## <a name="create-and-send-messages"></a>Nachrichten erstellen und senden

Nachrichten mit Aktionen ermöglichen es Benutzern, Maßnahmen zu ergreifen, ohne ihren E-Mail-Client zu verlassen, was die Benutzereinbindung erhöht. Mit Office 365 und eingehenden Webhooks können Sie Nachrichten senden, indem Sie eine JSON-Nutzlast an die Webhook-URL senden.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erstellen eines ausgehenden Webhooks](~/webhooks-and-connectors/how-to/add-outgoing-webhook.md)

## <a name="see-also"></a>Siehe auch

* [Erstellen eines eingehenden Webhooks](~/webhooks-and-connectors/how-to/add-incoming-webhook.md)
* [Erstellen eines Office 365-Connectors](~/webhooks-and-connectors/how-to/connectors-creating.md)
* [Nachrichten erstellen und senden](~/webhooks-and-connectors/how-to/connectors-using.md)
