---
title: Konfigurieren von OAuth 2.0-Identitätsanbietern
description: Beschreibt, wie Identitätsanbieter mit Schwerpunkt Azure AD konfiguriert werden
ms.topic: how-to
localization_priority: Normal
keywords: Teams-Authentifizierung AAD oauth identity provider
ms.openlocfilehash: f41e03717c24095b527adc471a89f8aee5de3a3ddba8773376fca49ee12bbbcc
ms.sourcegitcommit: 3ab1cbec41b9783a7abba1e0870a67831282c3b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2021
ms.locfileid: "57705566"
---
# <a name="configure-identity-providers"></a>Identitätsanbieter konfigurieren

## <a name="configuring-an-application-to-use-azure-active-directory-as-an-identity-provider"></a>Konfigurieren einer Anwendung für die Verwendung von Azure Active Directory als Identitätsanbieter

Identitätsanbieter, die OAuth 2.0 unterstützen, authentifizieren keine Anforderungen von unbekannten Anwendungen; Anwendungen müssen vorab registriert werden. Führen Sie die folgenden Schritte aus, um dies mit Azure AD zu tun:

1. Öffnen Sie das [Anwendungsregistrierungsportal.](https://ms.portal.azure.com/#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade)

2. Wählen Sie Ihre App aus, um ihre Eigenschaften anzuzeigen, oder klicken Sie auf die Schaltfläche "Neue Registrierung". Suchen Sie den **Abschnitt "Umleitungs-URI"** für die App.

3. Stellen Sie im Dropdownmenü sicher, dass **"Web"** ausgewählt ist. Aktualisieren Sie die URL zu Ihrem Authentifizierungsendpunkt. Für die TypeScript/Node.js- und C#-Beispiel-Apps auf GitHub ähneln die Umleitungs-URLs folgendem:

    Umleitungs-URLs: `https://<hostname>/bot-auth/simple-start`

Ersetzen Sie `<hostname>` dies durch Ihren tatsächlichen Host. Dies kann eine dedizierte Hostingwebsite wie Azure, Glitch oder ein ngrok-Tunnel zu localhost auf Ihrem Entwicklungscomputer sein, z. `abcd1234.ngrok.io` B. . Möglicherweise verfügen Sie noch nicht über diese Informationen, wenn Sie Ihre App (oder die oben genannte Beispiel-App) nicht abgeschlossen oder gehostet haben. Sie können jedoch jederzeit zu dieser Seite zurückkehren, wenn diese Informationen bekannt sind.

## <a name="other-authentication-providers"></a>Andere Authentifizierungsanbieter

* **LinkedIn** Folgen Sie den Anweisungen beim [Konfigurieren Ihrer LinkedIn-Anwendung.](/linkedin/talent/apply-with-linkedin)

* **Google** Abrufen von OAuth 2.0-Clientanmeldeinformationen aus der [Google API-Konsole](https://console.developers.google.com/)
