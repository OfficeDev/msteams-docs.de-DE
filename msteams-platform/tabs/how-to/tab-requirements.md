---
title: Grundlegendes zu Registerkartenanforderungen
author: laujan
description: Jede Registerkarte in Microsoft Teams muss diesen Anforderungen entsprechen.
keywords: Gruppenkanal für Registerkarten von Teams konfigurierbar
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 1f5a3eaa8ca16878944288d5dbbfa78cfe9fa3ce
ms.sourcegitcommit: 4539479289b43812eaae07a1c0f878bed815d2d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/12/2021
ms.locfileid: "49797924"
---
# <a name="tab-requirements"></a>Registerkartenanforderungen

Die Registerkarten von Teams müssen die folgenden Anforderungen erfüllen:

* Sie müssen zulassen, dass Ihre Registerkartenseiten in einem iFrame, über X-Frame-Optionen und/oder Content-Security-Policy-HTTP-Antwortheader bedient werden.
  * Festlegen der Kopfzeile: `Content-Security-Policy: frame-ancestors teams.microsoft.com *.teams.microsoft.com *.skype.com`
  * Für Internet Explorer 11-Kompatibilität, ebenfalls `X-Content-Security-Policy` festgelegt.
  * Alternativ können Sie header `X-Frame-Options: ALLOW-FROM https://teams.microsoft.com/` festlegen. Diese Kopfzeile ist veraltet, wird aber von den meisten Browsern weiterhin berücksichtigt.
* In der Regel werden Anmeldeseiten nicht in iFrames gerendert, um sich vor Klicks zu schützen. Daher muss Ihre Authentifizierungslogik eine andere Methode als die Umleitung verwenden (z. B. tokenbasierte oder cookiebasierte Authentifizierung).

> [!NOTE]
> Chrome 80, das Anfang 2020 veröffentlicht werden soll, führt neue Cookiewerte ein und legt standardmäßig Cookierichtlinien fest. Es wird empfohlen, die beabsichtigte Verwendung für Ihre Cookies zu verwenden, anstatt sich auf das Standardverhalten des Browsers zu verlassen. *Siehe* [SameSite cookie attribute (2020 update)](../../resources/samesite-cookie-update.md).

* Browser halten sich an eine Richtlinieneinschränkung des gleichen Ursprungs, die verhindert, dass eine Webseite Anforderungen an eine andere Domäne als die Domäne zurückfordert, die eine Webseite bedient hat. Möglicherweise müssen Sie jedoch die Konfigurations- oder Inhaltsseite an eine andere Domäne oder Unterdomäne umleiten. Ihre domänenübergreifende Navigationslogik sollte es dem Teams-Client ermöglichen, den Ursprung anhand einer statischen validDomains-Liste im App-Manifest beim Laden oder Kommunizieren mit der Registerkarte zu überprüfen.

* Um eine nahtlose Erfahrung zu ermöglichen, sollten Sie Ihre Registerkarten basierend auf dem Design, dem Design und der Absicht des Teams-Clients gestalten. Registerkarten funktionieren in der Regel am besten, wenn sie so erstellt werden, dass sie bestimmte Anforderungen erfüllen und sich auf eine kleine Gruppe von Aufgaben oder eine Teilmenge von Daten konzentrieren, die für den Kanalspeicherort der Registerkarte relevant sind.

* Fügen Sie auf Ihrer Inhaltsseite mithilfe von Skripttags einen Verweis auf [das Microsoft Teams-JavaScript-Client-SDK](/javascript/api/overview/msteams-client) hinzu. Nehmen Sie nach dem Laden der Seite einen Aufruf an `microsoftTeams.initialize()` . Ihre Seite wird nicht angezeigt, wenn Sie dies nicht tun.
