---
title: Registerkartenanforderungen
author: surbhigupta
description: Jede Registerkarte in Microsoft Teams muss diese Anforderungen erfüllen.
keywords: Konfigurierbarer Gruppenkanal für Teams-Registerkarten
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: a5d4b1a1c9b79d45d323acab7bfba2ba7ac2958d
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "53069205"
---
# <a name="tab-requirements"></a>Registerkartenanforderungen

Teams Registerkarten müssen die folgenden Anforderungen erfüllen:

* Sie müssen zulassen, dass Ihre Registerkartenseiten in einem iFrame bereitgestellt werden, indem Sie die HTTP-Antwortheader "X-Frame-Options" und "Content-Security-Policy" verwenden.
  * Header festlegen: `Content-Security-Policy: frame-ancestors teams.microsoft.com *.teams.microsoft.com *.skype.com`
  * Legen Sie aus Gründen der Internet Explorer 11-Kompatibilität `X-Content-Security-Policy` fest.
  * Legen Sie alternativ die Kopfzeile `X-Frame-Options: ALLOW-FROM https://teams.microsoft.com/` fest. Dieser Header ist veraltet, wird aber von den meisten Browsern weiterhin akzeptiert.
* Als Schutz vor Klickbuchsen werden Anmeldeseiten in der Regel nicht in iFrames gerendert. Ihre Authentifizierungslogik muss eine andere Methode als die Umleitung verwenden. Verwenden Sie beispielsweise die token- oder cookiebasierte Authentifizierung.

    > [!NOTE]
    > Chrome 80, das Anfang 2020 veröffentlicht werden soll, führt neue Cookiewerte ein und erlegt standardmäßig Cookierichtlinien auf. Es wird empfohlen, die beabsichtigte Verwendung für Ihre Cookies festzulegen, anstatt sich auf das Standardverhalten des Browsers zu verlassen. Weitere Informationen finden Sie unter [Update des SameSite-Cookieattributs 2020.](../../resources/samesite-cookie-update.md)

* Browser halten sich an eine Einschränkung der Richtlinie für den gleichen Ursprung, die verhindert, dass eine Webseite Anforderungen an eine andere Domäne als die Domäne stellt, die eine Webseite bedient hat. Sie können die Konfigurations- oder Inhaltsseite jedoch an eine andere Domäne oder Unterdomäne umleiten. Ihre domänenübergreifende Navigationslogik muss es dem Teams-Client ermöglichen, den Ursprung anhand einer statischen Liste gültiger Domänen im App-Manifest beim Laden oder Kommunizieren mit der Registerkarte zu überprüfen.

* Um eine nahtlose Oberfläche zu erstellen, müssen Sie Ihre Registerkarten basierend auf dem Design, dem Design und der Absicht des Teams Clients formatieren. Registerkarten funktionieren in der Regel am besten, wenn sie so erstellt werden, dass sie einem bestimmten Bedarf entsprechen und sich auf eine kleine Gruppe von Aufgaben oder eine Teilmenge von Daten konzentrieren, die für den Kanalspeicherort der Registerkarte relevant sind.

* Fügen Sie innerhalb Ihrer Inhaltsseite einen Verweis auf [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client) mithilfe von Skripttags hinzu. Nachdem die Seite geladen wurde, rufen Sie sie `microsoftTeams.initialize()` auf, andernfalls wird die Seite nicht angezeigt.

* Damit die Authentifizierung auf mobilen Clients funktioniert, müssen Sie Teams JavaScript SDK auf mindestens Version 1.4.1 aktualisieren.

* Wenn Sie ihre Kanal- oder Gruppenregisterkarte auf Teams mobilen Clients anzeigen möchten, muss die `setSettings()` Konfiguration einen Wert für die Eigenschaft `websiteUrl` aufweisen.

* Die Registerkarte "MS Teams" unterstützt nicht die Möglichkeit, Intranetwebsites zu laden, die selbstsignte Zertifikate verwenden.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erstellen einer benutzerdefinierten persönlichen Registerkarte mit Node.js und dem Yeoman-Generator für Microsoft Teams](~/tabs/quickstarts/create-personal-tab-node-yeoman.md)
