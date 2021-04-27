---
title: Authentifizieren von App-Benutzern
description: Beschreibt die Authentifizierung in Teams und deren Verwendung in den Apps
ms.topic: conceptual
localization_priority: Normal
keywords: Teams-Authentifizierung OAuth SSO AAD
ms.openlocfilehash: 23e0e500ee041afa191e9381b6f69b4c3881c391
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019972"
---
# <a name="authenticate-users-in-microsoft-teams"></a>Authentifizieren von Benutzern in Microsoft Teams

> [!NOTE]
> Die webbasierte Authentifizierung auf mobilen Clients erfordert Version 1.4.1 oder höher des Microsoft Teams JavaScript SDK.

Um auf Benutzerinformationen zu zugreifen, die durch Azure Active Directory (AAD) geschützt sind, und um auf Daten von Diensten wie Facebook und Twitter zu zugreifen, richtet die App eine vertrauenswürdige Verbindung mit diesen Anbietern ein. Wenn die App Microsoft Graph-APIs im Benutzerbereich verwendet, authentifizieren Sie den Benutzer, um die entsprechenden Authentifizierungstoken abzurufen.

In Teams gibt es zwei verschiedene Authentifizierungsflüsse für die App. Führen Sie einen herkömmlichen webbasierten Authentifizierungsfluss in einer Inhaltsseite aus, die in eine Registerkarte, eine Konfigurationsseite oder ein Aufgabenmodul eingebettet ist. [](~/tabs/how-to/create-tab-pages/content-page.md) Wenn die App einen Unterhaltungs-Bot enthält, verwenden Sie den OAuthPrompt-Flow und optional den Tokendienst von Azure Bot Framework, um einen Benutzer als Teil einer Unterhaltung zu authentifizieren.

## <a name="web-based-authentication-flow"></a>Webbasierter Authentifizierungsflow

Verwenden Sie den webbasierten Authentifizierungsfluss für [Registerkarten,](~/tabs/what-are-tabs.md) und wählen Sie ihn mit [Unterhaltungsbots](~/bots/what-are-bots.md) oder [Messagingerweiterungen aus.](~/messaging-extensions/what-are-messaging-extensions.md) Verwenden Sie [das Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client) auf einer Webinhaltsseite, um die Authentifizierung zu aktivieren. Nachdem Sie die Authentifizierung aktiviert haben, betten Sie die Inhaltsseite in eine Registerkarte, eine Konfigurationsseite oder ein Aufgabenmodul ein. Weitere Informationen zum webbasierten Authentifizierungsfluss finden Sie unter:

* [Add authentication to the Teams bot](~/bots/how-to/authentication/add-authentication.md) describes how to use web-based authentication flow with a conversational bot.
* [Der Authentifizierungsfluss in Registerkarten](~/tabs/how-to/authentication/auth-flow-tab.md) beschreibt die Funktionsweise der Registerkartenauthentifizierung in Teams. Dies zeigt einen typischen webbasierten Authentifizierungsfluss, der für Registerkarten verwendet wird.
* [Die AAD-Authentifizierung in Registerkarten](~/tabs/how-to/authentication/auth-tab-AAD.md) beschreibt, wie Sie über eine Registerkarte in der App in Teams eine Verbindung mit AAD herstellen.
* [AAD für](~/tabs/how-to/authentication/auth-silent-AAD.md) automatische Authentifizierung beschreibt, wie Anmelde- oder Zustimmungsaufforderungen in der App mithilfe von AAD reduziert werden.
* [.Net oder C#](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp) oder [JavaScript oder Node.js](https://github.com/OfficeDev/microsoft-teams-sample-complete-node) enthält Beispiele für die webbasierte Authentifizierung.

## <a name="the-oauthprompt-flow-for-conversational-bots"></a>Der OAuthPrompt-Fluss für Unterhaltungsbots

Der OAuthPrompt-Flow von Azure Bot Framework erleichtert die Authentifizierung für Apps, die Unterhaltungs-Bots verwenden. Verwenden Sie den Tokendienst von Azure Bot Framework, um die Tokenzwischenspeicherung zu unterstützen.

Weitere Informationen zur Verwendung von OAuthPrompt finden Sie unter:

* [Übersicht über den Botauthentifizierungsfluss](~/bots/how-to/authentication/auth-flow-bot.md) beschreibt, wie die Authentifizierung innerhalb eines Bots in der App in Teams funktioniert. Dies zeigt einen nicht webbasierten Authentifizierungsfluss, der für Bots in Teams Web, Desktop-App und mobilen Apps verwendet wird.
* [Die Botauthentifizierung](~/bots/how-to/authentication/add-authentication.md) beschreibt, wie Sie dem Teams-Bot die OAuth-Authentifizierung hinzufügen.

## <a name="code-sample"></a>Codebeispiel

bietet Bot-Authentifizierung v3 SDK-Beispiel.

| **Beispielname** | **Beschreibung** | **.NET** | **Node.js** | **Python** |
|---------------|------------|------------|-------------|---------------|
| Bot-Authentifizierung | In diesem Beispiel wird gezeigt, wie Sie mit der Authentifizierung in einem Bot für Microsoft Teams beginnen. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/46.teams-auth) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/46.teams-auth) |

## <a name="configure-the-identity-provider"></a>Konfigurieren des Identitätsanbieters

Konfigurieren Sie unabhängig vom Authentifizierungsfluss der App den Identitätsanbieter für die Kommunikation mit der Teams-App. Die meisten Beispiele und exemplarischen Vorgehensweisen befassen sich hauptsächlich mit der Verwendung von AAD als Identitätsanbieter. Die Konzepte gelten jedoch unabhängig vom Identitätsanbieter.

Weitere Informationen finden Sie unter [Konfigurieren eines Identitätsanbieters](~/concepts/authentication/configure-identity-provider.md).
