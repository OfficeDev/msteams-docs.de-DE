---
title: Testen Der App-Übersicht
description: Beschreibt den Prozess zum Testen der Teams benutzerdefinierten App in Microsoft 365
ms.topic: how-to
localization_priority: Normal
keywords: Konfigurieren Microsoft 365 Mandanten Teams Hochladen der Test-App
ms.openlocfilehash: 2c9f23a5c6ae286ff4b7d911f370bd45b854a647
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52565186"
---
# <a name="test-your-app"></a>Testen eigener Apps

Nachdem Sie Ihre App in Microsoft Teams integriert haben, müssen Sie ihre App testen, bevor Sie sie veröffentlichen. Das ultimative Ziel besteht darin, so viele Benutzer für Ihre App zu erhalten, daher stellen Sie sicher, dass die App auf mehreren Geräten getestet wird, die Benutzer verwenden könnten. Zum Testen Ihrer App:

* Bereiten Sie Ihren Microsoft 365 Mandanten vor.
* Wählen Sie einen Arbeitsbereich aus, um Ihre App zu testen und zu debuggen.
* Fügen Sie Ihrem Microsoft 365 Mandanten Testdaten hinzu.

## <a name="prepare-your-microsoft-365-tenant"></a>Vorbereiten Ihres Microsoft 365-Mandanten

Bevor Sie mit dem Testen Ihrer App beginnen, bereiten Sie Ihren Microsoft 365 Testmandanten vor und aktivieren Sie benutzerdefinierte Teams App, mit der Sie Ihre App hochladen können. Sie müssen sich für Microsoft 365 Entwicklerprogramm anmelden und die Teams Einstellungen für Ihre Organisation verwalten. Richten Sie Ihr Entwicklerabonnement ein, und konfigurieren Sie es, indem [Sie Ihre Microsoft 365 Mandanten vorbereiten.](~/concepts/build-and-test/prepare-your-o365-tenant.md)

## <a name="test-and-debug"></a>Testen und Debuggen

Zum Testen und Debuggen Ihrer App müssen Sie mindestens einen Arbeitsbereich erstellen. Sie können ein Test-Setup auswählen, z. B. einen lokalen oder cloudbasierten Host, um die App zu testen und zu debuggen. Anleitungzum Debuggen Ihrer Teams-App wird zum Laden und Ausführen ihrer App-Erfahrung bereitgestellt. Weitere Informationen finden [Sie unter Auswählen eines Setups und Ausführen ihrer Microsoft Teams-App](~/concepts/build-and-test/debug.md).

Testen Sie Ihren Bot lokal. Weitere Informationen finden Sie unter [Debuggen des Bots lokal mit einer IDE](~/bots/how-to/debug/locally-with-an-ide.md). Sie können Ihren Bot auch mit [Inspektionsmiddleware](/azure/bot-service/bot-service-debug-inspection-middleware?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true) und [adaptiven Tools](/azure/bot-service/bot-service-debug-adaptive-tools?view=azure-bot-service-4.0&preserve-view=true)debuggen. 

Um die Konsolenprotokolle anzuzeigen, HTML-, css- und Netzwerkanforderungen während der Laufzeit anzuzeigen oder zu ändern, fügen Sie Ihrem JavaScript-Code Haltepunkte hinzu, und führen Sie interaktiven Debugzugriff auf die DevTools durch. Weitere Informationen finden [Sie unter Zugriff auf die DevTools für Teams Registerkarten](~/tabs/how-to/developer-tools.md). 

## <a name="add-test-data-to-your-microsoft-365-tenant"></a>Hinzufügen von Testdaten zu Ihrem Microsoft 365 Mandanten

Fügen Sie die Testdaten Microsoft 365 Testmandanten hinzu. Weitere Informationen finden Sie unter [Hinzufügen von Testdaten zu Ihrem Office 365 Testmandanten](~/concepts/build-and-test/test-data.md), und schließen Sie alle Voraussetzungen ab, bevor Sie mit dem Hochladen der Testdaten beginnen.

## <a name="see-also"></a>Siehe auch

- [Debuggen Sie Ihre Registerkarte](~/tabs/how-to/developer-tools.md)
 
- [Debuggen Sie Ihre Bots](~/bots/how-to/debug/locally-with-an-ide.md)

- [RSC-Berechtigungen testen](~/graph-api/rsc/test-resource-specific-consent.md)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Vorbereiten Ihres Microsoft 365-Mandanten](~/concepts/build-and-test/prepare-your-o365-tenant.md)
