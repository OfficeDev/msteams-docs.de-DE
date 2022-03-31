---
title: Voraussetzungen
author: surbhigupta
description: Jede Registerkarte in Microsoft Teams muss diesen Anforderungen entsprechen.
keywords: Konfigurierbarer Gruppenkanal für Teams-Registerkarten
ms.localizationpriority: medium
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: fe72691465ca785cefb6a96c8eb4005a64601a17
ms.sourcegitcommit: 3dc9b539c6f7fbfb844c47a78e3b4d2200dabdad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/31/2022
ms.locfileid: "64571516"
---
# <a name="prerequisites"></a>Voraussetzungen

Stellen Sie sicher, dass Sie die folgenden Voraussetzungen erfüllen, während Sie Ihre Teams persönlichen Registerkarte und kanal- oder gruppenregisterkarte erstellen:

* Zulassen, dass Ihre Registerkartenseiten in einem iFrame mithilfe von X-Frame-Optionen und HTTP-Antwortheadern für Content-Security-Richtlinien ermittelt werden.
  * Header festlegen: `Content-Security-Policy: frame-ancestors teams.microsoft.com *.teams.microsoft.com *.skype.com`
  * Legen Sie aus Gründen der Internet Explorer 11-Kompatibilität fest `X-Content-Security-Policy`.
  * Legen Sie alternativ die Kopfzeile `X-Frame-Options: ALLOW-FROM https://teams.microsoft.com/`fest. Dieser Header ist veraltet, wird aber von den meisten Browsern weiterhin akzeptiert.

* Anmeldeseiten werden nicht in iFrames gerendert, als Schutz vor Clickjacking. Ihre Authentifizierungslogik muss eine andere Methode als die Umleitung verwenden. Verwenden Sie beispielsweise die token- oder cookiebasierte Authentifizierung.

    > [!NOTE]
    > Es wird empfohlen, die beabsichtigte Verwendung für Ihre Cookies festzulegen, anstatt sich auf das Standardverhalten des Browsers zu verlassen. Weitere Informationen finden Sie unter [SameSite-Cookieattribut](../../resources/samesite-cookie-update.md).

* Die Einschränkung der Browserrichtlinie für den gleichen Ursprung verhindert, dass Webseiten Anforderungen an andere Domänen als die bereitgestellte Webseite stellen. Sie können die Konfigurations- oder Inhaltsseite also an eine andere Domäne oder Unterdomäne umleiten. Ihre domänenübergreifende Navigationslogik muss es dem Teams-Client ermöglichen, den Ursprung anhand einer statischen `validDomains` Liste im App-Manifest beim Laden oder Kommunizieren mit der Registerkarte zu überprüfen.

* Formatieren Sie Ihre Registerkarten basierend auf dem Design, dem Design und der Absicht des Teams Clients. Registerkarten funktionieren am besten, wenn sie so erstellt werden, dass sie bestimmte Anforderungen erfüllen und sich auf eine kleine Gruppe von Aufgaben oder eine Teilmenge von Daten konzentrieren, die für den Kanalspeicherort der Registerkarte relevant sind.

* Fügen Sie innerhalb Ihrer Inhaltsseite einen Verweis auf [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client) mithilfe von Skripttags hinzu. Nachdem die Seite geladen wurde, rufen Sie sie auf `microsoftTeams.initialize()`, andernfalls wird die Seite nicht angezeigt.

* Damit die Authentifizierung auf mobilen Clients funktioniert, müssen Sie ein Upgrade auf Teams JavaScript SDK 1.4.1 und höher durchführen.

* Wenn Ihre Kanal- oder Gruppenregisterkarte auf Teams mobilen Client angezeigt werden soll, muss die `setSettings()` Konfiguration einen Wert für die `websiteUrl` Eigenschaft aufweisen.

* Microsoft Teams Registerkarte unterstützt nicht die Möglichkeit, Intranetwebsites zu laden, die selbstsignte Zertifikate verwenden.

## <a name="tools-to-build-tabs"></a>Tools zum Erstellen von Registerkarten

| &nbsp; | Installieren | Für die Verwendung... |
| --- | --- | --- |
| **Required** | &nbsp; | &nbsp; |
| &nbsp; | [Node.js](https://nodejs.org/en/download/) | Back-End-JavaScript-Laufzeitumgebung. Verwenden Sie die neueste Version von v14 LTS.|
| &nbsp; | [Microsoft Edge](https://www.microsoft.com/edge) (empfohlen) oder [Google Chrome](https://www.google.com/chrome/) | Ein Browser mit Entwicklertools. |
| &nbsp; | [Visual Studio Code](https://code.visualstudio.com/download) | JavaScript-, TypeScript- oder SharePoint-Framework-Buildumgebungen (SPFx). |
| &nbsp; | [Visual Studio 2019](https://visualstudio.com/download), **ASP.NET- und Webentwicklung** oder **.NET Core plattformübergreifende Entwicklungsarbeitsauslastung** | .NET. Sie können die kostenlose Community-Edition von Visual Studio 2019 installieren. |
| &nbsp; | [Git](https://git-scm.com/downloads) | Git zum Verwenden des Beispiel-App-Repositorys aus GitHub. |
| &nbsp; | [Microsoft Teams](https://www.microsoft.com/en-us/microsoft-teams/download-app) | Microsoft Teams, um mit allen Personen zusammenzuarbeiten, mit denen Sie über Apps für Chats, Besprechungen, Anrufe arbeiten – alles an einem Ort. |
| &nbsp; | [ngrok](https://ngrok.com/download) | Ngrok ist ein Reverseproxy-Softwaretool. Ngrok erstellt einen Tunnel zu den öffentlich verfügbaren HTTPS-Endpunkten Ihres lokal ausgeführten Webservers. Die Webendpunkte Ihres Servers sind während der aktuellen Sitzung auf Ihrem Computer verfügbar. Wenn der Computer heruntergefahren wird oder in den Ruhezustand wechselt, ist der Dienst nicht mehr verfügbar. |
| &nbsp; | [Entwicklerportal für Teams](https://dev.teams.microsoft.com/) | Webbasiertes Portal zum Konfigurieren, Verwalten und Verteilen Ihrer Teams-App, einschließlich ihrer Organisation oder des Teams Store. |

### <a name="build-your-teams-tab"></a>Erstellen der Registerkarte "Teams"

Jetzt erstellen wir Ihre Registerkarte. Wählen Sie jedoch zuerst die gewünschte Registerkarte aus, die Sie erstellen möchten:

> [!div class="nextstepaction"]
> [Erstellen einer persönlichen Registerkarte](~/tabs/how-to/create-personal-tab.md)
> [!div class="nextstepaction"]
> [Erstellen einer Kanal- oder Gruppenregisterkarte](~/tabs/how-to/create-channel-group-tab.md)

## <a name="see-also"></a>Weitere Informationen

* [registerkarten Teams](~/tabs/what-are-tabs.md)
* [Registerkarten auf mobilen Geräten](~/tabs/design/tabs-mobile.md)