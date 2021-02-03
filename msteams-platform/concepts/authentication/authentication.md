---
title: Authentifizieren von App-Benutzern
description: Beschreibt die Authentifizierung in Teams und deren Verwendung in den Apps
ms.topic: conceptual
keywords: Teams authentication OAuth SSO AAD
ms.openlocfilehash: 88b2098b7d45444cf47bebdfccc22fae772b7c22
ms.sourcegitcommit: 843da1730443ff8474a05295f60a6b376ed140da
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/02/2021
ms.locfileid: "50073103"
---
# <a name="authenticate-users-in-microsoft-teams"></a>Authentifizieren von Benutzern in Microsoft Teams

> [!NOTE]
> Für die webbasierte Authentifizierung auf mobilen Clients ist Version 1.4.1 oder höher des Microsoft Teams JavaScript SDK erforderlich.

Für den Zugriff auf Benutzerinformationen, die durch Azure Active Directory (AAD) geschützt sind, und für den Zugriff auf Daten von Diensten wie Facebook und Twitter richtet die App eine vertrauenswürdige Verbindung mit diesen Anbietern ein. Wenn die App Microsoft Graph-APIs im Benutzerbereich verwendet, authentifizieren Sie den Benutzer, um die entsprechenden Authentifizierungstoken abzurufen.

In Teams gibt es zwei verschiedene Authentifizierungsflüsse für die App. Durchführen eines herkömmlichen webbasierten [](~/tabs/how-to/create-tab-pages/content-page.md) Authentifizierungsflusses auf einer Inhaltsseite, die in eine Registerkarte, eine Konfigurationsseite oder ein Aufgabenmodul eingebettet ist. Wenn die App einen Unterhaltungsbot enthält, verwenden Sie den OAuthPrompt-Fluss und optional den Tokendienst des Azure Bot Framework, um einen Benutzer im Rahmen einer Unterhaltung zu authentifizieren.

## <a name="web-based-authentication-flow"></a>Webbasierter Authentifizierungsfluss

Verwenden Sie den webbasierten [Authentifizierungsfluss](~/tabs/what-are-tabs.md) für Registerkarten, und wählen Sie ihn für [Unterhaltungsbots oder](~/bots/what-are-bots.md) [Messagingerweiterungen aus.](~/messaging-extensions/what-are-messaging-extensions.md) Verwenden Sie [das Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client) auf einer Webinhaltsseite, um die Authentifizierung zu aktivieren. Betten Sie nach dem Aktivieren der Authentifizierung die Inhaltsseite in eine Registerkarte, eine Konfigurationsseite oder ein Aufgabenmodul ein. Weitere Informationen zum webbasierten Authentifizierungsfluss finden Sie unter:

* [Das Hinzufügen von Authentifizierung zum Teams-Bot](~/bots/how-to/authentication/add-authentication.md) beschreibt die Verwendung des webbasierten Authentifizierungsflusses mit einem Unterhaltungsbot.
* [Der Authentifizierungsfluss auf Registerkarten](~/tabs/how-to/authentication/auth-flow-tab.md) beschreibt, wie die Registerkartenauthentifizierung in Teams funktioniert. Dies zeigt einen typischen webbasierten Authentifizierungsfluss, der für Registerkarten verwendet wird.
* [Die AAD-Authentifizierung in Registerkarten](~/tabs/how-to/authentication/auth-tab-AAD.md) beschreibt, wie Sie von einer Registerkarte in der App in Teams aus eine Verbindung mit AAD herstellen.
* [AAD für die automatische Authentifizierung](~/tabs/how-to/authentication/auth-silent-AAD.md) beschreibt, wie Anmelde- oder Zustimmungsaufforderungen in der App mithilfe von AAD reduziert werden.
* [.Net oder C# oder](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp) [JavaScript oder Node.js](https://github.com/OfficeDev/microsoft-teams-sample-complete-node) bietet Beispiele für die webbasierte Authentifizierung.

## <a name="the-oauthprompt-flow-for-conversational-bots"></a>Der OAuthPrompt-Fluss für Unterhaltungsbots

Das OAuthPrompt des Azure Bot Framework erleichtert die Authentifizierung für Apps, die unterhaltungsbasierte Bots verwenden. Verwenden Sie den Tokendienst von Azure Bot Framework, um die Zwischenspeicherung von Token zu unterstützen.

Weitere Informationen zur Verwendung von OAuthPrompt finden Sie unter:

* [Übersicht über den](~/bots/how-to/authentication/auth-flow-bot.md) Botauthentifizierungsfluss beschreibt, wie die Authentifizierung innerhalb eines Bots in der App in Teams funktioniert. Dies zeigt einen nicht webbasierten Authentifizierungsfluss, der für Bots in Teams-Web-, Desktop-App- und mobilen Apps verwendet wird.
* [Die Botauthentifizierung](~/bots/how-to/authentication/add-authentication.md) beschreibt, wie Sie dem Teams-Bot die OAuth-Authentifizierung hinzufügen.
* [.Net oder C# oder](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth) [JavaScript oder Node.js](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/46.teams-auth) bietet #A0 v3 SDK-Beispiel.

## <a name="configure-the-identity-provider"></a>Konfigurieren des Identitätsanbieters

Konfigurieren Sie unabhängig vom Authentifizierungsfluss der App den Identitätsanbieter für die Kommunikation mit der Teams-App. Die meisten Beispiele und exemplarischen Vorgehensweisen befassen sich hauptsächlich mit der Verwendung von AAD als Identitätsanbieter. Die Konzepte gelten jedoch unabhängig vom Identitätsanbieter.

Weitere Informationen finden Sie unter [Konfigurieren eines Identitätsanbieters.](~/concepts/authentication/configure-identity-provider.md)
