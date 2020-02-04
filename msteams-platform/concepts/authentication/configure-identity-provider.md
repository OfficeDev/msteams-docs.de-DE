---
title: Konfigurieren von OAuth 2,0-Identitätsanbietern
description: Beschreibt, wie Identitätsanbieter mit einem Fokus auf Azure AD konfiguriert werden.
keywords: Teams-Authentifizierung Aad OAuth Identity Provider
ms.openlocfilehash: 799b0c20cda64456a4610acbdbedf758989bee55
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674463"
---
# <a name="configuring-identity-providers"></a>Konfigurieren von Identitätsanbietern

## <a name="configuring-an-application-to-use-azure-active-directory-as-an-identity-provider"></a>Konfigurieren einer Anwendung für die Verwendung von Azure Active Directory als Identitätsanbieter

Identitätsanbieter, die OAuth 2,0 unterstützen, authentifizieren keine Anforderungen von unbekannten Anwendungen; Anwendungen müssen frühzeitig registriert werden. Führen Sie dazu die folgenden Schritte aus Azure AD aus:

1. Öffnen Sie das [Anwendungs Registrierungs Portal](https://ms.portal.azure.com/#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade).

2. Wählen Sie Ihre APP aus, um die Eigenschaften anzuzeigen, oder klicken Sie auf die Schaltfläche "neue Registrierung". Suchen Sie den Abschnitt **Umleitungs-URI** für die app.

3. Stellen Sie sicher, dass im Dropdownmenü die Option **Internet** ausgewählt ist. Aktualisieren Sie die URL auf Ihren Authentifizierungs Endpunkt. Die Umleitungs-URLs sind für die Beispielanwendungen "Code/Node. js" und "C#" auf GitHub ähnlich:

    Umleitungs-URLs:`https://<hostname>/bot-auth/simple-start`

Ersetzen `<hostname>` Sie durch ihren tatsächlichen Host. Dies kann eine dedizierte Hostwebsite wie Azure, glitch oder ein ngrok-Tunnel sein, der auf dem Entwicklungscomputer wie `abcd1234.ngrok.io`. Sie verfügen möglicherweise noch nicht über diese Informationen, wenn Sie Ihre APP (oder die oben erwähnte Beispiel-APP) nicht abgeschlossen oder gehostet haben, aber Sie können jederzeit zu dieser Seite zurückkehren, wenn diese Informationen bekannt sind.

## <a name="other-authentication-providers"></a>Andere Authentifizierungsanbieter

* **LinkedIn** Befolgen Sie die Anweisungen unter [Konfigurieren ihrer LinkedIn-Anwendung](https://developer.linkedin.com/docs/oauth2) .

* **Google** - Abrufen von OAuth 2,0-Clientanmeldeinformationen über die [Google-API-Konsole](https://console.developers.google.com/)
