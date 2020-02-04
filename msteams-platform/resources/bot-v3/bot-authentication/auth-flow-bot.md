---
title: Authentifizierungsablauf für Bots
description: Beschreibung des Authentifizierungs Flusses in Bots
keywords: Bots für Teams-Authentifizierungs Fluss
ms.date: 03/01/2018
ms.openlocfilehash: 5230a94b23f9042d9d7753b52467fba5b2fec89e
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674576"
---
# <a name="microsoft-teams-authentication-flow-for-bots"></a>Microsoft Teams-Authentifizierungs Fluss für Bots

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

OAuth 2,0 ist ein offener Standard für Authentifizierung und Autorisierung, der von Azure AD und vielen anderen Identitätsanbietern verwendet wird. Ein grundlegendes Verständnis von OAuth 2,0 ist eine Voraussetzung für die Verwendung von Authentifizierung in Microsoft Teams. [hier finden Sie eine gute Übersicht](https://aaronparecki.com/oauth-2-simplified/) , die einfacher zu befolgen ist als die [formale Spezifikation](https://oauth.net/2/). Authentifizierungs Fluss für Registerkarten und Bots sind ein wenig anders, da Registerkarten sehr ähnlich zu Websites sind, damit Sie OAuth 2,0 direkt verwenden können, und Bots sind nicht und müssen ein paar Dinge anders tun, aber die Kernkonzepte sind identisch.

Im GitHub Repo [Microsoft Teams-Authentifizierungs Beispiel](https://github.com/OfficeDev/microsoft-teams-sample-auth-node) wird ein Beispiel für den Authentifizierungsablauf für Bots verwendet, die den Knoten mit dem [OAuth 2,0-Autorisierungscode Grant-Typ](https://oauth.net/2/grant-types/authorization-code/)verwenden.

![Robot-Authentifizierungs-Sequenzdiagramm](~/assets/images/authentication/bot_auth_sequence_diagram.png)

1. Der Benutzer sendet eine Nachricht an den bot.
2. Der bot bestimmt, ob der Benutzer sich anmelden muss.
    * In diesem Beispiel speichert der bot das Zugriffstoken in seinem Benutzerdatenspeicher. Der Benutzer wird aufgefordert, sich anzumelden, wenn er kein validiertes Token für den ausgewählten Identitätsanbieter besitzt. ([Code anzeigen](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/utils/AuthenticationUtils.ts#L58-L76))
3. Der bot konstruiert die URL der Startseite des Authentifizierungs Flusses und sendet eine Karte an den Benutzer mit einer `signin` Aktion. ([Code anzeigen](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/dialogs/BaseIdentityDialog.ts#L160-L190))
    * Wie bei anderen Anwendungs Authentifizierungs Abläufen in Microsoft Teams muss sich die Startseite in einer Domäne befinden `validDomains` , die sich in Ihrer Liste befindet, und in derselben Domäne wie die Umleitungsseite nach der Anmeldung.
    * **Wichtig**: der OAuth 2,0-Autorisierungscode Grant-Fluss `state` Ruft für einen Parameter in der Authentifizierungsanforderung, die ein eindeutiges Sitzungstoken enthält, um einen [Fälschungs Angriff mit standortübergreifender Anforderung](https://en.wikipedia.org/wiki/Cross-site_request_forgery)zu verhindern. Im Beispiel wird eine zufällig generierte GUID verwendet.
4. Wenn der Benutzer auf die Schaltfläche " *SignIn* " klickt, öffnet Microsoft Teams ein Popupfenster und navigiert es zur Startseite.
5. Auf der Startseite wird der Benutzer an den `authorize` Endpunkt des Identitätsanbieters umgeleitet. ([Code anzeigen](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/public/html/auth-start.html#L51-L56))
6. Der Benutzer meldet sich auf der Website des Anbieters an und erteilt Zugriff auf den bot.
7. Der Anbieter führt den Benutzer mit einem Autorisierungscode zur OAuth-Umleitungsseite des bot.
8. Der bot löst den Autorisierungscode für ein Zugriffstoken aus und ordnet das Token **vorläufig** dem Benutzer zu, der den Anmelde Fluss initiiert hat. Im folgenden wird dies als *provisorisches Token*bezeichnet.
    * Im Beispiel ordnet der bot den Wert des `state` Parameters der ID des Benutzers zu, der den Anmeldeprozess initiiert hat, sodass er ihn später mit dem `state` vom Identitätsanbieter zurückgegebenen Wert abgleichen kann. ([Code anzeigen](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/AuthBot.ts#L70-L99))
    * **Wichtig**: der bot speichert das Token, das vom Identitätsanbieter empfangen wird, und ordnet ihn einem bestimmten Benutzer zu, wird jedoch als "ausstehende Validierung" gekennzeichnet. Das vorläufige Token kann noch nicht verwendet werden: Es muss weiter validiert werden: 
      1. **Überprüfen Sie, was vom Identitätsanbieter empfangen wurde.** Der Wert des `state` Parameters muss gegenüber dem, was zuvor gespeichert wurde, bestätigt werden. 
      1. **Überprüfen Sie, was von Microsoft Teams empfangen wurde.** Es wird eine [zweistufige Authentifizierungs](https://en.wikipedia.org/wiki/Man-in-the-middle_attack) Überprüfung durchgeführt, um sicherzustellen, dass der Benutzer, der den bot mit dem Identitätsanbieter autorisiert hat, derselbe Benutzer ist, der mit dem bot chattet. Dies schützt vor [man-in-the-Middle](https://en.wikipedia.org/wiki/Man-in-the-middle_attack) -und [Phishing](https://en.wikipedia.org/wiki/Phishing) -Angriffen. Der Bot generiert einen Überprüfungscode und speichert ihn, der dem Benutzer zugeordnet ist. Der Überprüfungscode wird automatisch von Microsoft Teams gesendet, wie weiter unten in den Schritten 9 und 10 beschrieben. ([Code anzeigen](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/AuthBot.ts#L100-L113))
9. Der OAuth-Rückruf rendert eine Seite, `notifySuccess("<verification code>")`die ruft. ([Code anzeigen](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/master/src/views/oauth-callback-success.hbs))
10. Teams schließt das Popup und sendet das `<verification code>` an den `notifySuccess()` bot zurückgesendete. Der bot erhält eine [Invoke](/bot-framework/dotnet/bot-builder-dotnet-activities#invoke) -Nachricht `name = signin/verifyState`mit.
11. Der bot überprüft den eingehenden Verifizierungscode mit dem Bestätigungscode, der mit dem provisorischen Token des Benutzers gespeichert ist. ([Code anzeigen](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/dialogs/BaseIdentityDialog.ts#L127-L140))
12. Wenn Sie übereinstimmen, markiert der bot das Token als validiert und kann verwendet werden. Andernfalls schlägt der Authentifizierungs Fluss fehl, und der bot löscht das provisorische Token.

> [!Note]
> Wenn bei der Authentifizierung auf mobilen Geräten Probleme auftreten, stellen Sie sicher, dass Ihr JavaScript-SDK auf Version 1.4.1 oder höher aktualisiert wird.

## <a name="samples"></a>Beispiele

Beispielcode zum Anzeigen des bot-Authentifizierungsprozesses finden Sie unter:

* [Beispiel für Microsoft Teams-bot-Authentifizierung (Knoten)](https://github.com/OfficeDev/microsoft-teams-sample-auth-node)

## <a name="more-details"></a>Weitere Details

Ausführliche Exemplarische Vorgehensweisen zur Implementierung von bot-Authentifizierung für Azure Active Directory finden Sie unter:

* [Authentifizieren eines Benutzers in einem Microsoft Teams-bot](~/resources/bot-v3/bot-authentication/auth-bot-AAD.md)
