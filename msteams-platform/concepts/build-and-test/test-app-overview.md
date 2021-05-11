---
title: Testen der App-Übersicht
description: Beschreibt den Prozess zum Testen Teams benutzerdefinierten Apps in Microsoft 365
ms.topic: how-to
localization_priority: Normal
keywords: Konfigurieren Microsoft 365 Mandanten Teams Hochladen der Test-App
ms.openlocfilehash: d95d65961b060ff1938d51c0f3fafc2b1e56fa7e
ms.sourcegitcommit: a732789190f59ec1f3699e8ad2f06387e8fe1458
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2021
ms.locfileid: "52058607"
---
# <a name="test-your-app"></a>Testen eigener Apps

Nachdem Sie Ihre App in Microsoft Teams integriert haben, müssen Sie Ihre App testen, bevor Sie sie veröffentlichen. Das letztendliche Ziel ist es, so viele Benutzer für Ihre App zu erhalten, dass Sie die App auf mehreren Geräten testen, die Benutzer verwenden können. Zum Testen Ihrer App:

* Vorbereiten Ihres Microsoft 365-Mandanten
* Auswählen eines Arbeitsbereichs zum Testen und Debuggen Ihrer App
* Hinzufügen von Testdaten zu Ihrem Microsoft 365 Mandanten

## <a name="prepare-your-microsoft-365-tenant"></a>Vorbereiten Ihres Microsoft 365-Mandanten

Bevor Sie mit dem Testen Ihrer App beginnen, bereiten Sie Microsoft 365 Test-Mandant vor, und aktivieren Sie benutzerdefinierte Teams App, mit der Sie Ihre App hochladen können. Sie müssen sich für Microsoft 365-Entwicklerprogramm registrieren und die Teams für Ihre Organisation verwalten. Richten Sie Ihr Entwicklerabonnement ein, und konfigurieren Sie es, wenn [Sie Ihren Microsoft 365 vorbereiten.](~/concepts/build-and-test/prepare-your-o365-tenant.md)

## <a name="test-and-debug"></a>Testen und Debuggen

Zum Testen und Debuggen Ihrer App müssen Sie mindestens einen Arbeitsbereich erstellen. Sie können eine Testeinrichtung auswählen, z. B. einen lokalen Host oder einen cloudbasierten Host, um die App zu testen und zu debuggen. Anleitungen zum Debuggen Teams app wird bereitgestellt, um Ihre App-Erfahrung zu laden und ausführen. Weitere Informationen finden Sie unter Auswählen einer Einrichtung und Ausführen ihrer [Microsoft Teams App.](~/concepts/build-and-test/debug.md)

Testen Sie Ihren Bot lokal. Weitere Informationen finden Sie unter [Debuggen Des Bots lokal mit einer IDE](~/bots/how-to/debug/locally-with-an-ide.md). Sie können Ihren Bot auch mit [Prüf-Middleware und](/azure/bot-service/bot-service-debug-inspection-middleware?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true) [adaptiven Tools debuggen.](/azure/bot-service/bot-service-debug-adaptive-tools?view=azure-bot-service-4.0&preserve-view=true) 

Wenn Sie die Konsolenprotokolle anzeigen, html-, css- und Netzwerkanforderungen während der Laufzeit anzeigen oder ändern möchten, fügen Sie Ihrem JavaScript-Code Haltepunkte hinzu, und führen Sie interaktiven Debugzugriff auf devTools aus. Weitere Informationen finden Sie unter [Access the DevTools for Teams tabs](~/tabs/how-to/developer-tools.md). 

## <a name="add-test-data-to-your-microsoft-365-tenant"></a>Hinzufügen von Testdaten zu Ihrem Microsoft 365 Mandanten

Fügen Sie die Testdaten dem Microsoft 365 hinzu. Weitere Informationen finden Sie unter Hinzufügen von Testdaten zu Office 365 [Test-Mandant,](~/concepts/build-and-test/test-data.md)und füllen Sie alle erforderlichen Komponenten aus, bevor Sie mit dem Hochladen der Testdaten beginnen.

## <a name="see-also"></a>Siehe auch

- [Debuggen Ihrer Registerkarte](~/tabs/how-to/developer-tools.md)
 
- [Debuggen Ihrer Bots](~/bots/how-to/debug/locally-with-an-ide.md)

- [Testen von RSC-Berechtigungen](~/graph-api/rsc/test-resource-specific-consent.md)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Vorbereiten Ihres Microsoft 365-Mandanten](~/concepts/build-and-test/prepare-your-o365-tenant.md)
