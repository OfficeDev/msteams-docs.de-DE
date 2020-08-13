---
title: Was sind webhooks und Connectors?
author: clearab
description: Erfahren Sie, wie webhooks und Connectors ihre Webdienste mit dem Microsoft Teams-Client verbinden können.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 740806e43af94d5a5da876affec2070a5a461b11
ms.sourcegitcommit: 9fbc701a9a039ecdc360aefbe86df52b9c3593f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/12/2020
ms.locfileid: "46651998"
---
# <a name="what-are-webhooks-and-connectors"></a>Was sind webhooks und Connectors?

Webhooks und Connectors sind einfache Möglichkeiten zum Verbinden externer Systeme und Dienste mit Microsoft Teams-Kanälen und-Chats.

Benutzer können beispielsweise Benachrichtigungen von einer anderen APP abonnieren (normalerweise in Form von Karten).

## <a name="incoming-webhooks"></a>Eingehende webhooks

Eingehende webhooks sind die einfachste Art von Connector und eine schnelle und einfache Möglichkeit, den Kanal eines Teams mit einem externen Dienst zu verbinden. Für jeden Kanal (falls für dieses Team aktiviert) können Sie einen HTTPS-Endpunkt verfügbar machen, der ordnungsgemäß formatierte JSON akzeptiert und Nachrichten in den Kanal einfügt.

Siehe [Erstellen eines eingehenden webhooks](~/webhooks-and-connectors/how-to/add-incoming-webhook.md).

### <a name="user-scenarios"></a>Benutzerszenarien

Eingehende webhooks eignen sich am besten für Szenarien, die für ein bestimmtes Team eindeutig sind. Sie können beispielsweise einen eingehenden webhook in Ihrem DevOps-Kanal erstellen und ihre Build-, Bereitstellungs-und Überwachungsdienste so konfigurieren, dass Warnungen gesendet werden.

## <a name="office-365-connectors"></a>Office 365-Connectors

Mit einem Office 365-Konnektor können Sie eine benutzerdefinierte Konfigurationsseite für den eingehenden webhook erstellen und als Teil einer Teams-App verpacken. Sie können diese APP dann breiter oder sogar in unserem App Store verteilen. Sie senden Nachrichten in erster Linie mit Office 365-connectorkarten, die auch eine beschränkte Reihe von Karten Aktionen haben können. Sie werden auf Kanalebene konfiguriert, aber auf Teamebene installiert.

Weitere Informationen finden Sie unter [Erstellen eines Office 365-Konnektors](~/webhooks-and-connectors/how-to/connectors-creating.md).

### <a name="user-scenarios"></a>Benutzerszenarien

Ein Wetter-Konnektor, mit dem Sie einen Standort und eine Tageszeit für den Empfang von Updates für die Prognose von morgen auswählen können.

## <a name="outgoing-webhooks"></a>Ausgehende Webhooks

Ausgehende Webhooks ermöglichen Benutzern das Senden von Textnachrichten aus einem Kanal an Ihre Webdienste. Nach der Konfiguration können Benutzer Ihre APP @mention und eine Nachricht an Ihren externen Dienst senden. Ihr Dienst hat fünf Sekunden Zeit, um eine Antwort auf die Nachricht zu senden, die möglicherweise Text oder eine Karte enthält.

Ausgehende webhooks werden pro Team konfiguriert und können nicht als Teil einer normalen Teams-App eingeschlossen werden.

Weitere Informationen finden Sie unter [Create an Outgoing webhook](~/webhooks-and-connectors/how-to/add-outgoing-webhook.md).

### <a name="user-scenarios"></a>Benutzerszenarien

Ausgehende webhooks eignen sich am besten für die Durchführung Team spezifischer Workflows, die nicht das Sammeln oder austauschen großer Informationsmengen erfordern.

## <a name="learn-more"></a>Weitere Informationen

* [Planen Ihrer APP](../../concepts/extensibility-points.md)
* [Erstellen Ihrer APP](../../concepts/building-an-app.md)
* [Veröffentlichen Ihrer APP](../../concepts/deploy-and-publish/overview.md)
