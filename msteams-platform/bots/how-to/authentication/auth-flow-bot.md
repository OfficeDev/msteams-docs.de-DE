---
title: Microsoft Teams Authentifizierungsfluss für Bots
description: Beschreibt Microsoft Teams Authentifizierungsfluss in Bots mit Codebeispiel.
keywords: Teams-Authentifizierungsfluss-Bots
ms.localizationpriority: medium
ms.topic: overview
ms.openlocfilehash: 3e677c746b4cc548b4f8977dbaf61666c3fa85ce
ms.sourcegitcommit: eeaa8cbb10b9dfa97e9c8e169e9940ddfe683a7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2022
ms.locfileid: "65756870"
---
# <a name="authentication-flow-for-bots-in-microsoft-teams"></a>Authentifizierungsfluss für Bots in Microsoft Teams

OAuth 2.0 ist ein offener Standard für die Authentifizierung und Autorisierung, der von Azure Active Directory und vielen anderen Identitätsanbietern verwendet wird. Ein grundlegendes Verständnis von OAuth 2.0 ist eine Voraussetzung für die Arbeit mit der Authentifizierung in Teams; [Hier ist eine gute Übersicht](https://aaronparecki.com/oauth-2-simplified/), die einfacher zu befolgen ist als die [formale Spezifikation](https://oauth.net/2/). Der Authentifizierungsfluss für Registerkarten und Bots unterscheidet sich ein wenig – Registerkarten ähneln Websites, sodass sie OAuth 2.0 direkt verwenden können, während Bots einige Dinge nicht anders ausführen müssen, aber die Kernkonzepte sind identisch.

Ein Beispiel, das den Authentifizierungsfluss für Bots mit Node.js und dem [OAuth 2.0-Autorisierungscodegenehmigungstyp](https://oauth.net/2/grant-types/authorization-code/) veranschaulicht, finden Sie im GitHub Repository Microsoft Teams [Authentifizierungsbeispiel](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-auth/nodejs).

![Bot-Authentifizierungssequenzdiagramm](../../../assets/images/authentication/bot_auth_sequence_diagram.png)

1. Der Benutzer sendet eine Nachricht an den Bot.
2. Der Bot bestimmt, ob sich der Benutzer anmelden muss.
   In diesem Beispiel speichert der Bot das Zugriffstoken im Benutzerdatenspeicher. Der Benutzer wird aufgefordert, sich anzumelden, wenn er kein überprüftes Token für den ausgewählten Identitätsanbieter hat. ([Code anzeigen](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/utils/AuthenticationUtils.ts#L58-L76))
3. Der Bot erstellt die URL zur Startseite des Authentifizierungsflusses und sendet dem Benutzer eine Karte mit einer `signin` Aktion. ([Code anzeigen](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/dialogs/BaseIdentityDialog.ts#L160-L190))</br>
    Wie andere Anwendungsauthentifizierungsflüsse in Teams muss sich die Startseite in einer Domäne befinden, die sich in Ihrer `validDomains` Liste befindet, und in derselben Domäne wie die Umleitungsseite nach der Anmeldung.
    > [!IMPORTANT]
    > Der OAuth 2.0-Autorisierungscode-Genehmigungsfluss ruft einen `state` Parameter in der Authentifizierungsanforderung auf, der ein eindeutiges Sitzungstoken enthält, um einen [websiteübergreifenden Anforderungsfälschungsangriff](https://en.wikipedia.org/wiki/Cross-site_request_forgery) zu verhindern. Im Beispiel wird eine nach dem Zufallsprinzip generierte GUID verwendet.
4. Wenn der Benutzer die *Anmeldeschaltfläche* auswählt, öffnet Teams ein Popupfenster und navigiert zur Startseite.
   > [!NOTE]
   > Die Größe des Popupfensters kann über Die Zeichenfolgenparameter für die Breite und Höhe der Abfrage in der URL gesteuert werden. Wenn Sie beispielsweise "width=600" und "height=600" hinzufügen, beträgt die Größe des Popupfensters 600 x 600 Pixel. Die tatsächliche Größe des Popupfensters wird als Prozentsatz der größe des Teams Hauptfensters begrenzt. Wenn das Teams Fenster klein ist, ist das Popupfenster kleiner als die angegebenen Abmessungen.

5. Die Startseite leitet den Benutzer zum Endpunkt des Identitätsanbieters `authorize` um. ([Code anzeigen](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/public/html/auth-start.html#L51-L56))
6. Auf der Website des Anbieters meldet sich der Benutzer an und gewährt Zugriff auf den Bot.
7. Der Anbieter führt den Benutzer mit einem Autorisierungscode zur OAuth-Umleitungsseite des Bots.
8. Der Bot löst den Autorisierungscode für ein Zugriffstoken ein und ordnet das Token **vorläufig** dem Benutzer zu, der den Anmeldefluss initiiert hat. Unten wird dies als *vorläufiges Token* bezeichnet.
    * In dem Beispiel ordnet der Bot den Wert des `state` Parameters der ID des Benutzers zu, der den Anmeldevorgang initiiert hat, sodass er ihn später mit dem `state` vom Identitätsanbieter zurückgegebenen Wert abgleichen kann. ([Code anzeigen](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/AuthBot.ts#L70-L99))
      > [!IMPORTANT]
      > Der Bot speichert das Token, das er vom Identitätsanbieter empfängt, und ordnet es einem bestimmten Benutzer zu, ist aber als "ausstehende Überprüfung" gekennzeichnet.
    * Das vorläufige Token kann nicht ohne weitere Überprüfung verwendet werden.
      1. **Überprüfen Sie, was vom Identitätsanbieter empfangen wird.** Der Wert des Parameters muss anhand des `state` zuvor gespeicherten Parameters bestätigt werden.
      1. **Überprüfen Sie, was von Teams empfangen wird.** Es wird eine [zweistufige Authentifizierungsüberprüfung](https://en.wikipedia.org/wiki/Man-in-the-middle_attack) durchgeführt, um sicherzustellen, dass der Benutzer, der den Bot mit dem Identitätsanbieter autorisiert hat, derselbe Benutzer ist, der mit dem Bot chatt. Dies schützt vor [Man-in-the-Middle-](https://en.wikipedia.org/wiki/Man-in-the-middle_attack) und [Phishing-Angriffen](https://en.wikipedia.org/wiki/Phishing) . Der Bot generiert einen Überprüfungscode und speichert ihn, der dem Benutzer zugeordnet ist. Der Überprüfungscode wird automatisch von Teams wie unten beschrieben gesendet. ([Code anzeigen](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/AuthBot.ts#L100-L113))
9. Der OAuth-Rückruf rendert eine Seite, die aufruft `notifySuccess("<verification code>")`. ([Code anzeigen](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/master/src/views/oauth-callback-success.hbs))
10. Teams schließt das Popupfenster und sendet das `<verification code>` Gesendete zurück an `notifySuccess()` den Bot. Der Bot empfängt eine [Aufrufnachricht](/bot-framework/dotnet/bot-builder-dotnet-activities#invoke) mit `name = signin/verifyState`.
11. Der Bot überprüft den eingehenden Überprüfungscode anhand des Überprüfungscodes, der mit dem vorläufigen Token des Benutzers gespeichert ist. ([Code anzeigen](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/dialogs/BaseIdentityDialog.ts#L127-L140))
12. Wenn sie übereinstimmen, markiert der Bot das Token als validiert und einsatzbereit. Andernfalls schlägt der Authentifizierungsfluss fehl, und der Bot löscht das vorläufige Token.

    > [!NOTE]
    > Wenn Probleme mit der Authentifizierung auf mobilen Geräten auftreten, stellen Sie sicher, dass Ihr JavaScript SDK auf Version 1.4.1 oder höher aktualisiert wird.

## <a name="code-sample"></a>Codebeispiel

Beispielcode, der den Bot-Authentifizierungsprozess zeigt:

| **Beispielname** | **Beschreibung** | **Node.js** | **.NET** | **Python** |
|-----------------|----------------|--------------|----------|-----------|
| Teams Authentifizierung | In diesem Beispiel wird die Authentifizierung in Microsoft Teams Apps veranschaulicht. | [View](https://github.com/OfficeDev/microsoft-teams-sample-auth-node) | | |
| Bot-Authentifizierung | In diesem Beispiel wird die Verwendung der Authentifizierung für einen Bot veranschaulicht, der in Microsoft Teams | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/46.teams-auth) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/46.teams-auth) | [Anzeigen](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/46.teams-auth)

## <a name="see-also"></a>Siehe auch

[Authentifizierung für Ihren Teams-Bot hinzufügen](add-authentication.md)
