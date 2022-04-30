---
title: 'Testen der App: Übersicht'
description: Beschreibt den Prozess zum Testen und Debuggen Ihrer benutzerdefinierten Microsoft Teams-App in Microsoft 365.
ms.topic: how-to
ms.localizationpriority: high
keywords: Konfigurieren des Microsoft 365-Mandanten, Microsoft Teams, Hochladen der Test-App
ms.openlocfilehash: 98c00ece54e1654570556bac122e6760b283b73f
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111528"
---
# <a name="test-your-app"></a>Testen eigener Apps

Nachdem Sie Ihre App in Microsoft Teams integriert haben, müssen Sie ihre App testen, bevor Sie sie veröffentlichen. Das ultimative Ziel besteht darin, so viele Benutzer wie möglich für Ihre App zu erhalten. Stellen Sie daher sicher, dass Sie die App auf mehreren Geräten testen, die Benutzer verwenden können. Zum Testen Ihrer App:

* Bereiten Sie Ihren Microsoft 365-Mandanten vor.
* Wählen Sie einen Arbeitsbereich aus, um Ihre App zu testen und zu debuggen.
* Fügen Sie Testdaten zu Ihrem Microsoft 365 Mandanten hinzu.

## <a name="prepare-your-microsoft-365-tenant"></a>Vorbereiten Ihres Microsoft 365-Mandanten

Bevor Sie mit dem Testen Ihrer App beginnen, bereiten Sie Ihren Microsoft 365 Testmandanten vor, und aktivieren Sie die benutzerdefinierte Microsoft Teams-App, mit der Sie Ihre App hochladen können. Sie müssen sich für das Microsoft 365-Entwicklerprogramm registrieren und die Microsoft Teams-Einstellungen für Ihre Organisation verwalten. Richten Sie Ihr Entwicklerabonnement ein, und konfigurieren Sie es über [Vorbereiten Ihres Microsoft 365-Mandanten](~/concepts/build-and-test/prepare-your-o365-tenant.md).

## <a name="test-and-debug"></a>Testen und Debuggen

Um Ihre App zu testen und zu debuggen, müssen Sie mindestens einen Arbeitsbereich erstellen. Sie können ein Testsetup zum Testen und Debuggen der App auswählen, z. B. einen lokalen Host oder einen cloudbasierten Host. Eine Anleitung zum Debuggen Ihrer Microsoft Teams-App wird zum Ausführen der App-Umgebung bereitgestellt. Weitere Informationen finden Sie unter [Auswählen eines Setups und Ausführen Ihrer Microsoft Teams-App](~/concepts/build-and-test/debug.md).

Testen Sie Ihren Bot lokal. Weitere Informationen finden Sie unter [Lokales Debuggen Ihres Bots mit einer IDE](~/bots/how-to/debug/locally-with-an-ide.md). Sie können Ihren Bot auch mit [Inspektions-Middleware](/azure/bot-service/bot-service-debug-inspection-middleware?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true) und [adaptiven Tools](/azure/bot-service/bot-service-debug-adaptive-tools?view=azure-bot-service-4.0&preserve-view=true) debuggen.

Um die Konsolenprotokolle anzuzeigen, HTML-, CSS- und Netzwerkanforderungen während der Laufzeit anzuzeigen oder zu ändern, fügen Sie Ihrem JavaScript-Code Haltepunkte hinzu, und führen Sie den interaktiven Debugzugriff auf die DevTools aus. Weitere Informationen finden Sie unter [Zugriff auf die DevTools für Microsoft Teams-Registerkarten](~/tabs/how-to/developer-tools.md).

## <a name="add-test-data-to-your-microsoft-365-tenant"></a>Hinzufügen von Testdaten zu Ihrem Microsoft 365-Mandanten

Fügen Sie die Testdaten zum Microsoft 365-Testmandanten hinzu. Weitere Informationen finden Sie unter [Hinzufügen von Testdaten zu Ihrem Office 365-Testmandanten](~/concepts/build-and-test/test-data.md). Alle Voraussetzungen müssen erfüllt sein, bevor Sie mit dem Hochladen Ihrer Testdaten beginnen.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Vorbereiten Ihres Microsoft 365-Mandanten](~/concepts/build-and-test/prepare-your-o365-tenant.md)

## <a name="see-also"></a>Siehe auch

* [Debuggen Ihrer Registerkarten](~/tabs/how-to/developer-tools.md)
* [Debuggen Ihrer Bots](~/bots/how-to/debug/locally-with-an-ide.md)
* [Testen von RSC-Berechtigungen](~/graph-api/rsc/test-resource-specific-consent.md)
