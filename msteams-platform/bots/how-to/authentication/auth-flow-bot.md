---
title: Microsoft Teams-Authentifizierungsfluss für Bots
description: Beschreibt den Microsoft Teams-Authentifizierungsfluss in Bots
keywords: Teams-Authentifizierungsflussbots
ms.topic: overview
ms.openlocfilehash: e76b318f11e651bbf1c20131c5d0d482c2494b60
ms.sourcegitcommit: dd2220f691029d043aaddfc7c229e332735acb1d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2021
ms.locfileid: "51995911"
---
# <a name="authentication-flow-for-bots-in-microsoft-teams"></a>Authentifizierungsfluss für Bots in Microsoft Teams

OAuth 2.0 ist ein offener Standard für Authentifizierung und Autorisierung, der von Azure Active Directory (Azure AD) und vielen anderen Identitätsanbietern verwendet wird. Ein grundlegendes Verständnis von OAuth 2.0 ist eine Voraussetzung für die Arbeit mit der Authentifizierung in Teams. [Hier finden Sie eine gute Übersicht,](https://aaronparecki.com/oauth-2-simplified/) die einfacher zu befolgen ist als die [formale Spezifikation.](https://oauth.net/2/) Der Authentifizierungsfluss für Registerkarten und Bots ist etwas anders. Registerkarten ähneln Websites sehr, sodass sie OAuth 2.0 direkt verwenden können, während Bots nicht und müssen einiges anders tun – die Kernkonzepte sind jedoch identisch.

Ein Beispiel für den Authentifizierungsfluss von Bots mithilfe von Node.js und dem OAuth 2.0-Autorisierungscode-Grant-Typ finden Sie im Microsoft [Teams-Authentifizierungsbeispiel](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-auth/nodejs) für GitHub-Repository. [](https://oauth.net/2/grant-types/authorization-code/)

![Bot-Authentifizierungssequenzdiagramm](../../../assets/images/authentication/bot_auth_sequence_diagram.png)

1. Der Benutzer sendet eine Nachricht an den Bot.
2. Der Bot bestimmt, ob sich der Benutzer anmelden muss.
   In diesem Beispiel speichert der Bot das Zugriffstoken im Benutzerdatenspeicher. Er fordert den Benutzer auf, sich zu melden, wenn er kein überprüftes Token für den ausgewählten Identitätsanbieter hat. ([View code](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/utils/AuthenticationUtils.ts#L58-L76))
3. Der Bot erstellt die URL zur Startseite des Authentifizierungsflusses und sendet eine Karte mit einer Aktion an den `signin` Benutzer. ([View code](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/dialogs/BaseIdentityDialog.ts#L160-L190))</br>
    Wie andere Anwendungsauthentifizierungsflüsse in Teams muss sich die Startseite in einer Domäne befinden, die sich in Ihrer Liste und in derselben Domäne wie die Umleitungsseite nach der Anmeldung `validDomains` befinden.
    > [!IMPORTANT] 
    > Der OAuth 2.0-Autorisierungscode grant flow ruft einen Parameter in der Authentifizierungsanforderung auf, der ein eindeutiges Sitzungstoken enthält, um einen standortübergreifenden Anforderungsfälschungsangriff `state` [zu verhindern.](https://en.wikipedia.org/wiki/Cross-site_request_forgery) Das Beispiel verwendet eine zufällig generierte GUID.
4. Wenn der Benutzer die *Anmeldeschaltfläche* auswählt, öffnet Teams ein Popupfenster und navigiert zur Startseite.
   > [!NOTE]
   > Die Größe des Popupfensters kann über die Parameter für Die Breite und Höhe der Abfragezeichenfolge in der URL gesteuert werden. Wenn Sie beispielsweise width=500 und height=500 hinzufügen, beträgt die Größe des Popupfensters 500 x 500 Pixel. Teams zeigt das Popupfenster mit der angegebenen Pixelgröße an, bis zu einem Höchstwert, der ein Prozentsatz der Größe des Hauptfensters ist.

5. Die Startseite leitet den Benutzer an den Endpunkt des `authorize` Identitätsanbieters um. ([View code](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/public/html/auth-start.html#L51-L56))
6. Auf der Website des Anbieters meldet sich der Benutzer an und gewährt Zugriff auf den Bot.
7. Der Anbieter führt den Benutzer mit einem Autorisierungscode zur OAuth-Umleitungsseite des Bots.
8. Der Bot löst den Autorisierungscode für  ein Zugriffstoken ein und ordnet das Token vorläufig dem Benutzer zu, der den Anmeldefluss initiiert hat. Nachfolgend wird dies als *vorläufiges Token bezeichnet.*
    * Im Beispiel ordnet der Bot den Wert des Parameters der ID des Benutzers zu, der den Anmeldevorgang initiiert hat, damit er später mit dem vom Identitätsanbieter zurückgegebenen Wert `state` `state` übereinstimmen kann. ([View code](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/AuthBot.ts#L70-L99))
      > [!IMPORTANT] 
      > Der Bot speichert das Token, das er vom Identitätsanbieter erhält, und ordnet es einem bestimmten Benutzer zu, wird jedoch als "ausstehende Überprüfung" gekennzeichnet. 
    * Das vorläufige Token kann nicht ohne weitere Überprüfung verwendet werden.
      1. **Überprüfen Sie, was vom Identitätsanbieter empfangen wird.** Der Wert des Parameters muss mit dem zuvor `state` gespeicherten Wert bestätigt werden. 
      1. **Überprüfen Sie, was von Teams empfangen wird.** Eine [zweistufige](https://en.wikipedia.org/wiki/Man-in-the-middle_attack) Authentifizierungsüberprüfung wird durchgeführt, um sicherzustellen, dass der Benutzer, der den Bot mit dem Identitätsanbieter autorisiert hat, derselbe Benutzer ist, der mit dem Bot chatt. Dadurch wird vor [Man-in-the-Middle- und](https://en.wikipedia.org/wiki/Man-in-the-middle_attack) [Phishingangriffen gewehrt.](https://en.wikipedia.org/wiki/Phishing) Der Bot generiert einen Überprüfungscode und speichert ihn, der dem Benutzer zugeordnet ist. Der Überprüfungscode wird wie unten beschrieben automatisch von Teams gesendet. ([View code](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/AuthBot.ts#L100-L113))
9. Der OAuth-Rückruf rendert eine Seite, die `notifySuccess("<verification code>")` aufruft. ([View code](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/master/src/views/oauth-callback-success.hbs))
10. Teams schließt das Popupfenster und sendet das `<verification code>` gesendete an `notifySuccess()` zurück an den Bot. Der Bot empfängt eine [Aufrufnachricht](/bot-framework/dotnet/bot-builder-dotnet-activities#invoke) mit `name = signin/verifyState` .
11. Der Bot überprüft den eingehenden Überprüfungscode mit dem Überprüfungscode, der mit dem vorläufigen Token des Benutzers gespeichert ist. ([View code](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/dialogs/BaseIdentityDialog.ts#L127-L140))
12. Wenn sie übereinstimmen, markiert der Bot das Token als überprüft und einsatzbereit. Andernfalls schlägt der Authentifizierungsfluss fehl, und der Bot löscht das vorläufige Token.

    > [!NOTE]
    > Wenn Probleme mit der Authentifizierung auf Mobilgeräten auftreten, stellen Sie sicher, dass Ihr JavaScript SDK auf Version 1.4.1 oder höher aktualisiert wird.

## <a name="code-sample"></a>Codebeispiel

Beispielcode für den Botauthentifizierungsprozess:

| **Beispielname** | **Beschreibung** | **Node.js** | **.NET** | **Python** |
|-----------------|----------------|--------------|----------|-----------|
| Teams-Authentifizierung | In diesem Beispiel wird die Authentifizierung in Microsoft Teams-Apps veranschaulicht. | [View](https://github.com/OfficeDev/microsoft-teams-sample-auth-node) | | |
| Bot-Authentifizierung | In diesem Beispiel wird die Verwendung der Authentifizierung für eine Bot-Ausführung in Microsoft Teams gestartet. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/46.teams-auth) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/46.teams-auth) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/46.teams-auth)

## <a name="more-details"></a>Weitere Details

Ausführliche implementierungs exemplarische Vorgehensweisen für die Botauthentifizierung für Azure AD finden Sie unter:

[Hinzufügen der Authentifizierung zu Ihrem Teams-Bot](add-authentication.md)
