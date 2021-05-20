---
title: Grundlegendes zu den Tabstoppanforderungen
author: laujan
description: Jede Registerkarte in Microsoft Teams muss diese Anforderungen erfüllen.
keywords: Teams Tabs Gruppenkanal konfigurierbar
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: a46a80401b29b5436807c9a5b94580beca3786f0
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566663"
---
# <a name="tab-requirements"></a>Registerkartenanforderungen

Teams Registerkarten müssen die folgenden Anforderungen erfüllen:

* Sie müssen zulassen, dass Ihre Registerkarten in einem iFrame über X-Frame-Optionen und/oder Content-Security-Policy-HTTP-Antwortheader bereitgestellt werden.
  * Set-Header: `Content-Security-Policy: frame-ancestors teams.microsoft.com *.teams.microsoft.com *.skype.com`
  * Für Internet Explorer 11-Kompatibilität, legen Sie `X-Content-Security-Policy` auch fest.
  * Alternativ können Sie den Header `X-Frame-Options: ALLOW-FROM https://teams.microsoft.com/` festlegen. Dieser Header ist veraltet, wird aber von den meisten Browsern immer noch respektiert.
* In der Regel werden Anmeldeseiten als Schutz vor Click-Jacking nicht in iFrames gerendert. Daher muss Ihre Authentifizierungslogik eine andere Methode als die Umleitung verwenden. Verwenden Sie beispielsweise die tokenbasierte oder cookiebasierte Authentifizierung.

> [!NOTE]
> Chrome 80, das Anfang 2020 veröffentlicht werden soll, führt neue Cookie-Werte ein und schreibt standardmäßig Cookie-Richtlinien vor. Es wird empfohlen, die beabsichtigte Verwendung für Ihre Cookies festzulegen, anstatt sich auf das Standardmäßige Browserverhalten zu verlassen. Weitere Informationen finden Sie unter [SameSite-Cookieattribut (2020-Update)](../../resources/samesite-cookie-update.md).

* Browser halten sich an eine Richtlinieseinschränkung gleichen Ursprungs, die verhindert, dass eine Webseite Anforderungen an eine andere Domäne als die, die eine Webseite bedient hat, stellt. Möglicherweise müssen Sie jedoch die Konfigurations- oder Inhaltsseite an eine andere Domäne oder Subdomäne umleiten. Ihre domänenübergreifende Navigationslogik sollte es dem Teams Client ermöglichen, den Ursprung anhand einer statischen validDomains-Liste im App-Manifest zu überprüfen, wenn er die Registerkarte lädt oder mit ihr kommuniziert.

* Um eine nahtlose Erfahrung zu schaffen, sollten Sie Ihre Registerkarten basierend auf dem Design, dem Design und der Absicht des Teams Clients formatieren. In der Regel funktionieren Registerkarten am besten, wenn sie so erstellt werden, dass sie auf einen bestimmten Bedarf zugeschnitten sind und sich auf einen kleinen Satz von Aufgaben oder eine Teilmenge von Daten konzentrieren, die für den Kanalspeicherort der Registerkarte relevant sind.

* Fügen Sie auf ihrer Inhaltsseite mithilfe von Skripttags einen Verweis auf [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client) hinzu. Rufen Sie nach dem Laden der Seite `microsoftTeams.initialize()` an . Ihre Seite wird nicht angezeigt, wenn Sie dies nicht tun.

* Damit die Authentifizierung auf mobilen Clients funktioniert, müssen Sie Teams JavaScript SDK auf mindestens Version 1.4.1 aktualisieren.

* Wenn Sie festlegen, dass Ihr Kanal oder die Registerkarte Gruppe auf Teams mobilen Clients angezeigt wird, muss die `setSettings()` Konfiguration einen Wert für die Eigenschaft `websiteUrl` haben.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erstellen Sie eine benutzerdefinierte persönliche Registerkarte mit Node.js und dem Yeoman Generator für Microsoft Teams](~/tabs/quickstarts/create-personal-tab-node-yeoman.md)