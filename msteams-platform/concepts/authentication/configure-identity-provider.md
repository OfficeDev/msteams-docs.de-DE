---
title: Konfigurieren von OAuth 2.0-Identitätsanbietern
description: Beschreibt das Konfigurieren von Identitätsanbietern mit dem Fokus auf Azure AD
ms.topic: how-to
localization_priority: Normal
keywords: teams authentication AAD oauth identity provider
ms.openlocfilehash: ffcf376ea6c4f1a94d797413af22af867dbd5b53
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020856"
---
# <a name="configure-identity-providers"></a>Identitätsanbieter konfigurieren

## <a name="configuring-an-application-to-use-azure-active-directory-as-an-identity-provider"></a>Konfigurieren einer Anwendung zur Verwendung von Azure Active Directory als Identitätsanbieter

Identitätsanbieter, die OAuth 2.0 unterstützen, authentifizieren keine Anforderungen unbekannter Anwendungen. Anwendungen müssen im Voraus registriert werden. Führen Sie die folgenden Schritte aus, um dies mit Azure AD zu tun:

1. Öffnen Sie [das Anwendungsregistrierungsportal](https://ms.portal.azure.com/#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade).

2. Wählen Sie Ihre App aus, um ihre Eigenschaften anzeigen zu können, oder klicken Sie auf die Schaltfläche "Neue Registrierung". Suchen Sie **den Abschnitt Umleitungs-URI** für die App.

3. Stellen Sie im Dropdownmenü sicher, dass **Web** ausgewählt ist. Aktualisieren Sie die URL auf Ihren Authentifizierungsendpunkt. Für die TypeScript/Node.js- und C#-Beispiel-Apps auf GitHub sind die Umleitungs-URLs wie die folgenden:

    Umleitungs-URLs: `https://<hostname>/bot-auth/simple-start`

Ersetzen `<hostname>` Sie durch Den tatsächlichen Host. Dies kann eine dedizierte Hostingwebsite wie Azure, Glitch oder ein ngrok-Tunnel zu localhost auf Ihrem Entwicklungscomputer sein, z. B. `abcd1234.ngrok.io` . Diese Informationen sind möglicherweise noch nicht verfügbar, wenn Sie Ihre App (oder die oben genannte Beispiel-App) noch nicht abgeschlossen oder gehostet haben. Sie können jedoch immer zu dieser Seite zurückkehren, wenn diese Informationen bekannt sind.

## <a name="other-authentication-providers"></a>Andere Authentifizierungsanbieter

* **LinkedIn** Befolgen Sie die Anweisungen unter [Configuring your LinkedIn application](/linkedin/talent/apply-with-linkedin)

* **Google** Abrufen von OAuth 2.0-Clientanmeldeinformationen aus der [Google-API-Konsole](https://console.developers.google.com/)
