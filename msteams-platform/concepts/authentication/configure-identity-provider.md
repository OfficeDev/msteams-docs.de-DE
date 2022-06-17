---
title: Konfigurieren von OAuth 2.0-Identitätsanbietern
description: In diesem Modul erfahren Sie, wie Sie Identitätsanbieter mit dem Fokus auf Microsoft Azure Active Directory (Azure AD) konfigurieren.
ms.topic: how-to
ms.localizationpriority: medium
ms.openlocfilehash: 2d344fb5ffcbde35ad9e85eed9ea662d2a0ca9f6
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2022
ms.locfileid: "66143445"
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

* [Authentifizieren eines Benutzers in einem Microsoft Teams Bot](../../resources/bot-v3/bot-authentication/auth-bot-AAD.md)
* [Unterstützung für einmaliges Anmelden (SSO) für Registerkarten](../../tabs/how-to/authentication/tab-sso-overview.md)
* [Authentifizieren eines Benutzers auf einer Microsoft Teams Registerkarte](../../tabs/how-to/authentication/auth-tab-aad.md)
