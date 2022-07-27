---
title: Authentifizierungsfluss für Bots
description: Beschreibt den Authentifizierungsfluss in Bots
keywords: Teams-Authentifizierungsfluss-Bots
localization_priority: Normal
ms.topic: conceptual
ms.date: 03/01/2018
ms.openlocfilehash: e3bc5395a6a95272901076ec8bf51dc2ad57dfd2
ms.sourcegitcommit: 1cda2fd3498a76c09e31ed7fd88175414ad428f7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2022
ms.locfileid: "67035331"
---
# <a name="microsoft-teams-authentication-flow-for-bots"></a>Microsoft Teams-Authentifizierungsfluss für Bots

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

OAuth 2.0 ist ein offener Standard für die Authentifizierung und Autorisierung, der von Azure AD und vielen anderen Identitätsanbietern verwendet wird. Ein grundlegendes Verständnis von OAuth 2.0 ist eine Voraussetzung für die Arbeit mit der Authentifizierung in Teams. [Hier ist eine gute Übersicht](https://aaronparecki.com/oauth-2-simplified/) , die einfacher zu befolgen ist als die [formale Spezifikation](https://oauth.net/2/). Der Authentifizierungsfluss für Registerkarten und Bots unterscheidet sich. Registerkarten ähneln Websites, sodass sie OAuth 2.0 direkt verwenden können, und Bots sind nicht und müssen ein paar Dinge anders ausführen, aber die Kernkonzepte sind identisch.

Ein Beispiel für den Authentifizierungsfluss für Bots, die Node mithilfe des [OAuth 2.0-Autorisierungscodegenehmigungstyps](https://oauth.net/2/grant-types/authorization-code/) verwenden, finden Sie im GitHub-Repository-Microsoft [Teams-Authentifizierungsbeispiel](https://github.com/OfficeDev/microsoft-teams-sample-auth-node).

![Bot-Authentifizierungssequenzdiagramm](~/assets/images/authentication/bot_auth_sequence_diagram.png)

1. Der Benutzer sendet eine Nachricht an den Bot.
2. Der Bot bestimmt, ob sich der Benutzer anmelden muss.
    * In diesem Beispiel speichert der Bot das Zugriffstoken im Benutzerdatenspeicher. Der Benutzer wird aufgefordert, sich anzumelden, wenn er kein überprüftes Token für den ausgewählten Identitätsanbieter hat. ([Code anzeigen](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/utils/AuthenticationUtils.ts#L58-L76))
3. Der Bot erstellt die URL zur Startseite des Authentifizierungsflusses und sendet dem Benutzer eine Karte mit einer `signin` Aktion. ([Code anzeigen](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/dialogs/BaseIdentityDialog.ts#L160-L190))
    * Wie andere Anwendungsauthentifizierungsflüsse in Teams muss sich die Startseite in einer Domäne befinden, die sich in Ihrer `validDomains` Liste befindet, und sich in derselben Domäne wie die Umleitungsseite nach der Anmeldung befinden.
    * **WICHTIG**: Der OAuth 2.0-Autorisierungscode-Genehmigungsfluss ruft einen `state` Parameter in der Authentifizierungsanforderung auf, der ein eindeutiges Sitzungstoken enthält, um einen [websiteübergreifenden Fälschungsangriff von Anforderungen](https://en.wikipedia.org/wiki/Cross-site_request_forgery) zu verhindern. Im Beispiel wird eine zufällig generierte GUID verwendet.
4. Wenn der Benutzer die *Anmeldeschaltfläche* auswählt, öffnet Teams ein Popupfenster und navigiert es zur Startseite.
5. Die Startseite leitet den Benutzer zum Endpunkt des Identitätsanbieters `authorize` um. ([Code anzeigen](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/public/html/auth-start.html#L51-L56))
6. Auf der Website des Anbieters meldet sich der Benutzer an und gewährt Zugriff auf den Bot.
7. Der Anbieter führt den Benutzer mit einem Autorisierungscode zur OAuth-Umleitungsseite des Bots.
8. Der Bot löst den Autorisierungscode für ein Zugriffstoken ein und ordnet das Token **vorläufig** dem Benutzer zu, der den Anmeldefluss initiiert hat. Unten wird dies als *vorläufiges Token* bezeichnet.
    * In dem Beispiel ordnet der Bot den Wert des `state` Parameters der ID des Benutzers zu, der den Anmeldevorgang initiiert hat, sodass er ihn später mit dem `state` vom Identitätsanbieter zurückgegebenen Wert abgleichen kann. ([Code anzeigen](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/AuthBot.ts#L70-L99))
    * **WICHTIG**: Der Bot speichert das Token, das er vom Identitätsanbieter empfängt, und ordnet es einem bestimmten Benutzer zu, ist aber als "ausstehende Überprüfung" gekennzeichnet. Das vorläufige Token kann noch nicht verwendet werden: Es muss weiter überprüft werden:
      1. **Überprüfen Sie, was vom Identitätsanbieter empfangen wird.** Der Wert des Parameters muss anhand des `state` zuvor gespeicherten Parameters bestätigt werden.
      1. **Überprüfen Sie, was von Teams empfangen wird.** Es wird eine [zweistufige Authentifizierungsüberprüfung](https://en.wikipedia.org/wiki/Man-in-the-middle_attack) durchgeführt, um sicherzustellen, dass der Benutzer, der den Bot mit dem Identitätsanbieter autorisiert hat, derselbe Benutzer ist, der mit dem Bot chatt. Diese Überprüfung schützt vor [Man-in-the-Middle-](https://en.wikipedia.org/wiki/Man-in-the-middle_attack) und [Phishing-Angriffen](https://en.wikipedia.org/wiki/Phishing) . Der Bot generiert einen Überprüfungscode und speichert ihn, der dem Benutzer zugeordnet ist. Der Überprüfungscode wird automatisch von Teams gesendet, wie unten in den Schritten 9 und 10 beschrieben. ([Code anzeigen](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/AuthBot.ts#L100-L113))
9. Der OAuth-Rückruf rendert eine Seite, die aufruft `notifySuccess("<verification code>")`. ([Code anzeigen](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/master/src/views/oauth-callback-success.hbs))
10. Teams schließt das Popup und sendet das `<verification code>` Gesendete an `notifySuccess()` den Bot zurück. Der Bot empfängt eine [Aufrufnachricht](/bot-framework/dotnet/bot-builder-dotnet-activities#invoke) mit `name = signin/verifyState`.
11. Der Bot überprüft den eingehenden Überprüfungscode anhand des Überprüfungscodes, der mit dem vorläufigen Token des Benutzers gespeichert ist. ([Code anzeigen](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/dialogs/BaseIdentityDialog.ts#L127-L140))
12. Wenn sie übereinstimmen, markiert der Bot das Token als validiert und einsatzbereit. Andernfalls schlägt der Authentifizierungsfluss fehl, und der Bot löscht das vorläufige Token.

> [!Note]
> Wenn Probleme mit der Authentifizierung auf mobilen Geräten auftreten, stellen Sie sicher, dass Ihr Javascript SDK auf Version 1.4.1 oder höher aktualisiert wird.

## <a name="samples"></a>Beispiele

Beispielcode zum Anzeigen des Bot-Authentifizierungsprozesses finden Sie unter:

* [Microsoft Teams-Bot-Authentifizierungsbeispiel (Node)](https://github.com/OfficeDev/microsoft-teams-sample-auth-node)

## <a name="more-details"></a>Weitere Informationen

Ausführliche Exemplarische Vorgehensweisen zur Implementierung der Bot-Authentifizierung für Azure Active Directory finden Sie unter:

* [Authentifizieren eines Benutzers in einem Microsoft Teams-Bot](~/resources/bot-v3/bot-authentication/auth-bot-AAD.md)
