---
title: Authentifizieren eines Benutzers in Microsoft Teams
description: Beschreibung der Authentifizierung in Microsoft Teams und ihrer Verwendung in ihren apps
keywords: Teams-Authentifizierung OAuth SSO-Aad
ms.openlocfilehash: d3ae57d9937c6794fb743b44ca8210a5afd181bf
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674200"
---
# <a name="authentication-in-teams"></a>Authentifizierung in Microsoft Teams

> [!Note]
> Die webbasierte Authentifizierung auf mobilen Clients erfordert Version 1.4.1 oder höher des Teams-JavaScript-SDK.

Damit Ihre APP auf Benutzerinformationen zugreifen kann, die durch Azure Active Directory geschützt sind, sowie auf Daten anderer Dienste wie Facebook und Twitter zugreifen, muss Ihre APP eine vertrauenswürdige Verbindung mit diesen Anbietern herstellen. Wenn Ihre APP Microsoft Graph-APIs im Benutzerbereich verwenden muss, müssen Sie den Benutzer auch authentifizieren, um die entsprechenden Authentifizierungstoken abzurufen.

In Microsoft Teams gibt es zwei verschiedene Authentifizierungs Flüsse, die Ihre APP nutzen kann. Sie können einen herkömmlichen webbasierten Authentifizierungs Fluss auf einer [Inhaltsseite](~/tabs/how-to/create-tab-pages/content-page.md) ausführen, die in einer Registerkarte, einer Konfigurationsseite oder einem Aufgabenmodul eingebettet ist. Wenn Ihre APP einen Unterhaltungs-bot enthält, können Sie den OAuthPrompt-Fluss (und optional den Tokendienst des Azure bot-Frameworks) verwenden, um einen Benutzer als Teil einer Unterhaltung zu authentifizieren.

## <a name="web-based-authentication-flow"></a>Webbasierter Authentifizierungs Fluss

Sie müssen den webbasierten Authentifizierungs Fluss für [Registerkarten](~/tabs/what-are-tabs.md)verwenden, und Sie können ihn mit [Unterhaltungs Bots](~/bots/what-are-bots.md) oder [Messaging-Erweiterungen](~/messaging-extensions/what-are-messaging-extensions.md)verwenden. Sie verwenden das [Microsoft Teams-JavaScript-Client-SDK](/javascript/api/overview/msteams-client) auf einer Webinhalts Seite, um die Authentifizierung zu aktivieren und dann diese Inhaltsseite in eine Registerkarte, eine Konfigurationsseite oder ein Aufgabenmodul einzubetten. Wenn Sie den webbasierten Authentifizierungs Fluss mit einem Unterhaltungs-bot verwenden möchten, müssen Sie [ein Aufgabenmodul mit einem bot verwenden](~/task-modules-and-cards/task-modules/task-modules-bots.md).

* [Authentifizierungs Fluss in Registerkarten](~/tabs/how-to/authentication/auth-flow-tab.md) beschreibt die Funktionsweise der Tab-Authentifizierung in Microsoft Teams. Dies zeigt einen typischen webbasierten Authentifizierungs Fluss, der für Registerkarten verwendet wird.
* [In Registerkarten für Azure AD Authentifizierung](~/tabs/how-to/authentication/auth-tab-AAD.md) wird beschrieben, wie Sie eine Verbindung mit Azure Active Directory innerhalb einer Registerkarte in ihrer app in Microsoft Teams herstellen.
* In der [automatischen Authentifizierung (Azure AD)](~/tabs/how-to/authentication/auth-silent-AAD.md) wird beschrieben, wie Sie die Anmelde-und Zustimmungs Ansagen in ihrer App mithilfe von Azure Active Directory reduzieren.
* Webbasierte Authentifizierung in [dotnet/C#](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp) oder [JavaScript/Node. js](https://github.com/OfficeDev/microsoft-teams-sample-complete-node)

## <a name="the-oauthprompt-flow-for-conversational-bots"></a>Der OAuthPrompt-Ablauf für Unterhaltungs Bots

Die OAuthPrompt des Azure bot-Frameworks erleichtert die Authentifizierung für apps mit Unterhaltungs Bots. Sie können den Tokendienst des Azure bot-Frameworks nutzen, um auch bei der Token-Zwischenspeicherung behilflich zu sein.

Weitere Informationen zur Verwendung des OAuthPrompt finden Sie unter:

* [Übersicht über den bot-Authentifizierungs Fluss](~/bots/how-to/authentication/auth-flow-bot.md) beschreibt die Funktionsweise der Authentifizierung innerhalb eines bot in ihrer app in Microsoft Teams. Dies zeigt einen nicht webbasierten Authentifizierungs Fluss, der für Bots in allen Versionen von Teams verwendet wird (Webanwendung, Desktop-App und Mobile Apps)
* [Bot-Authentifizierung](~/bots/how-to/authentication/add-authentication.md)
* Beispiel für bot-Authentifizierung (V3 SDK) in [dotnet/C#](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth) oder [JavaScript/Node. js](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/46.teams-auth)

## <a name="configure-your-identity-provider"></a>Konfigurieren Ihres Identitätsanbieters

Unabhängig davon, welchen Authentifizierungs Fluss Ihre APP verwendet (Sie verwenden möglicherweise sogar beides), müssen Sie Ihren Identitätsanbieter so konfigurieren, dass er mit ihrer Teams-App kommuniziert. Die Mehrzahl der Beispiele und exemplarischen Vorgehensweisen, die Sie hier finden, befassen sich hauptsächlich mit der Verwendung von Azure Active Directory als Identitätsanbieter. Die Konzepte gelten jedoch unabhängig davon, welchen Identitätsanbieter Sie verwenden.

Weitere Informationen finden Sie unter [Konfigurieren eines Identitätsanbieters](~/concepts/authentication/configure-identity-provider.md) .
