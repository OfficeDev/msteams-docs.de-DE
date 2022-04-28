---
title: Authentifizieren von App-Benutzern
description: Beschreibt die Authentifizierung in Teams und deren Verwendung in den Apps
ms.topic: conceptual
ms.localizationpriority: medium
keywords: Teams-Authentifizierung OAuth SSO Microsoft Azure Active Directory (Azure AD)
ms.openlocfilehash: 811b8917297ad8fe1420f4887983b93f43cd73b3
ms.sourcegitcommit: 0117c4e750a388a37cc189bba8fc0deafc3fd230
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2022
ms.locfileid: "65103958"
---
# <a name="authenticate-users-in-microsoft-teams"></a>Authentifizieren von Benutzern in Microsoft Teams

> [!Note]
> Die webbasierte Authentifizierung auf mobilen Clients erfordert Version 1.4.1 oder höher des Teams JavaScript-Client-SDK.

Um auf durch Azure AD geschützte Benutzerinformationen zuzugreifen und auf Daten von Diensten wie Facebook und Twitter zuzugreifen, stellt die App eine vertrauenswürdige Verbindung mit diesen Anbietern her. Wenn die App Microsoft Graph-APIs im Benutzerbereich verwendet, authentifizieren Sie den Benutzer, um die entsprechenden Authentifizierungstoken abzurufen.

In Teams gibt es zwei unterschiedliche Authentifizierungsflüsse für die App. Führen Sie einen herkömmlichen webbasierten Authentifizierungsfluss in einer [Inhaltsseite](~/tabs/how-to/create-tab-pages/content-page.md) aus, die in eine Registerkarte, eine Konfigurationsseite oder ein Aufgabenmodul eingebettet ist. Wenn die App einen Unterhaltungs-Bot enthält, verwenden Sie den OAuthPrompt-Flow und optional den Tokendienst von Azure Bot Framework, um einen Benutzer als Teil einer Unterhaltung zu authentifizieren.

## <a name="web-based-authentication-flow"></a>Webbasierter Authentifizierungsflow

Verwenden Sie den webbasierten [Authentifizierungsfluss für Registerkarten](~/tabs/what-are-tabs.md) , und wählen Sie ihn für [Unterhaltungs-Bots](~/bots/what-are-bots.md) oder [Nachrichtenerweiterungen](~/messaging-extensions/what-are-messaging-extensions.md) aus. Verwenden Sie das [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client) in einer Webinhaltsseite, um die Authentifizierung zu aktivieren. Nachdem Sie die Authentifizierung aktiviert haben, betten Sie die Inhaltsseite in eine Registerkarte, eine Konfigurationsseite oder ein Aufgabenmodul ein. Weitere Informationen zum webbasierten Authentifizierungsfluss finden Sie unter:

* [Das Hinzufügen der Authentifizierung zum Teams Bot](~/bots/how-to/authentication/add-authentication.md) beschreibt, wie Sie den webbasierten Authentifizierungsfluss mit einem unterhaltungsbasierten Bot verwenden.
* [Der Authentifizierungsfluss in Registerkarten](~/tabs/how-to/authentication/auth-flow-tab.md) beschreibt, wie die Registerkartenauthentifizierung in Teams funktioniert. Dies zeigt einen typischen webbasierten Authentifizierungsfluss, der für Registerkarten verwendet wird.
* [Azure AD Authentifizierung in Registerkarten](~/tabs/how-to/authentication/auth-tab-AAD.md) beschreibt, wie Sie eine Verbindung mit Azure AD innerhalb einer Registerkarte in der App in Teams herstellen.
* [Die automatische Authentifizierung Azure AD](~/tabs/how-to/authentication/auth-silent-AAD.md) beschreibt, wie Anmelde- oder Zustimmungsaufforderungen in der App mithilfe von Azure AD reduziert werden.
* [.Net oder C#](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp) oder [JavaScript oder Node.js](https://github.com/OfficeDev/microsoft-teams-sample-complete-node) stellt Beispiele für die webbasierte Authentifizierung bereit.

## <a name="the-oauthprompt-flow-for-conversational-bots"></a>Der OAuthPrompt-Fluss für Unterhaltungsbots

Der OAuthPrompt-Flow von Azure Bot Framework erleichtert die Authentifizierung für Apps, die Unterhaltungs-Bots verwenden. Verwenden Sie den Tokendienst von Azure Bot Framework, um die Tokenzwischenspeicherung zu unterstützen.

Weitere Informationen zur Verwendung von OAuthPrompt finden Sie unter:

* [Die Übersicht über den Botauthentifizierungsfluss](~/bots/how-to/authentication/auth-flow-bot.md) beschreibt, wie die Authentifizierung innerhalb eines Bots in der App in Teams funktioniert. Dies zeigt einen nicht webbasierten Authentifizierungsfluss, der für Bots in Teams Web-, Desktop-App und mobilen Apps verwendet wird.
* Die [Botauthentifizierung](~/bots/how-to/authentication/add-authentication.md) beschreibt, wie die OAuth-Authentifizierung dem Teams Bot hinzugefügt wird.

## <a name="code-sample"></a>Codebeispiel

bietet Beispiel für botauthentifizierung v3 SDK.

| **Beispielname** | **Beschreibung** | **.NET** | **Node.js** | **Python** |
|---------------|------------|------------|-------------|---------------|
| Bot-Authentifizierung | In diesem Beispiel wird gezeigt, wie Sie mit der Authentifizierung in einem Bot für Microsoft Teams beginnen. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/46.teams-auth) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/46.teams-auth) |
| Registerkarten-, Bot- und Nachrichtenerweiterungs-SSO (ME) | Dieses Beispiel zeigt SSO für Tab, Bot und ME – Suche, Aktion, linkunfurl. |  [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-sso/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-sso/nodejs) | Nicht verfügbar |

## <a name="configure-the-identity-provider"></a>Konfigurieren des Identitätsanbieters

Konfigurieren Sie unabhängig vom Authentifizierungsfluss der App den Identitätsanbieter für die Kommunikation mit der Teams App. In den meisten Beispielen und Exemplaren geht es in erster Linie um die Verwendung von Azure AD als Identitätsanbieter. Die Konzepte gelten jedoch unabhängig vom Identitätsanbieter.

Weitere Informationen finden Sie [unter Konfigurieren eines Identitätsanbieters](~/concepts/authentication/configure-identity-provider.md).

## <a name="third-party-cookies-on-ios"></a>Cookies von Drittanbietern unter iOS

Nach dem iOS 14-Update hat Apple standardmäßig den Zugriff auf [Cookies von Drittanbietern](https://webkit.org/blog/10218/full-third-party-cookie-blocking-and-more/) für alle Apps blockiert. Daher können Apps, die Cookies von Drittanbietern für die Authentifizierung auf ihren Registerkarten "Kanal" oder "Chat" und "Persönliche Apps" verwenden, ihre Authentifizierungsworkflows auf Teams iOS-Clients nicht abschließen. Um den Datenschutz- und Sicherheitsanforderungen zu entsprechen, müssen Sie zu einem tokenbasierten System wechseln oder Cookies von Erstanbietern für die Benutzerauthentifizierungsworkflows verwenden.

## <a name="see-also"></a>Siehe auch

* [Microsoft Teams-Authentifizierungsablauf für Registerkarten](~/tabs/how-to/authentication/auth-flow-tab.md)
* [Unterstützung für einmaliges Anmelden für Bots](~/bots/how-to/authentication/auth-aad-sso-bots.md)
* [Hinzufügen der Authentifizierung zu Ihrer Nachrichtenerweiterung](~/messaging-extensions/how-to/add-authentication.md)
