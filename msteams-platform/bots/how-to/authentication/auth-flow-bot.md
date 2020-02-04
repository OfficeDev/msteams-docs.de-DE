---
title: Authentifizierungsablauf für Bots
description: Beschreibung des Authentifizierungs Flusses in Bots
keywords: Bots für Teams-Authentifizierungs Fluss
ms.date: 03/01/2018
ms.openlocfilehash: 40f34a3b51349cc1d11f819a92b479a92ebac149
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674490"
---
# <a name="microsoft-teams-authentication-flow-for-bots"></a>Microsoft Teams-Authentifizierungs Fluss für Bots

OAuth 2,0 ist ein offener Standard für Authentifizierung und Autorisierung, der von Azure Active Directory (Azure AD) und vielen anderen Identitätsanbietern verwendet wird. Ein grundlegendes Verständnis von OAuth 2,0 ist eine Voraussetzung für die Verwendung von Authentifizierung in Microsoft Teams. [hier finden Sie eine gute Übersicht](https://aaronparecki.com/oauth-2-simplified/) , die einfacher zu befolgen ist als die [formale Spezifikation](https://oauth.net/2/). Der Authentifizierungs Fluss für Registerkarten und Bots ist ein wenig anders: Registerkarten ähneln Websites sehr ähnlich, sodass Sie OAuth 2,0 direkt verwenden können, während Bots nicht unterschiedlich sind und ein paar andere Dinge tun müssen – die Kernkonzepte sind jedoch identisch.

Ein Beispiel, das den Authentifizierungsablauf für Bots mit Node. js und dem [Grant-Typ OAuth 2,0 Authorization Code](https://oauth.net/2/grant-types/authorization-code/)veranschaulicht, finden Sie im GitHub Repo [Microsoft Teams-Authentifizierungs Beispiel](https://github.com/OfficeDev/microsoft-teams-sample-auth-node) .

![Robot-Authentifizierungs-Sequenzdiagramm](../../../assets/images/authentication/bot_auth_sequence_diagram.png)

1. Der Benutzer sendet eine Nachricht an den bot.
2. Der bot bestimmt, ob der Benutzer sich anmelden muss.
    * In diesem Beispiel speichert der bot das Zugriffstoken in seinem Benutzerdatenspeicher. Der Benutzer wird aufgefordert, sich anzumelden, wenn er kein validiertes Token für den ausgewählten Identitätsanbieter besitzt. ([Code anzeigen](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/utils/AuthenticationUtils.ts#L58-L76))
3. Der bot konstruiert die URL der Startseite des Authentifizierungs Flusses und sendet eine Karte an den Benutzer mit einer `signin` Aktion. ([Code anzeigen](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/dialogs/BaseIdentityDialog.ts#L160-L190))
    * Wie bei anderen Anwendungs Authentifizierungs Bewegungen in Microsoft Teams muss sich die Startseite in einer Domäne befinden, `validDomains` die sich in Ihrer Liste befindet, und in derselben Domäne wie die Umleitungsseite nach der Anmeldung.
    * **Wichtig**: der OAuth 2,0-Autorisierungscode Grant-Fluss `state` Ruft für einen Parameter in der Authentifizierungsanforderung, die ein eindeutiges Sitzungstoken enthält, um einen [Fälschungs Angriff mit standortübergreifender Anforderung](https://en.wikipedia.org/wiki/Cross-site_request_forgery)zu verhindern. Im Beispiel wird eine zufällig generierte GUID verwendet.
4. Wenn der Benutzer die Schaltfläche *SignIn* auswählt, öffnet Microsoft Teams ein Popupfenster und navigiert zur Startseite.
5. Auf der Startseite wird der Benutzer an den `authorize` Endpunkt des Identitätsanbieters umgeleitet. ([Code anzeigen](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/public/html/auth-start.html#L51-L56))
6. Der Benutzer meldet sich auf der Website des Anbieters an und erteilt Zugriff auf den bot.
7. Der Anbieter führt den Benutzer zur OAuth-Umleitungsseite des bot mit einem Autorisierungscode.
8. Der bot löst den Autorisierungscode für ein Zugriffstoken aus und ordnet das Token **vorläufig** dem Benutzer zu, der den Anmelde Fluss initiiert hat. Im folgenden wird dies als *provisorisches Token*bezeichnet.
    * Im Beispiel ordnet der bot den Wert des `state` Parameters der ID des Benutzers zu, der den Anmeldeprozess initiiert hat, sodass er ihn später mit dem `state` vom Identitätsanbieter zurückgegebenen Wert abgleichen kann. ([Code anzeigen](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/AuthBot.ts#L70-L99))
    * **Wichtig**: der bot speichert das Token, das vom Identitätsanbieter empfangen wird, und ordnet ihn einem bestimmten Benutzer zu, wird jedoch als "ausstehende Validierung" gekennzeichnet. Das vorläufige Token kann noch nicht verwendet werden; Sie muss weiter validiert werden:
      1. **Überprüfen Sie, was vom Identitätsanbieter empfangen wurde.** Der Wert des `state` Parameters muss gegenüber dem, was zuvor gespeichert wurde, bestätigt werden. 
      1. **Überprüfen Sie, was von Microsoft Teams empfangen wurde.** Es wird eine [zweistufige Authentifizierungs](https://en.wikipedia.org/wiki/Man-in-the-middle_attack) Überprüfung durchgeführt, um sicherzustellen, dass der Benutzer, der den bot mit dem Identitätsanbieter autorisiert hat, derselbe Benutzer ist, der mit dem bot chattet. Dies schützt vor [man-in-the-Middle](https://en.wikipedia.org/wiki/Man-in-the-middle_attack) -und [Phishing](https://en.wikipedia.org/wiki/Phishing) -Angriffen. Der Bot generiert einen Überprüfungscode und speichert ihn, der dem Benutzer zugeordnet ist. Der Überprüfungscode wird automatisch von Microsoft Teams gesendet, wie unten beschrieben. ([Code anzeigen](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/AuthBot.ts#L100-L113))
9. Der OAuth-Rückruf rendert eine Seite, `notifySuccess("<verification code>")`die ruft. ([Code anzeigen](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/master/src/views/oauth-callback-success.hbs))
10. Teams schließt das Popupfenster und sendet den `<verification code>` an den bot gesendeten `notifySuccess()` zurück. Der bot erhält eine [Invoke](/bot-framework/dotnet/bot-builder-dotnet-activities#invoke) -Nachricht `name = signin/verifyState`mit.
11. Der bot überprüft den eingehenden Verifizierungscode mit dem Bestätigungscode, der mit dem provisorischen Token des Benutzers gespeichert ist. ([Code anzeigen](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/dialogs/BaseIdentityDialog.ts#L127-L140))
12. Wenn Sie übereinstimmen, markiert der bot das Token als validiert und kann verwendet werden. Andernfalls schlägt der Authentifizierungs Fluss fehl, und der bot löscht das provisorische Token.

> [!NOTE]
> Wenn bei der Authentifizierung auf mobilen Geräten Probleme auftreten, stellen Sie sicher, dass Ihr JavaScript-SDK auf Version 1.4.1 oder höher aktualisiert wird.

## <a name="samples"></a>Beispiele

Beispielcode zum Anzeigen des bot-Authentifizierungsprozesses finden Sie unter:

* [Beispiel für Microsoft Teams-bot-Authentifizierung (Node. js)](https://github.com/OfficeDev/microsoft-teams-sample-auth-node)

## <a name="more-details"></a>Weitere Details

Ausführliche Exemplarische Vorgehensweisen zur Implementierung von bot-Authentifizierungs Azure AD finden Sie unter:

* [Hinzufügen von Authentifizierung zu ihren Teams-bot](add-authentication.md)
