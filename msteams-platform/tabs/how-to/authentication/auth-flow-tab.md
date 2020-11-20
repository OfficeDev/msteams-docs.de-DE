---
title: Authentifizierungs Fluss für Registerkarten
description: Beschreibt den Authentifizierungs Fluss in Registerkarten
keywords: Registerkarten für Teams-Authentifizierungs Fluss
ms.openlocfilehash: de5e0312e4523c3adef211dc03b0349c205f92cb
ms.sourcegitcommit: 64acd30eee8af5fe151e9866c13226ed3f337c72
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/18/2020
ms.locfileid: "49346679"
---
# <a name="microsoft-teams-authentication-flow-for-tabs"></a>Microsoft Teams-Authentifizierungs Fluss für Registerkarten

> [!Note]
> Damit die Authentifizierung für Ihre Registerkarte auf mobilen Clients funktioniert, müssen Sie sicherstellen, dass Sie mindestens die Version 1.4.1 von Microsoft Teams JavaScript SDK verwenden.
> Microsoft Teams SDK startet ein separates Fenster für den Authentifizierungs Fluss und daher kann SameSite-Attribut auf "Lax" festgelegt werden. Derzeit wird SameSite = None nicht vom Microsoft Teams-Desktop Client oder älteren Versionen von Chrome oder Safari unterstützt.

OAuth 2,0 ist ein offener Standard für Authentifizierung und Autorisierung, der von Azure AD und vielen anderen Identitätsanbietern verwendet wird. Ein grundlegendes Verständnis von OAuth 2,0 ist eine Voraussetzung für die Verwendung von Authentifizierung in Microsoft Teams. [hier finden Sie eine gute Übersicht](https://aaronparecki.com/oauth-2-simplified/) , die einfacher zu befolgen ist als die [formale Spezifikation](https://oauth.net/2/). Der Authentifizierungs Fluss für Registerkarten und Bots ist ein wenig anders, da Registerkarten sehr ähnlich zu Websites sind, sodass Sie OAuth 2,0 direkt verwenden können. Bots sind nicht und müssen ein paar Dinge unterschiedlich tun, aber die Kernkonzepte sind identisch.

ein Beispiel zur Veranschaulichung des Authentifizierungs Flusses für Registerkarten und Bots mithilfe von Node mithilfe des [impliziten Grant-Typs OAuth 2,0](https://oauth.net/2/grant-types/implicit/).

![Tab-Authentifizierungs-Sequenzdiagramm](~/assets/images/authentication/tab_auth_sequence_diagram.png)

1. Der Benutzer interagiert mit dem Inhalt auf der Registerkarte Konfiguration oder Inhaltsseite, häufig eine Schaltfläche mit der Bezeichnung "Anmelden" oder "Anmelden".
2. Die Registerkarte erstellt die URL für Ihre Authentifizierungs Startseite, optional mithilfe von Informationen aus URL-Platzhaltern oder durch Aufrufen der `microsoftTeams.getContext()` Teams-Client-SDK-Methode, um die Authentifizierungs Erfahrung für den Benutzer zu rationalisieren. Wenn der Parameter beispielsweise bei der Authentifizierung mit Azure AD `login_hint` auf die e-Mail-Adresse des Benutzers festgelegt ist, muss sich der Benutzer möglicherweise nicht mehr anmelden, wenn er dies kürzlich getan hat, da Azure Ad die zwischengespeicherten Anmeldeinformationen des Benutzers nach Möglichkeit verwenden wird: das Popup blinkt kurz und wird dann ausgeblendet.
3. Auf der Registerkarte wird dann die `microsoftTeams.authentication.authenticate()`-Methode aufgerufen und die `successCallback`- und die `failureCallback`-Funktion registriert.
4. Teams öffnet die Startseite in einem IFRAME in einem Popupfenster. Auf der Startseite werden zufällige `state` Daten generiert, für die zukünftige Validierung gespeichert und an den Endpunkt des Identitätsanbieters umgeleitet `/authorize` (beispielsweise `https://login.microsoftonline.com/<tenant ID>/oauth2/authorize` für Azure AD). Ersetzen `<tenant id>` Sie durch ihre eigene Mandanten-ID (Context. TID).
    * Wie bei anderen Anwendungs Authentifizierungs Bewegungen in Microsoft Teams muss sich die Startseite in einer Domäne befinden, die sich in `validDomains` der Liste befindet, und in derselben Domäne wie die Umleitungsseite nach der Anmeldung.
    * **Wichtig**: der implizite Grant-Fluss von OAuth 2,0 Ruft einen `state` Parameter in der Authentifizierungsanforderung ab, der eindeutige Sitzungsdaten enthält, um einen [Fälschungs Angriff auf standortübergreifendes anfordern](https://en.wikipedia.org/wiki/Cross-site_request_forgery)zu verhindern. In den folgenden Beispielen wird eine zufällig generierte GUID für die `state` Daten verwendet.
5. Der Benutzer meldet sich auf der Website des Anbieters an und erteilt Zugriff auf die Registerkarte.
6. Der Anbieter führt den Benutzer zur Umleitungsseite der Registerkarte OAuth 2,0 mit einem Zugriffstoken.
7. Auf der Registerkarte wird überprüft, ob der zurückgegebene Wert mit dem `state` zuvor gespeicherten übereinstimmt, und Aufrufe `microsoftTeams.authentication.notifySuccess()` , die wiederum die `successCallback` in Schritt 3 registrierte Funktion aufrufen.
8. Das Popupfenster wird von Microsoft Teams geschlossen.
9. Auf der Registerkarte wird entweder die Konfigurationsbenutzeroberfläche angezeigt oder der Inhalt der Registerkarten aktualisiert oder neu geladen, je nachdem, von wo aus der Benutzer gestartet hat.

## <a name="treat-tab-context-as-hints"></a>Behandeln des Registerkarten Kontexts als Hinweise

Obwohl der Registerkartenkontext nützliche Informationen für den Benutzer bereitstellt, verwenden Sie diese Informationen nicht, um den Benutzer zu authentifizieren, unabhängig davon, ob Sie ihn als URL-Parameter zu ihrer Registerkarten-Inhalts-URL oder durch Aufrufen der `microsoftTeams.getContext()` Funktion im Microsoft Teams-Client-SDK erhalten. Ein böswilliger Akteur könnte Ihre Registerkarteninhalts-URL mit seinen eigenen Parametern aufrufen, und eine Webseite, die Microsoft Teams imitiert, kann die URL Ihres Registerkarteninhalts in einen iframe laden und eigene Daten an die Funktion zurückgeben `getContext()` . Sie sollten die identitätsbezogenen Informationen im Registerkartenkontext lediglich als Hinweise behandeln und diese vor der Verwendung validieren.

## <a name="samples"></a>Beispiele

Beispielcode zum Anzeigen des Registerkarten Authentifizierungsprozesses finden Sie unter:

* [Beispiel für Microsoft Teams-Registerkarten Authentifizierung (Knoten)](https://github.com/OfficeDev/microsoft-teams-sample-complete-node)
* [Microsoft Teams-Registerkarten Authentifizierung (Beispiel) (C#)](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp)

## <a name="more-details"></a>Weitere Details

Eine ausführliche Implementierungs Exemplarische Vorgehensweise für die Registerkarten Authentifizierung für Azure Active Directory finden Sie unter:

* [Authentifizieren eines Benutzers auf einer Microsoft Teams-Registerkarte](~/tabs/how-to/authentication/auth-tab-AAD.md)
* [Automatische Authentifizierung](~/tabs/how-to/authentication/auth-silent-AAD.md)
