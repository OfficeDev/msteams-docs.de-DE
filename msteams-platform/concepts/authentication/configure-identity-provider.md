---
title: Konfigurieren von OAuth 2.0-Identitätsanbietern
description: Beschreibt, wie Identitätsanbieter mit Einem Fokus auf Azure AD konfiguriert werden
ms.topic: how-to
keywords: Teams authentication AAD oauth identity provider
ms.openlocfilehash: b5ffd6c4c1edd2c4315ea1e31474a626de53aba1
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014467"
---
# <a name="configure-identity-providers"></a>Identitätsanbieter konfigurieren

## <a name="configuring-an-application-to-use-azure-active-directory-as-an-identity-provider"></a>Konfigurieren einer Anwendung für die Verwendung von Azure Active Directory als Identitätsanbieter

Identitätsanbieter, die OAuth 2.0 unterstützen, authentifizieren keine Anforderungen von unbekannten Anwendungen. Anwendungen müssen im Voraus registriert werden. Führen Sie die folgenden Schritte aus, um dies mit Azure AD zu tun:

1. Öffnen Sie [das Anwendungsregistrierungsportal.](https://ms.portal.azure.com/#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade)

2. Wählen Sie Ihre App aus, um ihre Eigenschaften anzeigen zu können, oder klicken Sie auf die Schaltfläche "Neue Registrierung". Suchen Sie den **Abschnitt "Umleitungs-URI"** für die App.

3. Stellen Sie im Dropdownmenü sicher, dass **"Web"** ausgewählt ist. Aktualisieren Sie die URL auf Ihren Authentifizierungsendpunkt. Für die TypeScript/Node.js- und C#-Beispiel-Apps auf GitHub sind die Umleitungs-URLs ähnlich wie die folgenden:

    Umleitungs-URLs: `https://<hostname>/bot-auth/simple-start`

Ersetzen `<hostname>` Sie dies durch den tatsächlichen Host. Dies kann eine dedizierte Hostingwebsite wie Azure, Glitch oder ein ngrok-Tunnel zu localhost auf Ihrem Entwicklungscomputer sein, z. B. `abcd1234.ngrok.io` . Sie verfügen möglicherweise noch nicht über diese Informationen, wenn Sie Ihre App (oder die oben erwähnte Beispiel-App) noch nicht abgeschlossen oder gehostet haben. Sie können jedoch jederzeit zu dieser Seite zurückkehren, wenn diese Informationen bekannt sind.

## <a name="other-authentication-providers"></a>Andere Authentifizierungsanbieter

* **LinkedIn** Befolgen Sie die Anweisungen unter ["Konfigurieren der LinkedIn-Anwendung".](https://developer.linkedin.com/docs/oauth2)

* **Google** Abrufen von OAuth 2.0-Clientanmeldeinformationen aus der [Google -API-Konsole](https://console.developers.google.com/)
