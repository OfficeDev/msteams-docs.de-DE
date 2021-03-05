---
title: Authentifizierungsfluss für Registerkarten
description: Beschreibt den Authentifizierungsfluss in Registerkarten
ms.topic: conceptual
keywords: Registerkarten für den Authentifizierungsfluss von Teams
ms.openlocfilehash: ddd9ea1ee907b154005445613fd3d09de2158766
ms.sourcegitcommit: 5cb3453e918bec1173899e7591b48a48113cf8f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2021
ms.locfileid: "50449563"
---
# <a name="microsoft-teams-authentication-flow-for-tabs"></a>Microsoft Teams-Authentifizierungsfluss für Registerkarten

> [!NOTE]
> Damit die Authentifizierung für Ihre Registerkarte auf mobilen Clients funktioniert, müssen Sie sicherstellen, dass Sie mindestens die Version 1.4.1 des Microsoft Teams JavaScript SDK verwenden.
> Das Teams SDK startet ein separates Fenster für den Authentifizierungsfluss. Legen Sie `SameSite` das Attribut auf **Lax .** Der Teams-Desktopclient oder ältere Versionen von Chrome oder Safari unterstützen `SameSite` =None nicht.

OAuth 2.0 ist ein offener Standard für die Authentifizierung und Autorisierung, der von Azure Active Directory (AAD) und vielen anderen Identitätsanbietern verwendet wird. Ein grundlegendes Verständnis von OAuth 2.0 ist eine Voraussetzung für die Arbeit mit der Authentifizierung in Teams. Weitere Informationen finden Sie unter [OAuth 2 simplified](https://aaronparecki.com/oauth-2-simplified/) that is easier to follow than the [formal specification](https://oauth.net/2/). Der Authentifizierungsfluss für Registerkarten und Bots ist unterschiedlich, da Registerkarten Websites ähneln, sodass sie OAuth 2.0 direkt verwenden können. Bots tun einiges anders, aber die Kernkonzepte sind identisch.

Ein Beispiel für den Authentifizierungsfluss für Registerkarten und Bots mit Node und dem [impliziten OAuth 2.0-Erteilungstyp](https://oauth.net/2/grant-types/implicit/)finden Sie unter [Initiieren](~/tabs/how-to/authentication/auth-tab-aad.md#initiate-authentication-flow)des Authentifizierungsflusses für Registerkarten .

> [!NOTE]
> Bevor Sie dem **Benutzer eine Anmeldeschaltfläche** anzeigen und die API als Reaktion auf die Auswahl der Schaltfläche aufrufen, müssen Sie warten, bis die `microsoftTeams.authentication.authenticate` SDK-Initialisierung abgeschlossen ist. Sie können einen Rückruf an die API übergeben, die nach `microsoftTeams.initialize` Abschluss der Initialisierung aufgerufen wird.

![Diagramm der Registerkartenauthentifizierungssequenz](~/assets/images/authentication/tab_auth_sequence_diagram.png)

1. Der Benutzer interagiert mit dem Inhalt auf der Registerkartenkonfiguration oder Inhaltsseite, in der Regel mit der Schaltfläche Anmelden **oder** **Anmelden.**
2. Die Registerkarte erstellt die URL für die Startseite der Authentifizierung. Optional verwendet es Informationen von URL-Platzhaltern oder ruft die Teams-Client-SDK-Methode auf, um die `microsoftTeams.getContext()` Authentifizierungserfahrung für den Benutzer zu optimieren. Wenn der Parameter beispielsweise bei der Authentifizierung mit AAD auf die E-Mail-Adresse des Benutzers festgelegt ist, muss sich der Benutzer nicht anmelden, wenn er dies kürzlich `login_hint` getan hat. Dies liegt daran, dass AAD die zwischengespeicherten Anmeldeinformationen des Benutzers verwendet. Das Popupfenster wird kurz angezeigt und dann nicht mehr angezeigt.
3. Auf der Registerkarte wird dann die `microsoftTeams.authentication.authenticate()`-Methode aufgerufen und die `successCallback`- und die `failureCallback`-Funktion registriert.
4. Teams öffnet die Startseite in einem iframe in einem Popupfenster. Die Startseite generiert zufällige Daten, speichert sie für die zukünftige Überprüfung und leitet sie an den Endpunkt des Identitätsanbieters um, z. B. `state` `/authorize` für Azure `https://login.microsoftonline.com/<tenant ID>/oauth2/authorize` AD. Ersetzen `<tenant id>` Sie durch Ihre eigene Mandanten-ID, die context.tid ist.
Ähnlich wie bei anderen Anwendungsauthentisierungsflüssen in Teams muss sich die Startseite in einer Domäne befinden, die sich in der Liste befindet, und in derselben Domäne wie die Umleitungsseite für die `validDomains` Post-Anmeldung.

    > [!NOTE]
    > Der implizite OAuth 2.0-Grant-Fluss ruft einen Parameter in der Authentifizierungsanforderung auf, der eindeutige Sitzungsdaten enthält, um einen standortübergreifenden Anforderungsfälschungsangriff `state` [zu verhindern.](https://en.wikipedia.org/wiki/Cross-site_request_forgery) In den Beispielen wird eine zufällig generierte GUID für die Daten `state` verwendet.

5. Auf der Website des Anbieters meldet sich der Benutzer an und gewährt Zugriff auf die Registerkarte.
6. Der Anbieter führt den Benutzer mit einem Zugriffstoken zur OAuth 2.0-Umleitungsseite der Registerkarte.
7. Die Registerkarte überprüft, ob der zurückgegebene Wert dem entspricht, was zuvor gespeichert wurde, und ruft auf, wodurch wiederum die in Schritt 3 registrierte `state` `microsoftTeams.authentication.notifySuccess()` Funktion `successCallback` aufruft.
8. Teams schließt das Popupfenster.
9. Auf der Registerkarte wird entweder die Konfigurationsbenutzeroberfläche angezeigt, der Inhalt der Registerkarten wird aktualisiert oder neu geladen, je nachdem, wo der Benutzer angefangen hat.

## <a name="treat-tab-context-as-hints"></a>Behandeln des Registerkartenkontexts als Hinweise

Obwohl der Registerkartenkontext hilfreiche Informationen zum Benutzer enthält, verwenden Sie diese Informationen nicht, um den Benutzer zu authentifizieren. Authentifizieren Sie den Benutzer auch dann, wenn Sie die Informationen als URL-Parameter zu Ihrer Registerkarteninhalts-URL oder durch Aufrufen der Funktion `microsoftTeams.getContext()` im Microsoft Teams-Client-SDK erhalten. Ein böswilliger Akteur kann ihre Registerkarteninhalts-URL mit eigenen Parametern aufrufen. Der Akteur kann auch eine Webseite aufrufen, die die Identität von Microsoft Teams übertrüssig gibt, um ihre Registerkarteninhalts-URL in einem iframe zu laden und eigene Daten an die Funktion `getContext()` zurückzukehren. Sie müssen die identitätsbezogenen Informationen im Registerkartenkontext einfach als Hinweise behandeln und vor der Verwendung überprüfen. Verweisen Sie auf die Notizen im [Navigieren zur Autorisierungsseite von Ihrer Popupseite](~/tabs/how-to/authentication/auth-tab-aad.md#navigate-to-the-authorization-page-from-your-popup-page).

## <a name="samples"></a>Beispiele

Beispielcode, der den Vorgang der Registerkartenauthentifizierung zeigt, finden Sie unter:

* [Beispiel für die Registerkartenauthentifizierung von Teams (Node)](https://github.com/OfficeDev/microsoft-teams-sample-complete-node)
* [Beispiel für die Registerkartenauthentifizierung von Teams (C#)](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp)

## <a name="more-details"></a>Weitere Details

Eine detaillierte Implementierung für die Registerkartenauthentifizierung mit AAD finden Sie unter:

* [Authentifizieren eines Benutzers auf einer Registerkarte "Teams"](~/tabs/how-to/authentication/auth-tab-AAD.md)
* [Automatische Authentifizierung](~/tabs/how-to/authentication/auth-silent-AAD.md)
