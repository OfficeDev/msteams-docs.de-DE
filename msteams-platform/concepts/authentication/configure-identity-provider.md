---
title: Konfigurieren von OAuth 2.0-Identitätsanbietern
description: Beschreibt, wie Identitätsanbieter mit einem Fokus auf Microsoft Azure Active Directory (Azure AD) konfiguriert werden.
ms.topic: how-to
ms.localizationpriority: medium
keywords: Teams-Authentifizierung – Azure AD-OAuth-Identitätsanbieter
ms.openlocfilehash: 6fb17041e9169b4d5e74295cbb62ea97c8befd0f
ms.sourcegitcommit: e16b51a49756e0fe4eaf239898e28d3021f552da
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2022
ms.locfileid: "65887569"
---
# <a name="configure-identity-providers"></a>Identitätsanbieter konfigurieren

## <a name="configuring-an-application-to-use-azure-ad-as-an-identity-provider"></a>Konfigurieren einer Anwendung zur Verwendung von Azure AD als Identitätsanbieter

Identitätsanbieter, die OAuth 2.0 unterstützen, authentifizieren keine Anforderungen von unbekannten Anwendungen. Anwendungen müssen vorab registriert werden. Führen Sie die folgenden Schritte aus, um dies mit Azure AD zu tun:

1. Öffnen Sie das [Anwendungsregistrierungsportal](https://ms.portal.azure.com/#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade).

2. Wählen Sie Ihre App aus, um deren Eigenschaften anzuzeigen, oder wählen Sie die Schaltfläche "Neue Registrierung" aus. Suchen Sie den **Abschnitt "Umleitungs-URI** " für die App.

3. Wählen Sie im Dropdownmenü " **Web** " aus. Aktualisieren Sie die URL zu Ihrem Authentifizierungsendpunkt. Für die TypeScript/Node.js- und C#-Beispiel-Apps auf GitHub ähneln die Umleitungs-URLs den folgenden:

    Umleitungs-URLs: `https://<hostname>/bot-auth/simple-start`

Ersetzen Sie `<hostname>` ihren eigentlichen Host, der eine dedizierte Hostingwebsite wie Azure, Glitch oder ein ngrok-Tunnel zu localhost auf Ihrem Entwicklungscomputer sein kann, z `abcd1234.ngrok.io`. B. . Möglicherweise verfügen Sie nicht über diese Informationen, wenn Sie Ihre App (oder die oben erwähnte Beispiel-App) noch nicht abgeschlossen oder gehostet haben, aber Sie können immer zu dieser Seite zurückkehren, wenn diese Informationen bekannt sind.

## <a name="other-authentication-providers"></a>Andere Authentifizierungsanbieter

* **Linkedin:** Befolgen Sie die Anweisungen unter [Konfigurieren der LinkedIn-Anwendung](/linkedin/talent/apply-with-linkedin)

* **Google:** Abrufen von OAuth 2.0-Clientanmeldeinformationen aus der [Google API-Konsole](https://console.developers.google.com/)

* **Externe OAuth-Anbieter über Registerkarten:** Weitere Informationen finden [Sie unter Verwenden externer OAuth-Anbieter](../../tabs/how-to/authentication/auth-oauth-provider.md)

## <a name="see-also"></a>Siehe auch

* [Authentifizieren eines Benutzers in einem Microsoft Teams-Bot](../../resources/bot-v3/bot-authentication/auth-bot-AAD.md)
* [Unterstützung für einmaliges Anmelden (SSO) für Registerkarten](../../tabs/how-to/authentication/tab-sso-overview.md)
* [Authentifizieren eines Benutzers auf einer Microsoft Teams-Registerkarte](../../tabs/how-to/authentication/auth-tab-aad.md)
