---
title: Konfigurieren von OAuth 2.0-Identitätsanbietern
description: Beschreibt, wie Identitätsanbieter konfiguriert werden, deren Schwerpunkt auf Microsoft Azure Active Directory (Azure AD) liegt.
ms.topic: how-to
ms.localizationpriority: medium
keywords: Teams-Authentifizierung Azure AD oauth-Identitätsanbieter
ms.openlocfilehash: b35f28f2cb306a6dfc3ae3151616925da1525069
ms.sourcegitcommit: b9af51e24c9befcf46945400789e750c34723e56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2022
ms.locfileid: "62821353"
---
# <a name="configure-identity-providers"></a>Identitätsanbieter konfigurieren

## <a name="configuring-an-application-to-use-azure-ad-as-an-identity-provider"></a>Konfigurieren einer Anwendung für die Verwendung von Azure AD als Identitätsanbieter

Identitätsanbieter, die OAuth 2.0 unterstützen, authentifizieren keine Anforderungen von unbekannten Anwendungen; Anwendungen müssen vorab registriert werden. Führen Sie die folgenden Schritte aus, um dies mit Azure AD zu tun:

1. Öffnen Sie das [Anwendungsregistrierungsportal](https://ms.portal.azure.com/#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade).

2. Wählen Sie Ihre App aus, um ihre Eigenschaften anzuzeigen, oder wählen Sie die Schaltfläche "Neue Registrierung" aus. Suchen Sie den **Abschnitt "Umleitungs-URI** " für die App.

3. Wählen Sie im Dropdownmenü die Option **Web** aus. Aktualisieren Sie die URL zu Ihrem Authentifizierungsendpunkt. Für die TypeScript/Node.js- und C#-Beispiel-Apps auf GitHub ähneln die Umleitungs-URLs den folgenden:

    Umleitungs-URLs: `https://<hostname>/bot-auth/simple-start`

Ersetzen Sie `<hostname>` dies durch Ihren tatsächlichen Host, bei dem es sich möglicherweise um eine dedizierte Hostingwebsite wie Azure, Glitch oder einen ngrok-Tunnel zu localhost auf Ihrem Entwicklungscomputer wie `abcd1234.ngrok.io`z. B. . Möglicherweise verfügen Sie nicht über diese Informationen, wenn Sie Ihre App nicht abgeschlossen oder gehostet haben (oder die oben genannte Beispiel-App), aber Sie können immer zu dieser Seite zurückkehren, wenn diese Informationen bekannt sind.

## <a name="other-authentication-providers"></a>Andere Authentifizierungsanbieter

* **Linkedin:** Folgen Sie den Anweisungen beim [Konfigurieren Ihrer LinkedIn-Anwendung](/linkedin/talent/apply-with-linkedin).

* **Google:** Abrufen von OAuth 2.0-Clientanmeldeinformationen aus der [Google API-Konsole](https://console.developers.google.com/)
