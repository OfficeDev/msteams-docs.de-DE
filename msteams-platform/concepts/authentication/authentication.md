---
title: Authentifizieren von App-Benutzern
description: Beschreibt die Authentifizierung in Teams und ihre Verwendung in den Apps.
ms.topic: conceptual
ms.localizationpriority: medium
keywords: Teams-Authentifizierung OAuth SSO AAD
ms.openlocfilehash: 8a148fc6d36a94afe88d4738711b7b86850f8be9
ms.sourcegitcommit: 1431dfe08d5a19a63dbf1542a2e6c661e4dd7fc1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2021
ms.locfileid: "60949026"
---
# <a name="authenticate-users-in-microsoft-teams"></a>Authentifizieren von Benutzern in Microsoft Teams

> [!Note]
> Für die webbasierte Authentifizierung auf mobilen Clients ist Version 1.4.1 oder höher des Teams JavaScript-Client-SDKs erforderlich.

Um auf durch Azure Active Directory (AAD) geschützte Benutzerinformationen zuzugreifen und auf Daten von Diensten wie Facebook und Twitter zuzugreifen, stellt die App eine vertrauenswürdige Verbindung mit diesen Anbietern her. Wenn die App Microsoft Graph-APIs im Benutzerbereich verwendet, authentifizieren Sie den Benutzer, um die entsprechenden Authentifizierungstoken abzurufen.

In Teams gibt es zwei unterschiedliche Authentifizierungsflüsse für die App. Führen Sie einen herkömmlichen webbasierten Authentifizierungsfluss in einer [Inhaltsseite](~/tabs/how-to/create-tab-pages/content-page.md) aus, die in eine Registerkarte, eine Konfigurationsseite oder ein Aufgabenmodul eingebettet ist. Wenn die App einen Unterhaltungs-Bot enthält, verwenden Sie den OAuthPrompt-Flow und optional den Tokendienst von Azure Bot Framework, um einen Benutzer als Teil einer Unterhaltung zu authentifizieren.

## <a name="web-based-authentication-flow"></a>Webbasierter Authentifizierungsflow

Verwenden Sie den webbasierten Authentifizierungsfluss für [Registerkarten,](~/tabs/what-are-tabs.md) und wählen Sie ihn mit [Unterhaltungsbots](~/bots/what-are-bots.md) oder [Messaging-Erweiterungen.](~/messaging-extensions/what-are-messaging-extensions.md) Verwenden Sie das [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client) in einer Webinhaltsseite, um die Authentifizierung zu aktivieren. Nachdem Sie die Authentifizierung aktiviert haben, betten Sie die Inhaltsseite in eine Registerkarte, eine Konfigurationsseite oder ein Aufgabenmodul ein. Weitere Informationen zum webbasierten Authentifizierungsfluss finden Sie unter:

* [Fügen Sie dem Teams Bot eine Authentifizierung](~/bots/how-to/authentication/add-authentication.md) hinzu, in der beschrieben wird, wie der webbasierte Authentifizierungsfluss mit einem Unterhaltungsbot verwendet wird.
* [Der Authentifizierungsfluss in Registerkarten](~/tabs/how-to/authentication/auth-flow-tab.md) beschreibt, wie die Registerkartenauthentifizierung in Teams funktioniert. Dies zeigt einen typischen webbasierten Authentifizierungsfluss, der für Registerkarten verwendet wird.
* [AAD Authentifizierung in Registerkarten](~/tabs/how-to/authentication/auth-tab-AAD.md) beschreibt, wie Sie eine Verbindung mit AAD von einer Registerkarte in der App in Teams herstellen.
* [Die automatische Authentifizierung AAD](~/tabs/how-to/authentication/auth-silent-AAD.md) beschreibt, wie Anmelde- oder Zustimmungsaufforderungen in der App mithilfe von AAD reduziert werden.
* [.Net oder C#](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp) oder [JavaScript oder Node.js](https://github.com/OfficeDev/microsoft-teams-sample-complete-node) enthält Beispiele für die webbasierte Authentifizierung.

## <a name="the-oauthprompt-flow-for-conversational-bots"></a>Der OAuthPrompt-Ablauf für Unterhaltungsbots

Der OAuthPrompt-Flow von Azure Bot Framework erleichtert die Authentifizierung für Apps, die Unterhaltungs-Bots verwenden. Verwenden Sie den Tokendienst von Azure Bot Framework, um die Tokenzwischenspeicherung zu unterstützen.

Weitere Informationen zur Verwendung von OAuthPrompt finden Sie unter:

* Die Übersicht über den [Bot-Authentifizierungsfluss](~/bots/how-to/authentication/auth-flow-bot.md) beschreibt, wie die Authentifizierung innerhalb eines Bots in der App in Teams funktioniert. Dies zeigt einen nicht webbasierten Authentifizierungsfluss, der für Bots in Teams Web, Desktop-App und mobilen Apps verwendet wird.
* [Die Bot-Authentifizierung](~/bots/how-to/authentication/add-authentication.md) beschreibt, wie dem Teams Bot die OAuth-Authentifizierung hinzugefügt wird.

## <a name="code-sample"></a>Codebeispiel

bietet beispiel für die Bot-Authentifizierung v3 SDK.

| **Beispielname** | **Beschreibung** | **.NET** | **Node.js** | **Python** |
|---------------|------------|------------|-------------|---------------|
| Bot-Authentifizierung | Dieses Beispiel zeigt, wie Sie mit der Authentifizierung in einem Bot für Microsoft Teams beginnen. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/46.teams-auth) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/46.teams-auth) |
| Tab, Bot and Messaging Extension (ME) SSO | Dieses Beispiel zeigt SSO für Tab, Bot und ME – Suche, Aktion, Linkunfurl. |  [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-sso/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-sso/nodejs) | Nicht verfügbar |


## <a name="configure-the-identity-provider"></a>Konfigurieren des Identitätsanbieters

Konfigurieren Sie unabhängig vom Authentifizierungsfluss der App den Identitätsanbieter für die Kommunikation mit der Teams App. Die meisten Beispiele und exemplarischen Vorgehensweisen befassen sich hauptsächlich mit der Verwendung von AAD als Identitätsanbieter. Die Konzepte gelten jedoch unabhängig vom Identitätsanbieter. 

Weitere Informationen finden Sie unter [Konfigurieren eines Identitätsanbieters.](~/concepts/authentication/configure-identity-provider.md)

## <a name="third-party-cookies-on-ios"></a>Cookies von Drittanbietern unter iOS

Nach dem iOS 14-Update hat Apple standardmäßig den [Cookiezugriff](https://webkit.org/blog/10218/full-third-party-cookie-blocking-and-more/) von Drittanbietern für alle Apps blockiert. Daher können apps, die Cookies von Drittanbietern für die Authentifizierung auf ihren Kanal- oder Chat-Registerkarten nutzen, und persönliche Apps ihre Authentifizierungsworkflows auf Teams iOS-Clients nicht abschließen. Um den Datenschutz- und Sicherheitsanforderungen zu entsprechen, müssen Sie zu einem tokenbasierten System wechseln oder Cookies von Erstanbietern für die Benutzerauthentifizierungsworkflows verwenden.

## <a name="see-also"></a>Siehe auch

* [Microsoft Teams Authentifizierungsfluss für Registerkarten](~/tabs/how-to/authentication/auth-flow-tab.md)
* [Unterstützung für einmaliges Anmelden für Bots](~/bots/how-to/authentication/auth-aad-sso-bots.md)
* [Hinzufügen einer Authentifizierung zu Ihrer Messaging-Erweiterung](~/messaging-extensions/how-to/add-authentication.md)