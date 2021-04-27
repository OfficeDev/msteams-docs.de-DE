---
title: Authentifizierungsfluss für Bots
description: Beschreibt den Authentifizierungsfluss in Bots
keywords: Teams-Authentifizierungsflussbots
localization_priority: Normal
ms.topic: conceptual
ms.date: 03/01/2018
ms.openlocfilehash: fe7e528be98a0b58334535952327b6026b30a87d
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019804"
---
# <a name="microsoft-teams-authentication-flow-for-bots"></a>Microsoft Teams-Authentifizierungsfluss für Bots

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

OAuth 2.0 ist ein offener Standard für die Authentifizierung und Autorisierung, der von Azure AD und vielen anderen Identitätsanbietern verwendet wird. Ein grundlegendes Verständnis von OAuth 2.0 ist eine Voraussetzung für die Arbeit mit der Authentifizierung in Teams. [Hier finden Sie eine gute Übersicht,](https://aaronparecki.com/oauth-2-simplified/) die einfacher zu befolgen ist als die [formale Spezifikation.](https://oauth.net/2/) Der Authentifizierungsfluss für Registerkarten und Bots ist etwas anders, da Registerkarten Websites sehr ähnlich sind, sodass sie OAuth 2.0 direkt verwenden können, und Bots sind und müssen einiges anders tun, aber die Kernkonzepte sind identisch.

Im Beispiel für die [Microsoft Teams-Authentifizierung](https://github.com/OfficeDev/microsoft-teams-sample-auth-node) des GitHub-Repositorys finden Sie ein Beispiel, das den Authentifizierungsfluss für Bots mithilfe von Node mithilfe des OAuth 2.0-Autorisierungscode-Grant-Typs [veranschaulicht.](https://oauth.net/2/grant-types/authorization-code/)

![Bot-Authentifizierungssequenzdiagramm](~/assets/images/authentication/bot_auth_sequence_diagram.png)

1. Der Benutzer sendet eine Nachricht an den Bot.
2. Der Bot bestimmt, ob sich der Benutzer anmelden muss.
    * In diesem Beispiel speichert der Bot das Zugriffstoken im Benutzerdatenspeicher. Er fordert den Benutzer auf, sich zu melden, wenn er kein überprüftes Token für den ausgewählten Identitätsanbieter hat. ([View code](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/utils/AuthenticationUtils.ts#L58-L76))
3. Der Bot erstellt die URL zur Startseite des Authentifizierungsflusses und sendet eine Karte mit einer Aktion an den `signin` Benutzer. ([View code](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/dialogs/BaseIdentityDialog.ts#L160-L190))
    * Wie andere Anwendungsauthentifizierungsflüsse in Teams muss sich die Startseite in einer Domäne befinden, die sich in Ihrer Liste und in derselben Domäne wie die Umleitungsseite nach der Anmeldung `validDomains` befinden.
    * **WICHTIG**: Der OAuth 2.0-Autorisierungscode-Erteilungsfluss ruft einen Parameter in der Authentifizierungsanforderung auf, der ein eindeutiges Sitzungstoken enthält, um einen standortübergreifenden Anforderungsfälschungsangriff `state` [zu verhindern.](https://en.wikipedia.org/wiki/Cross-site_request_forgery) Das Beispiel verwendet eine zufällig generierte GUID.
4. Wenn der Benutzer auf  die Anmeldeschaltfläche klickt, öffnet Teams ein Popupfenster und navigiert es zur Startseite.
5. Die Startseite leitet den Benutzer an den Endpunkt des `authorize` Identitätsanbieters um. ([View code](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/public/html/auth-start.html#L51-L56))
6. Auf der Website des Anbieters meldet sich der Benutzer an und gewährt Zugriff auf den Bot.
7. Der Anbieter führt den Benutzer mit einem Autorisierungscode zur OAuth-Umleitungsseite des Bots.
8. Der Bot löst den Autorisierungscode für  ein Zugriffstoken ein und ordnet das Token vorläufig dem Benutzer zu, der den Anmeldefluss initiiert hat. Nachfolgend wird dies als *vorläufiges Token bezeichnet.*
    * Im Beispiel ordnet der Bot den Wert des Parameters der ID des Benutzers zu, der den Anmeldevorgang initiiert hat, damit er später mit dem vom Identitätsanbieter zurückgegebenen Wert `state` `state` übereinstimmen kann. ([View code](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/AuthBot.ts#L70-L99))
    * **WICHTIG:** Der Bot speichert das Token, das er vom Identitätsanbieter erhält, und ordnet es einem bestimmten Benutzer zu, wird jedoch als "ausstehende Überprüfung" gekennzeichnet. Das vorläufige Token kann noch nicht verwendet werden: Es muss weiter überprüft werden: 
      1. **Überprüfen Sie, was vom Identitätsanbieter empfangen wird.** Der Wert des Parameters muss mit dem zuvor `state` gespeicherten Wert bestätigt werden. 
      1. **Überprüfen Sie, was von Teams empfangen wird.** Eine [zweistufige](https://en.wikipedia.org/wiki/Man-in-the-middle_attack) Authentifizierungsüberprüfung wird durchgeführt, um sicherzustellen, dass der Benutzer, der den Bot mit dem Identitätsanbieter autorisiert hat, derselbe Benutzer ist, der mit dem Bot chatt. Dadurch wird vor [Man-in-the-Middle- und](https://en.wikipedia.org/wiki/Man-in-the-middle_attack) [Phishingangriffen gewehrt.](https://en.wikipedia.org/wiki/Phishing) Der Bot generiert einen Überprüfungscode und speichert ihn, der dem Benutzer zugeordnet ist. Der Überprüfungscode wird automatisch von Teams gesendet, wie unten in den Schritten 9 und 10 beschrieben. ([View code](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/AuthBot.ts#L100-L113))
9. Der OAuth-Rückruf rendert eine Seite, die `notifySuccess("<verification code>")` aufruft. ([View code](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/master/src/views/oauth-callback-success.hbs))
10. Teams schließt das Popup und sendet das `<verification code>` gesendete an `notifySuccess()` zurück an den Bot. Der Bot empfängt eine [Aufrufnachricht](/bot-framework/dotnet/bot-builder-dotnet-activities#invoke) mit `name = signin/verifyState` .
11. Der Bot überprüft den eingehenden Überprüfungscode mit dem Überprüfungscode, der mit dem vorläufigen Token des Benutzers gespeichert ist. ([View code](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/dialogs/BaseIdentityDialog.ts#L127-L140))
12. Wenn sie übereinstimmen, markiert der Bot das Token als überprüft und einsatzbereit. Andernfalls schlägt der Authentifizierungsfluss fehl, und der Bot löscht das vorläufige Token.

> [!Note]
> Wenn Probleme mit der Authentifizierung auf Mobilgeräten auftreten, stellen Sie sicher, dass Ihr Javascript SDK auf Version 1.4.1 oder höher aktualisiert wird.

## <a name="samples"></a>Beispiele

Beispielcode zum Botauthentifizierungsprozess finden Sie unter:

* [Microsoft Teams-Bot-Authentifizierungsbeispiel (Node)](https://github.com/OfficeDev/microsoft-teams-sample-auth-node)

## <a name="more-details"></a>Weitere Details

Ausführliche implementierungs exemplarische Vorgehensweisen für die Botauthentifizierung für Azure Active Directory finden Sie unter:

* [Authentifizieren eines Benutzers in einem Microsoft Teams-Bot](~/resources/bot-v3/bot-authentication/auth-bot-AAD.md)
