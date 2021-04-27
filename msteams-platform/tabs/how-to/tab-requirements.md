---
title: Grundlegendes zu Registerkartenanforderungen
author: laujan
description: Jede Registerkarte in Microsoft Teams muss diese Anforderungen erfüllen.
keywords: Gruppenkanal für Teams-Registerkarten konfigurierbar
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 8013c10050ae81ada0f2a27576cd43077eafe1e0
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019580"
---
# <a name="tab-requirements"></a>Registerkartenanforderungen

Teams-Registerkarten müssen die folgenden Anforderungen erfüllen:

* Sie müssen zulassen, dass Ihre Registerkartenseiten in einem iFrame über X-Frame-Optionen und/oder Content-Security-Policy-HTTP-Antwortheader bedient werden.
  * Kopfzeile festlegen: `Content-Security-Policy: frame-ancestors teams.microsoft.com *.teams.microsoft.com *.skype.com`
  * Für Internet Explorer 11-Kompatibilität ebenfalls `X-Content-Security-Policy` festgelegt.
  * Alternativ können Sie header `X-Frame-Options: ALLOW-FROM https://teams.microsoft.com/` festlegen. Diese Kopfzeile ist veraltet, wird jedoch von den meisten Browsern weiterhin berücksichtigt.
* In der Regel werden Anmeldeseiten als Schutz vor Klicks nicht in iFrames gerendert. Daher muss Ihre Authentifizierungslogik eine andere Methode als die Umleitung verwenden (z. B. tokenbasierte oder cookiebasierte Authentifizierung).

> [!NOTE]
> Chrome 80, das anfang 2020 veröffentlicht werden soll, führt neue Cookiewerte ein und setzt standardmäßig Cookierichtlinien auf. Es wird empfohlen, dass Sie die beabsichtigte Verwendung für Ihre Cookies festlegen, anstatt sich auf das Standardverhalten des Browsers zu verlassen. *Weitere Informationen* [finden Sie unter SameSite cookie attribute (2020 update)](../../resources/samesite-cookie-update.md).

* Browser halten sich an eine Richtlinieneinschränkung mit demselben Ursprung, die verhindert, dass eine Webseite Anforderungen an eine andere Domäne als die einer Webseite anfordert. Möglicherweise müssen Sie die Konfigurations- oder Inhaltsseite jedoch zu einer anderen Domäne oder Unterdomäne umleiten. Ihre domänenübergreifende Navigationslogik sollte es dem Teams-Client ermöglichen, den Ursprung anhand einer statischen validDomains-Liste im App-Manifest zu überprüfen, wenn die Registerkarte geladen oder mit ihr kommuniziert wird.

* Um eine nahtlose Benutzererfahrung zu ermöglichen, sollten Sie Ihre Registerkarten basierend auf design, design und intent des Teams-Clients formatiert haben. In der Regel funktionieren Registerkarten am besten, wenn sie für eine bestimmte Notwendigkeit erstellt wurden und sich auf eine kleine Gruppe von Aufgaben oder eine Teilmenge von Daten konzentrieren, die für den Kanalspeicherort der Registerkarte relevant sind.

* Fügen Sie auf Ihrer Inhaltsseite mithilfe von Skripttags einen Verweis auf [das Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client) hinzu. Rufen Sie nach dem Laden der Seite auf `microsoftTeams.initialize()` . Ihre Seite wird nicht angezeigt, wenn Sie dies nicht tun.

* Damit die Authentifizierung auf mobilen Clients funktioniert, müssen Sie das Teams JavaScript SDK auf mindestens Version 1.4.1 aktualisieren.

* Wenn Sie den Kanal oder die Registerkarte "Gruppe" auf mobilen Teams-Clients anzeigen möchten, muss die Konfiguration `setSettings()` einen Wert für die Eigenschaft `websiteUrl` haben.