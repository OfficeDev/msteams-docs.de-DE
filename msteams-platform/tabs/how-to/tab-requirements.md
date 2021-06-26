---
title: Voraussetzungen
author: surbhigupta
description: Jede Registerkarte in Microsoft Teams muss diese Anforderungen erfüllen.
keywords: Konfigurierbarer Gruppenkanal für Teams-Registerkarten
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: b54fc7235132a9253f6eecc62417f786bf4aa45c
ms.sourcegitcommit: 4d9d1542e04abacfb252511c665a7229d8bb7162
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2021
ms.locfileid: "53140187"
---
# <a name="prerequisites"></a>Voraussetzungen

Teams Registerkarten müssen die folgenden Voraussetzungen erfüllen:

* Sie müssen zulassen, dass Ihre Registerkartenseiten in einem iFrame angezeigt werden, indem Sie X-Frame-Optionen und HTTP-Antwortheader für Inhaltssicherheitsrichtlinien verwenden.
  * Header festlegen: `Content-Security-Policy: frame-ancestors teams.microsoft.com *.teams.microsoft.com *.skype.com`
  * Legen Sie aus Gründen der Internet Explorer 11-Kompatibilität `X-Content-Security-Policy` fest.
  * Legen Sie alternativ die Kopfzeile `X-Frame-Options: ALLOW-FROM https://teams.microsoft.com/` fest. Dieser Header ist veraltet, wird aber von den meisten Browsern weiterhin akzeptiert.

* Als Schutz vor Clickjacking werden Anmeldeseiten in der Regel nicht in iFrames gerendert. Ihre Authentifizierungslogik muss eine andere Methode als die Umleitung verwenden. Verwenden Sie beispielsweise die token- oder cookiebasierte Authentifizierung.

    > [!NOTE]
    > Chrome 80, das Anfang 2020 veröffentlicht werden soll, führt neue Cookiewerte ein und erlegt standardmäßig Cookierichtlinien auf. Es wird empfohlen, die beabsichtigte Verwendung für Ihre Cookies festzulegen, anstatt sich auf das Standardverhalten des Browsers zu verlassen. Weitere Informationen finden Sie unter [SameSite-Cookieattribut.](../../resources/samesite-cookie-update.md)

* Browser halten sich an eine Einschränkung der Richtlinie für den gleichen Ursprung. Es verhindert, dass Webseiten Anforderungen an andere Domänen als die bereitgestellte Webseite senden. Sie können die Konfigurations- oder Inhaltsseite jedoch an eine andere Domäne oder Unterdomäne umleiten. Ihre domänenübergreifende Navigationslogik muss es dem Teams-Client ermöglichen, den Ursprung anhand einer statischen `validDomains` Liste im App-Manifest beim Laden oder Kommunizieren mit der Registerkarte zu überprüfen.

* Sie müssen ihre Registerkarten basierend auf dem Design, dem Design und der Absicht des Teams Clients formatieren. Registerkarten funktionieren in der Regel am besten, wenn sie so erstellt werden, dass sie einem bestimmten Bedarf entsprechen und sich auf eine kleine Gruppe von Aufgaben oder eine Teilmenge von Daten konzentrieren, die für den Kanalspeicherort der Registerkarte relevant sind.

* Fügen Sie innerhalb Ihrer Inhaltsseite einen Verweis auf [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client) mithilfe von Skripttags hinzu. Nachdem die Seite geladen wurde, rufen Sie sie `microsoftTeams.initialize()` auf, andernfalls wird die Seite nicht angezeigt.

* Damit die Authentifizierung auf mobilen Clients funktioniert, müssen Sie Teams JavaScript SDK auf mindestens Version 1.4.1 aktualisieren.

* Wenn Sie ihre Kanal- oder Gruppenregisterkarte auf Teams mobilen Clients anzeigen möchten, muss die `setSettings()` Konfiguration einen Wert für die Eigenschaft `websiteUrl` aufweisen.

* Die Registerkarte "MS Teams" unterstützt nicht die Möglichkeit, Intranetwebsites zu laden, die selbstsignte Zertifikate verwenden.

## <a name="see-also"></a>Siehe auch

* [registerkarten Teams](~/tabs/what-are-tabs.md)
* [Erstellen einer Kanal- oder Gruppenregisterkarte](~/tabs/how-to/create-channel-group-tab.md)
* [Erstellen einer Inhaltsseite](~/tabs/how-to/create-tab-pages/content-page.md)
* [Erstellen einer Konfigurationsseite](~/tabs/how-to/create-tab-pages/configuration-page.md)
* [Erstellen einer Seite zum Entfernen ihrer Registerkarte](~/tabs/how-to/create-tab-pages/removal-page.md)
* [Registerkarten auf mobilen Geräten](~/tabs/design/tabs-mobile.md)
* [Kontext für Ihre Registerkarte erhalten](~/tabs/how-to/access-teams-context.md)
* [Erstellen von Registerkarten mit adaptiven Karten](~/tabs/how-to/build-adaptive-card-tabs.md)
* [Aufgeklappte Registerkartenverknüpfung und Phasenansicht](~/tabs/tabs-link-unfurling.md)
* [Registerkarten für Unterhaltungen erstellen](~/tabs/how-to/conversational-tabs.md)
* [Änderungen am Registerkartenrand](~/resources/removing-tab-margins.md)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erstellen einer persönlichen Registerkarte](~/tabs/how-to/create-personal-tab.md)
