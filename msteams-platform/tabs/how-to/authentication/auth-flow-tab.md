---
title: Authentifizierungsfluss für Registerkarten
description: Beschreibt den Authentifizierungsfluss auf Registerkarten
ms.topic: conceptual
keywords: Registerkarten für den Authentifizierungsfluss von Teams
ms.openlocfilehash: 9505419a6594529bcf8d19a90d029705e573c67b
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014586"
---
# <a name="microsoft-teams-authentication-flow-for-tabs"></a>Microsoft Teams-Authentifizierungsfluss für Registerkarten

> [!Note]
> Damit die Authentifizierung für Ihre Registerkarte auf mobilen Clients funktioniert, müssen Sie sicherstellen, dass Sie mindestens die Version 1.4.1 des JavaScript SDK für Teams verwenden.
> Das Teams SDK startet ein separates Fenster für den Authentifizierungsfluss, und daher kann dasselbe Standortattribut auf "Lax" festgelegt werden. Derzeit wird SameSite=None vom Desktopclient von Teams oder älteren Versionen von Chrome oder Safari nicht unterstützt.

OAuth 2.0 ist ein offener Standard für die Authentifizierung und Autorisierung, der von Azure AD und vielen anderen Identitätsanbietern verwendet wird. Ein grundlegendes Verständnis von OAuth 2.0 ist eine Voraussetzung für die Arbeit mit der Authentifizierung in Teams; [Hier finden Sie eine gute Übersicht,](https://aaronparecki.com/oauth-2-simplified/) die einfacher zu befolgen ist als die [formale Spezifikation.](https://oauth.net/2/) Der Authentifizierungsfluss für Registerkarten und Bots ist etwas anders, da Registerkarten Websites sehr ähnlich sind, sodass sie OAuth 2.0 direkt verwenden können. Bots sind nicht und müssen einige Dinge anders tun, aber die Kernkonzepte sind identisch.

*Unter* ["Initiieren des Authentifizierungsflusses](~/tabs/how-to/authentication/auth-tab-aad.md#initiate-authentication-flow) für Registerkarten" finden Sie ein Beispiel für den Authentifizierungsfluss für Registerkarten und Bots, die Node und den impliziten [OAuth 2.0-Gewährungstyp verwenden.](https://oauth.net/2/grant-types/implicit/)

![Diagramm der Registerkartenauthentifizierungssequenz](~/assets/images/authentication/tab_auth_sequence_diagram.png)

1. Der Benutzer interagiert mit dem Inhalt auf der Registerkartenkonfiguration oder Inhaltsseite, in der Regel eine Schaltfläche mit der Bezeichnung "Anmelden" oder "Anmelden".
2. Die Registerkarte erstellt die URL für die Startseite der Authentifizierung, optional mithilfe von Informationen von URL-Platzhaltern oder durch Aufrufen der Teams-Client-SDK-Methode, um die Authentifizierungserfahrung für den Benutzer `microsoftTeams.getContext()` zu optimieren. Wenn der Parameter beispielsweise bei der Authentifizierung mit Azure AD auf die E-Mail-Adresse des Benutzers festgelegt ist, muss sich der Benutzer möglicherweise nicht einmal anmelden, wenn er dies kürzlich getan hat, da Azure AD die zwischengespeicherten Anmeldeinformationen des Benutzers nach Möglichkeit verwendet: Das Popup blinkt kurz und verschwindet `login_hint` dann.
3. Auf der Registerkarte wird dann die `microsoftTeams.authentication.authenticate()`-Methode aufgerufen und die `successCallback`- und die `failureCallback`-Funktion registriert.
4. Teams öffnet die Startseite in einem iframe in einem Popupfenster. Die Startseite generiert zufällige Daten, speichert sie für die zukünftige Überprüfung und leitet sie an den Endpunkt des Identitätsanbieters um, z. B. `state` `/authorize` für Azure `https://login.microsoftonline.com/<tenant ID>/oauth2/authorize` AD. Ersetzen `<tenant id>` Sie diese durch Ihre eigene Mandanten-ID (context.tid).
    * Wie bei anderen Authentifizierungsflüssen in Teams muss sich die Startseite in einer Domäne befinden, die sich in ihrer Liste und in derselben Domäne wie die Umleitungsseite nach der Anmeldung `validDomains` befinden.
    * **WICHTIG:** Der implizite OAuth 2.0-Genehmigungsfluss ruft einen Parameter in der Authentifizierungsanforderung auf, der eindeutige Sitzungsdaten enthält, um einen angriffsübergreifenden Angriff auf `state` Anforderungsfälscher [zu verhindern.](https://en.wikipedia.org/wiki/Cross-site_request_forgery) In den folgenden Beispielen wird eine zufällig generierte GUID für die Daten `state` verwendet.
5. Auf der Website des Anbieters meldet sich der Benutzer an und gewährt Zugriff auf die Registerkarte.
6. Der Anbieter leitet den Benutzer mit einem Zugriffstoken zur OAuth 2.0-Umleitungsseite der Registerkarte.
7. Die Registerkarte überprüft, ob der zurückgegebene Wert dem entspricht, was zuvor gespeichert wurde, und ruft auf, wodurch wiederum die in Schritt 3 registrierte `state` `microsoftTeams.authentication.notifySuccess()` Funktion `successCallback` aufruft.
8. Teams schließt das Popupfenster.
9. Auf der Registerkarte wird entweder die Konfigurationsbenutzeroberfläche angezeigt oder der Inhalt der Registerkarten aktualisiert oder neu geladen, je nachdem, wo der Benutzer begonnen hat.

## <a name="treat-tab-context-as-hints"></a>Behandeln des Registerkartenkontexts als Hinweise

Obwohl der Registerkartenkontext hilfreiche Informationen zum Benutzer enthält, sollten Sie diese Informationen nicht verwenden, um den Benutzer zu authentifizieren, unabhängig davon, ob Sie sie als URL-Parameter für Ihre Registerkarteninhalts-URL oder durch Aufrufen der Funktion im `microsoftTeams.getContext()` Microsoft Teams-Client-SDK erhalten. Ein böswilliger Akteur könnte die URL des Registerkarteninhalts mit seinen eigenen Parametern aufrufen, und eine Webseite, die microsoft Teams als Identitätswechsel antsprecht, könnte die URL des Registerkarteninhalts in einem iframe laden und eigene Daten an die Funktion `getContext()` zurückgeben. Sie sollten die identitätsbezogenen Informationen im Registerkartenkontext einfach als Hinweise behandeln und vor der Verwendung überprüfen. Lesen Sie die Hinweise unter [Navigieren zur Autorisierungsseite von Ihrer Popupseite aus.](~/tabs/how-to/authentication/auth-tab-aad.md#navigate-to-the-authorization-page-from-your-popup-page)

## <a name="samples"></a>Beispiele

Beispielcode für den Prozess der Registerkartenauthentifizierung finden Sie unter:

* [Beispiel für die Microsoft Teams-Registerkartenauthentifizierung (Knoten)](https://github.com/OfficeDev/microsoft-teams-sample-complete-node)
* [Beispiel für die Registerkartenauthentifizierung in Microsoft Teams (C#)](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp)

## <a name="more-details"></a>Weitere Details

Eine ausführliche implementierungs exemplarische Vorgehensweise für die Registerkartenauthentifizierung für Azure Active Directory finden Sie unter:

* [Authentifizieren eines Benutzers auf einer Microsoft Teams-Registerkarte](~/tabs/how-to/authentication/auth-tab-AAD.md)
* [Automatische Authentifizierung](~/tabs/how-to/authentication/auth-silent-AAD.md)
