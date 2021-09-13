---
title: Authentifizierungsfluss für Bots
description: Beschreibt den Authentifizierungsfluss in Bots
keywords: Teams-Authentifizierungsfluss-Bots
localization_priority: Normal
ms.topic: conceptual
ms.date: 03/01/2018
ms.openlocfilehash: fe7e528be98a0b58334535952327b6026b30a87d
ms.sourcegitcommit: fc9f906ea1316028d85b41959980b81f2c23ef2f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2021
ms.locfileid: "59156758"
---
# <a name="microsoft-teams-authentication-flow-for-bots"></a>Microsoft Teams Authentifizierungsfluss für Bots

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

OAuth 2.0 ist ein offener Standard für die Authentifizierung und Autorisierung, der von Azure AD und vielen anderen Identitätsanbietern verwendet wird. Ein grundlegendes Verständnis von OAuth 2.0 ist eine Voraussetzung für die Arbeit mit der Authentifizierung in Teams; [Hier ist eine gute Übersicht,](https://aaronparecki.com/oauth-2-simplified/) die einfacher zu befolgen ist als die [formale Spezifikation.](https://oauth.net/2/) Der Authentifizierungsfluss für Registerkarten und Bots unterscheidet sich etwas, da Registerkarten Websites sehr ähnlich sind, sodass sie OAuth 2.0 direkt verwenden können. Bots sind und müssen einige Dinge nicht anders ausführen, aber die Kernkonzepte sind identisch.

Ein Beispiel, das den Authentifizierungsfluss für Bots veranschaulicht, die Node mithilfe des [OAuth 2.0-Autorisierungscodeerteilungstyps](https://oauth.net/2/grant-types/authorization-code/)verwenden, finden Sie im GitHub Repository Microsoft Teams [Authentication-Beispiel.](https://github.com/OfficeDev/microsoft-teams-sample-auth-node)

![Diagramm der Bot-Authentifizierungssequenz](~/assets/images/authentication/bot_auth_sequence_diagram.png)

1. Der Benutzer sendet eine Nachricht an den Bot.
2. Der Bot bestimmt, ob sich der Benutzer anmelden muss.
    * In diesem Beispiel speichert der Bot das Zugriffstoken in seinem Benutzerdatenspeicher. Der Benutzer wird aufgefordert, sich anzumelden, wenn kein überprüftes Token für den ausgewählten Identitätsanbieter vorhanden ist. ([Ansichtscode](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/utils/AuthenticationUtils.ts#L58-L76))
3. Der Bot erstellt die URL zur Startseite des Authentifizierungsflusses und sendet eine Karte mit einer Aktion an den `signin` Benutzer. ([Ansichtscode](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/dialogs/BaseIdentityDialog.ts#L160-L190))
    * Wie andere Anwendungsauthentifizierungsflüsse in Teams muss sich die Startseite in einer Domäne befinden, die sich in Ihrer `validDomains` Liste befindet, und in derselben Domäne wie die Umleitungsseite nach der Anmeldung.
    * **WICHTIG:** Der OAuth 2.0-Autorisierungscode-Genehmigungsfluss ruft einen `state` Parameter in der Authentifizierungsanforderung auf, der ein eindeutiges Sitzungstoken enthält, um einen [websiteübergreifenden Anforderungs-Forgery-Angriff](https://en.wikipedia.org/wiki/Cross-site_request_forgery)zu verhindern. Im Beispiel wird eine zufällig generierte GUID verwendet.
4. Wenn der Benutzer auf die *Anmeldeschaltfläche* klickt, öffnet Teams ein Popupfenster und navigiert zur Startseite.
5. Die Startseite leitet den Benutzer an den Endpunkt des Identitätsanbieters `authorize` weiter. ([Ansichtscode](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/public/html/auth-start.html#L51-L56))
6. Auf der Website des Anbieters meldet sich der Benutzer an und gewährt Zugriff auf den Bot.
7. Der Anbieter führt den Benutzer mit einem Autorisierungscode zur OAuth-Umleitungsseite des Bots.
8. Der Bot löst den Autorisierungscode für ein Zugriffstoken ein und ordnet das Token **vorläufig** dem Benutzer zu, der den Anmeldefluss initiiert hat. Nachfolgend wird dies als *vorläufiges Token bezeichnet.*
    * In dem Beispiel ordnet der Bot den Wert des Parameters der ID des Benutzers zu, `state` der den Anmeldevorgang initiiert hat, damit er ihn später mit dem vom Identitätsanbieter zurückgegebenen Wert abgleichen `state` kann. ([Ansichtscode](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/AuthBot.ts#L70-L99))
    * **WICHTIG:** Der Bot speichert das Token, das er vom Identitätsanbieter erhält, und ordnet es einem bestimmten Benutzer zu, ist jedoch als "ausstehende Überprüfung" gekennzeichnet. Das vorläufige Token kann noch nicht verwendet werden: Es muss weiter überprüft werden: 
      1. **Überprüfen, was vom Identitätsanbieter empfangen wird.** Der Wert des Parameters muss gegenüber dem `state` bestätigt werden, was zuvor gespeichert wurde. 
      1. **Überprüfen, was von Teams empfangen wird.** Es wird eine [zweistufige Authentifizierungsüberprüfung](https://en.wikipedia.org/wiki/Man-in-the-middle_attack) durchgeführt, um sicherzustellen, dass der Benutzer, der den Bot mit dem Identitätsanbieter autorisiert hat, derselbe Benutzer ist, der mit dem Bot chatscht. Dies schützt vor [Man-in-the-Middle-](https://en.wikipedia.org/wiki/Man-in-the-middle_attack) und [Phishing-Angriffen.](https://en.wikipedia.org/wiki/Phishing) Der Bot generiert einen Überprüfungscode und speichert ihn, der dem Benutzer zugeordnet ist. Der Überprüfungscode wird automatisch von Teams gesendet, wie unten in den Schritten 9 und 10 beschrieben. ([Ansichtscode](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/AuthBot.ts#L100-L113))
9. Der OAuth-Rückruf rendert eine Seite, die `notifySuccess("<verification code>")` aufruft. ([Ansichtscode](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/master/src/views/oauth-callback-success.hbs))
10. Teams schließt das Popup und sendet das `<verification code>` Gesendete `notifySuccess()` an den Bot zurück. Der Bot empfängt eine [Aufrufnachricht](/bot-framework/dotnet/bot-builder-dotnet-activities#invoke) mit `name = signin/verifyState` .
11. Der Bot überprüft den eingehenden Überprüfungscode anhand des Überprüfungscodes, der mit dem vorläufigen Token des Benutzers gespeichert ist. ([Ansichtscode](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/dialogs/BaseIdentityDialog.ts#L127-L140))
12. Wenn sie übereinstimmen, markiert der Bot das Token als überprüft und einsatzbereit. Andernfalls schlägt der Authentifizierungsfluss fehl, und der Bot löscht das vorläufige Token.

> [!Note]
> Wenn Probleme mit der Authentifizierung auf mobilen Geräten auftreten, stellen Sie sicher, dass Ihr Javascript SDK auf Version 1.4.1 oder höher aktualisiert ist.

## <a name="samples"></a>Beispiele

Beispielcode für den Bot-Authentifizierungsprozess finden Sie unter:

* [Microsoft Teams Bot-Authentifizierungsbeispiel (Node)](https://github.com/OfficeDev/microsoft-teams-sample-auth-node)

## <a name="more-details"></a>Weitere Informationen

Ausführliche Exemplarische Vorgehensweisen zur Implementierung der Bot-Authentifizierung für Azure Active Directory finden Sie unter:

* [Authentifizieren eines Benutzers in einem Microsoft Teams-Bot](~/resources/bot-v3/bot-authentication/auth-bot-AAD.md)
