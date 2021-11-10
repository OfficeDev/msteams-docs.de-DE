---
title: Testen der App-Übersicht
description: Beschreibt den Prozess zum Testen und Debuggen Ihrer Teams benutzerdefinierten App in Microsoft 365
ms.topic: how-to
ms.localizationpriority: medium
keywords: Konfigurieren Microsoft 365 Mandanten Teams Hochladen der Test-App
ms.openlocfilehash: 9cbb650fc248d12fc310cc8b1aaaded7b9a87140
ms.sourcegitcommit: af1d0a4041ce215e7863ac12c71b6f1fa3e3ba81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2021
ms.locfileid: "60889265"
---
# <a name="test-your-app"></a>Testen eigener Apps

Nach der Integration Ihrer App in Microsoft Teams müssen Sie ihre App vor der Veröffentlichung testen. Das ultimative Ziel besteht darin, so viele Benutzer für Ihre App zu erhalten. Stellen Sie daher sicher, dass Sie die App auf mehreren Geräten testen, die Benutzer verwenden können. Zum Testen Ihrer App:

* Bereiten Sie Ihren Microsoft 365 Mandanten vor.
* Wählen Sie einen Arbeitsbereich aus, um Ihre App zu testen und zu debuggen.
* Fügen Sie Ihrem Microsoft 365 Mandanten Testdaten hinzu.

## <a name="prepare-your-microsoft-365-tenant"></a>Vorbereiten Ihres Microsoft 365-Mandanten

Bevor Sie mit dem Testen Ihrer App beginnen, bereiten Sie Ihren Microsoft 365 Testmandanten vor, und aktivieren Sie benutzerdefinierte Teams App, mit der Sie Ihre App hochladen können. Sie müssen sich für Microsoft 365 Entwicklerprogramm registrieren und die Teams Einstellungen für Ihre Organisation verwalten. Richten Sie Ihr Entwicklerabonnement ein, und konfigurieren Sie es durch [Vorbereiten Ihres Microsoft 365 Mandanten.](~/concepts/build-and-test/prepare-your-o365-tenant.md)

## <a name="test-and-debug"></a>Testen und Debuggen

Um Ihre App zu testen und zu debuggen, müssen Sie mindestens einen Arbeitsbereich erstellen. Sie können ein Testsetup auswählen, z. B. einen lokalen Host oder einen cloudbasierten Host, um die App zu testen und zu debuggen. Anleitungen zum Debuggen Ihrer Teams App werden bereitgestellt, um Ihre App-Erfahrung zu laden und auszuführen. Weitere Informationen finden Sie unter ["Einrichten und Ausführen Ihrer Microsoft Teams-App".](~/concepts/build-and-test/debug.md)

Testen Sie Ihren Bot lokal. Weitere Informationen finden Sie unter [Debuggen Ihres Bots lokal mit einer IDE.](~/bots/how-to/debug/locally-with-an-ide.md) Sie können Ihren Bot auch mit [Middleware](/azure/bot-service/bot-service-debug-inspection-middleware?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true) für die Überprüfung und [adaptiven Tools](/azure/bot-service/bot-service-debug-adaptive-tools?view=azure-bot-service-4.0&preserve-view=true)debuggen. 

Wenn Sie die Konsolenprotokolle anzeigen, HTML-, CSS- und Netzwerkanforderungen während der Laufzeit anzeigen, anzeigen oder ändern möchten, fügen Sie Ihrem JavaScript-Code Haltepunkte hinzu, und führen Sie den interaktiven Debugzugriff auf devTools aus. Weitere Informationen finden Sie unter [Access the DevTools for Teams tabs](~/tabs/how-to/developer-tools.md). 

## <a name="add-test-data-to-your-microsoft-365-tenant"></a>Hinzufügen von Testdaten zu Ihrem Microsoft 365 Mandanten

Fügen Sie die Testdaten Microsoft 365 Testmandanten hinzu. Weitere Informationen finden Sie unter [Hinzufügen von Testdaten zu Ihrem Office 365 Testmandanten](~/concepts/build-and-test/test-data.md)und Erfüllen aller Voraussetzungen, bevor Sie mit dem Hochladen ihrer Testdaten beginnen.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Vorbereiten Ihres Microsoft 365-Mandanten](~/concepts/build-and-test/prepare-your-o365-tenant.md)

## <a name="see-also"></a>Siehe auch

* [Debuggen der Registerkarte](~/tabs/how-to/developer-tools.md)
* [Debuggen Von Bots](~/bots/how-to/debug/locally-with-an-ide.md)
* [Testen von RSC-Berechtigungen](~/graph-api/rsc/test-resource-specific-consent.md)
