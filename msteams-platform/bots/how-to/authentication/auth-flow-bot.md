---
title: Microsoft Teams Authentifizierungsfluss für Bots
description: Beschreibt Microsoft Teams Authentifizierungsfluss in Bots
keywords: Teams-Authentifizierungsfluss-Bots
localization_priority: Normal
ms.topic: overview
ms.openlocfilehash: 0eb4808cc162b293404530f7da7ac9d63b9f98cb86a0d864866fd31e388ecb89
ms.sourcegitcommit: 3ab1cbec41b9783a7abba1e0870a67831282c3b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2021
ms.locfileid: "57708319"
---
# <a name="authentication-flow-for-bots-in-microsoft-teams"></a>Authentifizierungsfluss für Bots in Microsoft Teams

OAuth 2.0 ist ein offener Standard für Authentifizierung und Autorisierung, der von Azure Active Directory (Azure AD) und vielen anderen Identitätsanbietern verwendet wird. Ein grundlegendes Verständnis von OAuth 2.0 ist eine Voraussetzung für die Arbeit mit der Authentifizierung in Teams; [Hier ist eine gute Übersicht,](https://aaronparecki.com/oauth-2-simplified/) die leichter zu befolgen ist als die [formale Spezifikation.](https://oauth.net/2/) Der Authentifizierungsfluss für Registerkarten und Bots ist ein wenig anders – Registerkarten sind Websites sehr ähnlich, sodass sie OAuth 2.0 direkt verwenden können, während Bots einige Dinge nicht anders ausführen müssen und müssen, aber die Kernkonzepte sind identisch.

Ein Beispiel, das den Authentifizierungsfluss für Bots mit Node.js und dem [OAuth 2.0-Autorisierungscode-Erteilungstyp](https://oauth.net/2/grant-types/authorization-code/)veranschaulicht, finden Sie im GitHub Repository Microsoft Teams [Authentifizierungsbeispiel.](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-auth/nodejs)

![Diagramm der Bot-Authentifizierungssequenz](../../../assets/images/authentication/bot_auth_sequence_diagram.png)

1. Der Benutzer sendet eine Nachricht an den Bot.
2. Der Bot bestimmt, ob sich der Benutzer anmelden muss.
   In diesem Beispiel speichert der Bot das Zugriffstoken in seinem Benutzerdatenspeicher. Der Benutzer wird aufgefordert, sich anzumelden, wenn er kein überprüftes Token für den ausgewählten Identitätsanbieter hat. ([Ansichtscode](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/utils/AuthenticationUtils.ts#L58-L76))
3. Der Bot erstellt die URL zur Startseite des Authentifizierungsflusses und sendet eine Karte mit einer Aktion an den `signin` Benutzer. ([Ansichtscode](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/dialogs/BaseIdentityDialog.ts#L160-L190))</br>
    Wie andere Anwendungsauthentifizierungsflüsse in Teams muss sich die Startseite in einer Domäne befinden, die sich in Ihrer `validDomains` Liste befindet, und in derselben Domäne wie die Umleitungsseite nach der Anmeldung.
    > [!IMPORTANT] 
    > Der OAuth 2.0-Autorisierungscode-Genehmigungsfluss ruft einen `state` Parameter in der Authentifizierungsanforderung auf, der ein eindeutiges Sitzungstoken enthält, um einen [websiteübergreifenden Anforderungs-Forgery-Angriff](https://en.wikipedia.org/wiki/Cross-site_request_forgery)zu verhindern. Im Beispiel wird eine zufällig generierte GUID verwendet.
4. Wenn der Benutzer die *Anmeldeschaltfläche* auswählt, öffnet Teams ein Popupfenster und navigiert zur Startseite.
   > [!NOTE]
   > Die Größe des Popupfensters kann über Die Abfragezeichenfolgenparameter für Breite und Höhe in der URL gesteuert werden. Wenn Sie beispielsweise width=600 und height=600 hinzufügen, beträgt die Größe des Popupfensters 600 x 600 Pixel. Die tatsächliche Größe des Popupfensters ist als Prozentsatz der Teams Hauptfenstergröße begrenzt. Wenn das Teams Fenster klein ist, ist das Popupfenster kleiner als die angegebenen Abmessungen.

5. Die Startseite leitet den Benutzer an den Endpunkt des Identitätsanbieters `authorize` weiter. ([Ansichtscode](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/public/html/auth-start.html#L51-L56))
6. Auf der Website des Anbieters meldet sich der Benutzer an und gewährt Zugriff auf den Bot.
7. Der Anbieter führt den Benutzer mit einem Autorisierungscode zur OAuth-Umleitungsseite des Bots.
8. Der Bot löst den Autorisierungscode für ein Zugriffstoken ein und ordnet das Token **vorläufig** dem Benutzer zu, der den Anmeldefluss initiiert hat. Nachfolgend wird dies als *vorläufiges Token bezeichnet.*
    * In dem Beispiel ordnet der Bot den Wert des Parameters der ID des Benutzers zu, `state` der den Anmeldevorgang initiiert hat, damit er ihn später mit dem vom Identitätsanbieter zurückgegebenen Wert abgleichen `state` kann. ([Ansichtscode](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/AuthBot.ts#L70-L99))
      > [!IMPORTANT] 
      > Der Bot speichert das Token, das er vom Identitätsanbieter erhält, und ordnet es einem bestimmten Benutzer zu, ist jedoch als "Ausstehende Überprüfung" gekennzeichnet. 
    * Das vorläufige Token kann ohne weitere Überprüfung nicht verwendet werden.
      1. **Überprüfen, was vom Identitätsanbieter empfangen wird.** Der Wert des Parameters muss gegenüber dem `state` bestätigt werden, was zuvor gespeichert wurde. 
      1. **Überprüfen, was von Teams empfangen wird.** Es wird eine [zweistufige Authentifizierungsüberprüfung](https://en.wikipedia.org/wiki/Man-in-the-middle_attack) durchgeführt, um sicherzustellen, dass der Benutzer, der den Bot mit dem Identitätsanbieter autorisiert hat, derselbe Benutzer ist, der mit dem Bot chatscht. Dies schützt vor [Man-in-the-Middle-](https://en.wikipedia.org/wiki/Man-in-the-middle_attack) und [Phishing-Angriffen.](https://en.wikipedia.org/wiki/Phishing) Der Bot generiert einen Überprüfungscode und speichert ihn, der dem Benutzer zugeordnet ist. Der Überprüfungscode wird automatisch von Teams wie unten beschrieben gesendet. ([Ansichtscode](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/AuthBot.ts#L100-L113))
9. Der OAuth-Rückruf rendert eine Seite, die `notifySuccess("<verification code>")` aufruft. ([Ansichtscode](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/master/src/views/oauth-callback-success.hbs))
10. Teams schließt das Popupfenster und sendet das `<verification code>` Gesendete `notifySuccess()` an den Bot zurück. Der Bot empfängt eine [Aufrufnachricht](/bot-framework/dotnet/bot-builder-dotnet-activities#invoke) mit `name = signin/verifyState` .
11. Der Bot überprüft den eingehenden Überprüfungscode anhand des Überprüfungscodes, der mit dem vorläufigen Token des Benutzers gespeichert ist. ([Ansichtscode](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/dialogs/BaseIdentityDialog.ts#L127-L140))
12. Wenn sie übereinstimmen, markiert der Bot das Token als überprüft und einsatzbereit. Andernfalls schlägt der Authentifizierungsfluss fehl, und der Bot löscht das vorläufige Token.

    > [!NOTE]
    > Wenn Probleme mit der Authentifizierung auf mobilen Geräten auftreten, stellen Sie sicher, dass Ihr JavaScript-SDK auf Version 1.4.1 oder höher aktualisiert wird.

## <a name="code-sample"></a>Codebeispiel

Beispielcode für den Bot-Authentifizierungsprozess:

| **Beispielname** | **Beschreibung** | **Node.js** | **.NET** | **Python** |
|-----------------|----------------|--------------|----------|-----------|
| Teams-Authentifizierung | In diesem Beispiel wird die Authentifizierung in Microsoft Teams Apps veranschaulicht. | [Anzeigen](https://github.com/OfficeDev/microsoft-teams-sample-auth-node) | | |
| Bot-Authentifizierung | In diesem Beispiel wird die Verwendung der Authentifizierung für einen Bot veranschaulicht, der in Microsoft Teams | [Anzeigen](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/46.teams-auth) | [Anzeigen](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/46.teams-auth) | [Anzeigen](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/46.teams-auth)

## <a name="see-also"></a>Siehe auch

[Hinzufügen der Authentifizierung zu Ihrem Teams-Bot](add-authentication.md)
