---
title: Authentifizieren von App-Benutzern
description: Beschreibt die Authentifizierung in Teams und deren Verwendung in Ihren Apps
ms.topic: conceptual
keywords: Teams authentication OAuth SSO AAD
ms.openlocfilehash: 6ddcd8a9e847d9216b7e2dcc12733a6cd413b48e
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014292"
---
# <a name="authenticating-users-in-microsoft-teams"></a>Authentifizieren von Benutzern in Microsoft Teams

> [!Note]
> Die webbasierte Authentifizierung auf mobilen Clients erfordert Version 1.4.1 oder höher des JavaScript SDK für Teams.

Damit Ihre App auf Benutzerinformationen zugreifen kann, die durch Azure Active Directory geschützt sind, und auf Daten von anderen Diensten wie Facebook und Twitter zugreifen kann, muss Ihre App eine vertrauenswürdige Verbindung mit diesen Anbietern herstellen. Wenn Ihre App Microsoft Graph-APIs im Benutzerbereich verwenden muss, müssen Sie den Benutzer auch authentifizieren, um die entsprechenden Authentifizierungstoken abzurufen.

In Microsoft Teams gibt es zwei verschiedene Authentifizierungsflüsse, die Ihre App nutzen kann. Sie können einen herkömmlichen webbasierten [](~/tabs/how-to/create-tab-pages/content-page.md) Authentifizierungsfluss auf einer Inhaltsseite ausführen, die in eine Registerkarte, eine Konfigurationsseite oder ein Aufgabenmodul eingebettet ist. Wenn Ihre App einen Unterhaltungsbot enthält, können Sie den OAuthPrompt-Fluss (und optional den Tokendienst des Azure Bot Framework) verwenden, um einen Benutzer im Rahmen einer Unterhaltung zu authentifizieren.

## <a name="web-based-authentication-flow"></a>Webbasierter Authentifizierungsfluss

Sie müssen den webbasierten Authentifizierungsfluss [](~/tabs/what-are-tabs.md)für Registerkarten verwenden und können ihn mit [Unterhaltungsbots oder](~/bots/what-are-bots.md) [Messagingerweiterungen verwenden.](~/messaging-extensions/what-are-messaging-extensions.md) Sie verwenden das [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client) auf einer Webinhaltsseite, um die Authentifizierung zu aktivieren, und betten dann diese Inhaltsseite in eine Registerkarte, eine Konfigurationsseite oder ein Aufgabenmodul ein. Wenn Sie den webbasierten Authentifizierungsfluss mit einem Unterhaltungsbot verwenden möchten, müssen Sie ein Aufgabenmodul [mit einem Bot verwenden.](~/task-modules-and-cards/task-modules/task-modules-bots.md)

* [Der Authentifizierungsfluss auf Registerkarten](~/tabs/how-to/authentication/auth-flow-tab.md) beschreibt, wie die Registerkartenauthentifizierung in Teams funktioniert. Dies zeigt einen typischen webbasierten Authentifizierungsfluss, der für Registerkarten verwendet wird.
* [Azure AD authentication in tabs](~/tabs/how-to/authentication/auth-tab-AAD.md) describes how to connect to Azure Active Directory from within a tab in your app in Teams.
* [Die automatische Authentifizierung (Azure AD)](~/tabs/how-to/authentication/auth-silent-AAD.md) beschreibt, wie Anmelde-/Zustimmungsaufforderungen in Ihrer App mithilfe von Azure Active Directory reduziert werden.
* Webbasierte Authentifizierung in [dotnet/C# oder](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp) [JavaScript/Node.js](https://github.com/OfficeDev/microsoft-teams-sample-complete-node)

## <a name="the-oauthprompt-flow-for-conversational-bots"></a>Der OAuthPrompt-Fluss für Unterhaltungsbots

Das OAuthPrompt des Azure Bot Framework erleichtert die Authentifizierung für Apps, die unterhaltungsbasierte Bots verwenden. Sie können den Tokendienst von Azure Bot Framework nutzen, um auch beim Zwischenspeichern von Token zu helfen.

Weitere Informationen zur Verwendung von OAuthPrompt finden Sie unter:

* [Übersicht über den Ablauf der](~/bots/how-to/authentication/auth-flow-bot.md) Botauthentifizierung beschreibt, wie die Authentifizierung in einem Bot in Ihrer App in Teams funktioniert. Dies zeigt einen nicht webbasierten Authentifizierungsfluss, der für Bots in allen Versionen von Teams (Web, Desktop-App und mobile Apps) verwendet wird.
* [Botauthentifizierung](~/bots/how-to/authentication/add-authentication.md)
* Beispiel für #A0 (v3 SDK) in [dotnet/C#](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth) oder [JavaScript/Node.js](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/46.teams-auth)

## <a name="configure-your-identity-provider"></a>Konfigurieren des Identitätsanbieters

Unabhängig davon, welchen Authentifizierungsfluss Ihre App verwendet (möglicherweise verwenden Sie sogar beide), müssen Sie Ihren Identitätsanbieter für die Kommunikation mit Ihrer Teams-App konfigurieren. Die meisten Beispiele und exemplarischen Vorgehensweisen, die Sie hier finden, befassen sich hauptsächlich mit der Verwendung von Azure Active Directory als Identitätsanbieter. Die Konzepte gelten jedoch unabhängig davon, welchen Identitätsanbieter Sie verwenden.

Weitere Informationen finden Sie unter [Konfigurieren eines Identitätsanbieters](~/concepts/authentication/configure-identity-provider.md)
