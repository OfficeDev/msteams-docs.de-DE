---
title: Voraussetzungen
author: surbhigupta
description: In diesem Artikel erfahren Sie mehr über die Voraussetzungen zum Erstellen einer persönlichen, kanal- oder gruppenbasierten Registerkarte für Microsoft Teams. Kennen Sie die Tools, die zum Erstellen Ihrer Registerkarte erforderlich sind.
ms.localizationpriority: high
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 4471d88b7f9b0fd6364c833f6b3dd910aadb300a
ms.sourcegitcommit: 9ea9a70d2591bce6b8c980d22014e160f7b45f91
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2022
ms.locfileid: "68819961"
---
# <a name="prerequisites"></a>Voraussetzungen

Stellen Sie sicher, dass Sie die folgenden Voraussetzungen erfüllen, während Sie Ihre persönliche und Kanal- oder Gruppenregisterkarte für Teams erstellen:

* Lassen Sie zu, dass Ihre Tab-Seiten in einem iFrame erkannt werden, indem Sie die HTTP-Antwort-Header X-Frame-Options und Content-Security-Policy verwenden.
  * Kopfzeile setzen: `Content-Security-Policy: frame-ancestors teams.microsoft.com *.teams.microsoft.com *.skype.com`
  * Legen Sie für die Kompatibilität mit Internet Explorer 11 `X-Content-Security-Policy`.
  * Setzen Sie alternativ Header `X-Frame-Options: ALLOW-FROM https://teams.microsoft.com/`. Dieser Header ist veraltet, wird aber von den meisten Browsern noch akzeptiert.

* Anmeldeseiten werden nicht in iFrames gerendert, um sich vor Clickjacking zu schützen. Ihre Authentifizierungslogik muss eine andere Methode als die Umleitung verwenden. Verwenden Sie beispielsweise die tokenbasierte oder cookiebasierte Authentifizierung.

    > [!NOTE]
    > Es wird empfohlen, dass Sie die beabsichtigte Verwendung für Ihre Cookies festlegen, anstatt sich auf das Standardverhalten des Browsers zu verlassen. Weitere Informationen finden Sie unter [SameSite-Cookie-Attribut](../../resources/samesite-cookie-update.md).

* Die Einschränkung der Richtlinie für den gleichen Ursprung des Browsers verhindert, dass Webseiten Anfragen an andere Domänen als die bereitgestellte Webseite senden. Sie können also die Konfigurations- oder Inhaltsseite auf eine andere Domain oder Subdomain umleiten. Ihre domänenübergreifende Navigationslogik muss es dem Teams-Client ermöglichen, den Ursprung beim Laden oder Kommunizieren mit der Registerkarte anhand einer statischen `validDomains` Liste im App-Manifest zu validieren.

* Gestalten Sie Ihre Registerkarten basierend auf dem Design, dem Design und der Absicht des Teams-Clients. Registerkarten funktionieren am besten, wenn sie für einen bestimmten Bedarf erstellt wurden und sich auf eine kleine Gruppe von Aufgaben oder eine Teilmenge von Daten konzentrieren, die für die Kanalposition der Registerkarte relevant sind.

* Fügen Sie auf Ihrer Inhaltsseite mithilfe von Skript-Tags einen Verweis auf das JavaScript-Client-SDK von [Microsoft Teams](/javascript/api/overview/msteams-client) hinzu. Nachdem die Seite geladen wurde, rufen Sie auf, `app.initialize()`andernfalls wird Ihre Seite nicht angezeigt.

* Damit die Authentifizierung auf mobilen Clients funktioniert, müssen Sie auf Teams JavaScript SDK 1.4.1 und höher aktualisieren.

* Wenn Sie festlegen, dass Ihre Kanal- oder Gruppenregisterkarte auf dem mobilen Teams-Client angezeigt wird, muss die `setConfig()` Konfiguration einen Wert für die `websiteUrl` Eigenschaft aufweisen.

* Die Registerkarte Microsoft Teams unterstützt nicht die Möglichkeit, Intranetwebsites zu laden, die selbstsignierte Zertifikate verwenden.

[!INCLUDE [sdk-include](~/includes/sdk-include.md)]

## <a name="tools-to-build-tabs"></a>Tools zum Erstellen von Registerkarten

| &nbsp; | Installieren | Zum Benutzen... |
| --- | --- | --- |
| **Required** | &nbsp; | &nbsp; |
| &nbsp; | [Node.js](https://nodejs.org/en/download/) | Back-End-JavaScript-Laufzeitumgebung. Verwenden Sie das neueste v16 LTS-Release.|
| &nbsp; | [Microsoft Edge](https://www.microsoft.com/edge) (empfohlen) oder [Google Chrome](https://www.google.com/chrome/) | Ein Browser mit Entwicklertools. |
| &nbsp; | [Visual Studio Code](https://code.visualstudio.com/download) | Build-Umgebungen für JavaScript, TypeScript oder SharePoint Framework (SPFx). |
| &nbsp; | [Visual Studio 2022](https://visualstudio.microsoft.com), **ASP.NET- und Webentwicklung** oder **plattformübergreifende .NET Core-Entwicklungsworkload** | .NET. Sie können die kostenlose Community-Edition von Visual Studio 2022 installieren. |
| &nbsp; | [Git](https://git-scm.com/downloads) | Git, um das Repository für Beispiel-Apps von GitHub zu verwenden. |
| &nbsp; | [Microsoft Teams](https://www.microsoft.com/en-us/microsoft-teams/download-app) | Microsoft Teams für die Zusammenarbeit mit allen, mit denen Sie zusammenarbeiten, über Apps für Chats, Besprechungen und Anrufe – alles an einem Ort. |
| &nbsp; | [ngrok](https://ngrok.com/download) | Ngrok ist ein Reverse-Proxy-Softwaretool. Ngrok erstellt einen Tunnel zu den öffentlich verfügbaren HTTPS-Endpunkten Ihres lokal ausgeführten Webservers. Die Webendpunkte Ihres Servers sind während der aktuellen Sitzung auf Ihrem Computer verfügbar. Wenn der Computer heruntergefahren wird oder in den Energiesparmodus wechselt, ist der Dienst nicht mehr verfügbar. |
| &nbsp; | [Entwicklerportal für Teams](https://dev.teams.microsoft.com/) | Webbasiertes Portal zum Konfigurieren, Verwalten und Verteilen Ihrer Teams-App, einschließlich an Ihre Organisation oder den Teams-Store. |

### <a name="build-your-teams-tab"></a>Erstellen Sie Ihre Registerkarte "Teams".

Lassen Sie uns jetzt Ihren Tab erstellen. Aber wählen Sie zuerst die Registerkarte Ihrer Wahl aus, die Sie erstellen möchten:

> [!div class="nextstepaction"]
> [Erstellen einer persönlichen Registerkarte](~/tabs/how-to/create-personal-tab.md)
> [!div class="nextstepaction"]
> [Erstellen Sie einen Kanal- oder Gruppen-Tab](~/tabs/how-to/create-channel-group-tab.md)

## <a name="see-also"></a>Siehe auch

* [Erstellen von Registerkarten für Teams](../what-are-tabs.md)
* [Erstellen Ihrer ersten Registerkarten-App mit JavaScript](../../sbs-gs-javascript.yml)
* [Registrieren Ihrer Registerkarten-App in Azure AD](authentication/tab-sso-register-aad.md)
* [Registerkarten auf mobilen Geräten](~/tabs/design/tabs-mobile.md)
