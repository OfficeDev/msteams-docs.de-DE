---
title: Authentifizierungs Fluss für Registerkarten
description: Beschreibt den Authentifizierungs Fluss in Registerkarten
keywords: Registerkarten für Teams-Authentifizierungs Fluss
ms.openlocfilehash: 6c669162f407924f0844b89625f5c5791e96b6f7
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674333"
---
# <a name="microsoft-teams-authentication-flow-for-tabs"></a>Microsoft Teams-Authentifizierungs Fluss für Registerkarten

> [!Note]
> Damit die Authentifizierung für Ihre Registerkarte auf mobilen Clients funktioniert, müssen Sie sicherstellen, dass Sie mindestens die Version 1.4.1 von Microsoft Teams JavaScript SDK verwenden.

OAuth 2,0 ist ein offener Standard für Authentifizierung und Autorisierung, der von Azure AD und vielen anderen Identitätsanbietern verwendet wird. Ein grundlegendes Verständnis von OAuth 2,0 ist eine Voraussetzung für die Verwendung von Authentifizierung in Microsoft Teams. [hier finden Sie eine gute Übersicht](https://aaronparecki.com/oauth-2-simplified/) , die einfacher zu befolgen ist als die [formale Spezifikation](https://oauth.net/2/). Der Authentifizierungs Fluss für Registerkarten und Bots ist ein wenig anders, da Registerkarten sehr ähnlich zu Websites sind, sodass Sie OAuth 2,0 direkt verwenden können. Bots sind nicht und müssen ein paar Dinge unterschiedlich tun, aber die Kernkonzepte sind identisch.

ein Beispiel zur Veranschaulichung des Authentifizierungs Flusses für Registerkarten und Bots mithilfe von Node mithilfe des [impliziten Grant-Typs OAuth 2,0](https://oauth.net/2/grant-types/implicit/).

![Tab-Authentifizierungs-Sequenzdiagramm](~/assets/images/authentication/tab_auth_sequence_diagram.png)

1. Der Benutzer interagiert mit dem Inhalt auf der Registerkarte Konfiguration oder Inhaltsseite, häufig eine Schaltfläche mit der Bezeichnung "Anmelden" oder "Anmelden".
2. Die Registerkarte erstellt die URL für Ihre Authentifizierungs Startseite, optional mithilfe von Informationen aus URL-Platzhaltern oder durch Aufrufen `microsoftTeams.getContext()` der Teams-Client-SDK-Methode, um die Authentifizierungs Erfahrung für den Benutzer zu rationalisieren. Wenn der `login_hint` Parameter beispielsweise bei der Authentifizierung mit Azure AD auf die e-Mail-Adresse des Benutzers festgelegt ist, muss sich der Benutzer möglicherweise nicht mehr anmelden, wenn er dies kürzlich getan hat, da Azure Ad die zwischengespeicherten Anmeldeinformationen des Benutzers nach Möglichkeit verwenden wird: das Popup blinkt kurz und wird dann ausgeblendet.
3. Anschließend ruft die Registerkarte `microsoftTeams.authentication.authenticate()` die-Methode auf `successCallback` und `failureCallback` registriert die Funktionen und.
4. Teams öffnet die Startseite in einem IFRAME in einem Popupfenster. Auf der Startseite werden `state` zufällige Daten generiert, für die zukünftige Validierung gespeichert und an den `/authorize` Endpunkt des Identitätsanbieters umgeleitet (Beispiels `https://login.microsoftonline.com/<tenant ID>/oauth2/authorize` Weise für Azure AD). Ersetzen `<tenant id>` Sie durch ihre eigene Mandanten-ID (Context. TID).
    * Wie bei anderen Anwendungs Authentifizierungs Bewegungen in Microsoft Teams muss sich die Startseite in einer Domäne befinden, `validDomains` die sich in der Liste befindet, und in derselben Domäne wie die Umleitungsseite nach der Anmeldung.
    * **Wichtig**: der implizite Grant-Fluss von OAuth 2,0 `state` Ruft einen Parameter in der Authentifizierungsanforderung ab, der eindeutige Sitzungsdaten enthält, um einen [Fälschungs Angriff auf standortübergreifendes anfordern](https://en.wikipedia.org/wiki/Cross-site_request_forgery)zu verhindern. In den folgenden Beispielen wird eine zufällig generierte GUID für die `state` Daten verwendet.
5. Der Benutzer meldet sich auf der Website des Anbieters an und erteilt Zugriff auf die Registerkarte.
6. Der Anbieter führt den Benutzer zur Umleitungsseite der Registerkarte OAuth 2,0 mit einem Zugriffstoken.
7. Auf der Registerkarte wird überprüft `state` , ob der zurückgegebene Wert mit `microsoftTeams.authentication.notifySuccess()`dem zuvor gespeicherten übereinstimmt, `successCallback` und Aufrufe, die wiederum die in Schritt 3 registrierte Funktion aufrufen.
8. Das Popupfenster wird von Microsoft Teams geschlossen.
9. Auf der Registerkarte wird entweder die Konfigurationsbenutzeroberfläche angezeigt oder der Inhalt der Registerkarten aktualisiert oder neu geladen, je nachdem, von wo aus der Benutzer gestartet hat.

## <a name="treat-tab-context-as-hints"></a>Behandeln des Registerkarten Kontexts als Hinweise

Obwohl der Registerkartenkontext nützliche Informationen für den Benutzer bereitstellt, verwenden Sie diese Informationen nicht, um den Benutzer zu authentifizieren, unabhängig davon, ob Sie ihn als URL-Parameter `microsoftTeams.getContext()` zu ihrer Registerkarten-Inhalts-URL oder durch Aufrufen der Funktion im Microsoft Teams-Client-SDK erhalten. Ein böswilliger Akteur könnte Ihre Registerkarteninhalts-URL mit seinen eigenen Parametern aufrufen, und eine Webseite, die Microsoft Teams imitiert, kann die URL Ihres Registerkarteninhalts in einen iframe laden `getContext()` und eigene Daten an die Funktion zurückgeben. Sie sollten die identitätsbezogenen Informationen im Registerkartenkontext lediglich als Hinweise behandeln und diese vor der Verwendung validieren.

## <a name="samples"></a>Beispiele

Beispielcode zum Anzeigen des Registerkarten Authentifizierungsprozesses finden Sie unter:

* [Beispiel für Microsoft Teams-Registerkarten Authentifizierung (Knoten)](https://github.com/OfficeDev/microsoft-teams-sample-complete-node)
* [Microsoft Teams-Registerkarten Authentifizierung (Beispiel) (C#)](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp)

## <a name="more-details"></a>Weitere Details

Eine ausführliche Implementierungs Exemplarische Vorgehensweise für die Registerkarten Authentifizierung für Azure Active Directory finden Sie unter:

* [Authentifizieren eines Benutzers auf einer Microsoft Teams-Registerkarte](~/tabs/how-to/authentication/auth-tab-AAD.md)
* [Automatische Authentifizierung](~/tabs/how-to/authentication/auth-silent-AAD.md)
