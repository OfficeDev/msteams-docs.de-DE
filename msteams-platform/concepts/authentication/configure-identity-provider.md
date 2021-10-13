---
title: Konfigurieren von OAuth 2.0-Identitätsanbietern
description: Beschreibt, wie Identitätsanbieter konfiguriert werden, deren Schwerpunkt auf Azure AD
ms.topic: how-to
ms.localizationpriority: medium
keywords: Teams-Authentifizierung AAD oauth-Identitätsanbieter
ms.openlocfilehash: d14dc4811faae13535ad1029a8820c5904f44774
ms.sourcegitcommit: 37b1724bb0d2f1b087c356e0fd0ff80145671e22
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2021
ms.locfileid: "60291618"
---
# <a name="configure-identity-providers"></a>Identitätsanbieter konfigurieren

## <a name="configuring-an-application-to-use-azure-active-directory-as-an-identity-provider"></a>Konfigurieren einer Anwendung für die Verwendung von Azure Active Directory als Identitätsanbieter

Identitätsanbieter, die OAuth 2.0 unterstützen, authentifizieren keine Anforderungen von unbekannten Anwendungen. Anwendungen müssen vorab registriert werden. Führen Sie die folgenden Schritte aus, um dies mit Azure AD zu tun:

1. Öffnen Sie das [Anwendungsregistrierungsportal.](https://ms.portal.azure.com/#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade)

2. Wählen Sie Ihre App aus, um ihre Eigenschaften anzuzeigen, oder klicken Sie auf die Schaltfläche "Neue Registrierung". Suchen Sie den **Abschnitt "Umleitungs-URI"** für die App.

3. Stellen Sie im Dropdownmenü sicher, dass **"Web"** ausgewählt ist. Aktualisieren Sie die URL zu Ihrem Authentifizierungsendpunkt. Für die TypeScript/Node.js- und C#-Beispiel-Apps auf GitHub ähneln die Umleitungs-URLs folgendem:

    Umleitungs-URLs: `https://<hostname>/bot-auth/simple-start`

Ersetzen Sie `<hostname>` dies durch Ihren tatsächlichen Host. Dies kann eine dedizierte Hostingwebsite wie Azure, Glitch oder ein ngrok-Tunnel zu localhost auf Ihrem Entwicklungscomputer sein, z. `abcd1234.ngrok.io` B. . Möglicherweise verfügen Sie nicht über diese Informationen, wenn Sie Ihre App nicht abgeschlossen oder gehostet haben (oder die oben genannte Beispiel-App), aber Sie können immer zu dieser Seite zurückkehren, wenn diese Informationen bekannt sind.

## <a name="other-authentication-providers"></a>Andere Authentifizierungsanbieter

* **LinkedIn:** Folgen Sie den Anweisungen beim [Konfigurieren Ihrer LinkedIn-Anwendung.](/linkedin/talent/apply-with-linkedin)

* **Google:** Abrufen von OAuth 2.0-Clientanmeldeinformationen aus der [Google API-Konsole](https://console.developers.google.com/)
