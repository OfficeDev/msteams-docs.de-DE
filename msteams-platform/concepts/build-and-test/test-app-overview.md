---
title: Testen der App-Übersicht
description: Beschreibt den Prozess zum Testen Ihrer benutzerdefinierten Teams-App in Microsoft 365
ms.topic: how-to
keywords: Konfigurieren der Microsoft 365-Mandantenteams zum Hochladen der Test-App
ms.openlocfilehash: b199ca4be31b546364091b754cdb890c8c0dd7d0
ms.sourcegitcommit: 5b3ba227c2e5e6f7a2c629961993f168da6a504d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2021
ms.locfileid: "51634779"
---
# <a name="test-your-app"></a>Testen eigener Apps

Nachdem Sie Ihre App in Microsoft Teams integriert haben, müssen Sie Ihre App testen, bevor Sie sie veröffentlichen. Das letztendliche Ziel ist es, so viele Benutzer für Ihre App zu erhalten, dass Sie die App auf mehreren Geräten testen, die Benutzer verwenden können. Zum Testen Ihrer App:

* Vorbereiten des Microsoft 365-Mandanten
* Auswählen eines Arbeitsbereichs zum Testen und Debuggen Ihrer App
* Hinzufügen von Testdaten zu Ihrem Microsoft 365-Mandanten

## <a name="prepare-your-microsoft-365-tenant"></a>Vorbereiten des Microsoft 365-Mandanten

Bevor Sie mit dem Testen Ihrer App beginnen, bereiten Sie Ihren Microsoft 365-Test-Mandanten vor, und aktivieren Sie die benutzerdefinierte Teams-App, mit der Sie Ihre App hochladen können. Sie müssen sich für das Microsoft 365-Entwicklerprogramm registrieren und die Teams-Einstellungen für Ihre Organisation verwalten. Richten Sie Ihr Entwicklerabonnement ein, und konfigurieren Sie es, wenn [Sie Ihren Microsoft 365-Mandanten vorbereiten.](~/concepts/build-and-test/prepare-your-o365-tenant.md)

## <a name="test-and-debug"></a>Testen und Debuggen

Zum Testen und Debuggen Ihrer App müssen Sie mindestens einen Arbeitsbereich erstellen. Sie können eine Testeinrichtung auswählen, z. B. einen lokalen Host oder einen cloudbasierten Host, um die App zu testen und zu debuggen. Anleitungen zum Debuggen Ihrer Teams-App finden Sie zum Laden und Ausführen Ihrer App-Erfahrung. Weitere Informationen finden Sie [unter Auswählen einer Einrichtung und Ausführen Ihrer Microsoft Teams-App.](~/concepts/build-and-test/debug.md)

Testen Sie Ihren Bot lokal. Weitere Informationen finden Sie unter [Debuggen Des Bots lokal mit einer IDE](~/bots/how-to/debug/locally-with-an-ide.md). Sie können Ihren Bot auch mit [Prüf-Middleware und](/azure/bot-service/bot-service-debug-inspection-middleware?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true) [adaptiven Tools debuggen.](/azure/bot-service/bot-service-debug-adaptive-tools?view=azure-bot-service-4.0&preserve-view=true) 

Wenn Sie die Konsolenprotokolle anzeigen, html-, css- und Netzwerkanforderungen während der Laufzeit anzeigen oder ändern möchten, fügen Sie Ihrem JavaScript-Code Haltepunkte hinzu, und führen Sie interaktiven Debugzugriff auf devTools aus. Weitere Informationen finden Sie unter [Access the DevTools for Teams tabs](~/tabs/how-to/developer-tools.md). 

## <a name="add-test-data-to-your-microsoft-365-tenant"></a>Hinzufügen von Testdaten zu Ihrem Microsoft 365-Mandanten

Fügen Sie die Testdaten dem Microsoft 365-Test-Mandanten hinzu. Weitere Informationen finden Sie unter Hinzufügen von Testdaten zu [Ihrem Office 365-Test-Mandanten,](~/concepts/build-and-test/test-data.md)und füllen Sie alle erforderlichen Komponenten aus, bevor Sie mit dem Hochladen ihrer Testdaten beginnen.

## <a name="see-also"></a>Siehe auch

> [!div class="nextstepaction"]
> [Debuggen Ihrer Registerkarte](~/tabs/how-to/developer-tools.md)
 
> [!div class="nextstepaction"]
> [Debuggen Ihrer Bots](~/bots/how-to/debug/locally-with-an-ide.md)

> [!div class="nextstepaction"]
> [Testen von RSC-Berechtigungen](~/graph-api/rsc/test-resource-specific-consent.md)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Vorbereiten des Microsoft 365-Mandanten](~/concepts/build-and-test/prepare-your-o365-tenant.md)
