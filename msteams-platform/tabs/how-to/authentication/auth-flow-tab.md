---
title: Authentifizierungsfluss für Registerkarten
description: Beschreibt den Authentifizierungsfluss in Registerkarten, OAuth nach Azure AD und stellt Codebeispiele bereit.
ms.topic: conceptual
ms.localizationpriority: medium
keywords: Registerkarten des Teams-Authentifizierungsflusses
ms.openlocfilehash: a4d6c184ca0747a2b0328e0194ebad472e9dfa6e
ms.sourcegitcommit: 90587b1ec04bf20d716ed6feb8ccca4313e87f8c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/10/2022
ms.locfileid: "62518296"
---
# <a name="microsoft-teams-authentication-flow-for-tabs"></a>Microsoft Teams Authentifizierungsfluss für Registerkarten

> [!NOTE]
> Damit die Authentifizierung für Ihre Registerkarte auf mobilen Clients funktioniert, müssen Sie sicherstellen, dass Sie mindestens version 1.4.1 des Microsoft Teams JavaScript SDK verwenden.  
> Teams SDK startet ein separates Fenster für den Authentifizierungsfluss. Legen Sie das `SameSite` Attribut auf **"Lax" fest**. Teams Desktopclient oder ältere Versionen von Chrome oder Safari unterstützen `SameSite`keine.

OAuth 2.0 ist ein offener Standard für die Authentifizierung und Autorisierung, der von Microsoft Azure Active Directory (Azure AD) und vielen anderen Identitätsanbietern verwendet wird. Ein grundlegendes Verständnis von OAuth 2.0 ist eine Voraussetzung für die Arbeit mit der Authentifizierung in Teams. Weitere Informationen finden Sie unter ["Vereinfachter OAuth 2](https://aaronparecki.com/oauth-2-simplified/) ",der einfacher zu befolgen ist als die [formale Spezifikation](https://oauth.net/2/). Der Authentifizierungsfluss für Registerkarten und Bots unterscheidet sich, da Registerkarten Websites ähneln, sodass sie OAuth 2.0 direkt verwenden können. Bots führen einige Dinge anders aus, aber die Kernkonzepte sind identisch.

For example, the authentication flow for tabs and bots using Node and the [OAuth 2.0 implicit grant type](https://oauth.net/2/grant-types/implicit/), see [initiate authentication flow for tabs](~/tabs/how-to/authentication/auth-tab-aad.md#initiate-authentication-flow).

> [!NOTE]
> Bevor Sie dem Benutzer eine **Anmeldeschaltfläche** anzeigen und die `microsoftTeams.authentication.authenticate` API als Reaktion auf die Auswahl der Schaltfläche aufrufen, müssen Sie warten, bis die SDK-Initialisierung abgeschlossen ist. Sie können einen Rückruf an die API übergeben, die `microsoftTeams.initialize` aufgerufen wird, wenn die Initialisierung abgeschlossen ist.

![Diagramm der Tab-Authentifizierungssequenz](~/assets/images/authentication/tab_auth_sequence_diagram.png)

1. Der Benutzer interagiert mit dem Inhalt auf der Registerkartenkonfigurations- oder Inhaltsseite, in der Regel einer Anmelde **-** oder **Anmeldeschaltfläche** .
2. Die Registerkarte erstellt die URL für die Authentifizierungsstartseite. Optional werden Informationen von URL-Platzhaltern oder Aufrufen `microsoftTeams.getContext()` Teams Client SDK-Methode verwendet, um die Authentifizierung für den Benutzer zu optimieren. Wenn beispielsweise bei der Authentifizierung mit A Microsoft Azure Active Directory (Azure AD) der `login_hint` Parameter auf die E-Mail-Adresse des Benutzers festgelegt ist, muss sich der Benutzer nicht anmelden, wenn er dies kürzlich getan hat. Dies liegt daran, dass Microsoft Azure Active Directory (Azure AD) die zwischengespeicherten Anmeldeinformationen des Benutzers verwendet. Das Popupfenster wird kurz angezeigt und dann ausgeblendet.
3. Auf der Registerkarte wird dann die `microsoftTeams.authentication.authenticate()`-Methode aufgerufen und die `successCallback`- und die `failureCallback`-Funktion registriert.
4. Teams öffnet die Startseite in einem iFrame in einem Popupfenster. Die Startseite generiert zufällige `state` Daten, speichert sie für die zukünftige Überprüfung und leitet zum Endpunkt des Identitätsanbieters `/authorize` um, z`https://login.microsoftonline.com/<tenant ID>/oauth2/authorize`. B. für Microsoft Azure Active Directory (Azure AD). Ersetzen Sie `<tenant id>` diese durch Ihre eigene Mandanten-ID context.tid.
Ähnlich wie bei anderen Anwendungsauthentifizierungsflüssen in Teams muss sich die Startseite in einer Domäne befinden, die sich in `validDomains` der Liste befindet, und in derselben Domäne wie die Umleitungsseite nach der Anmeldung.

    > [!NOTE]
    > Der implizite OAuth 2.0-Genehmigungsfluss ruft einen `state` Parameter in der Authentifizierungsanforderung auf, der eindeutige Sitzungsdaten enthält, um einen [websiteübergreifenden Angriff auf Anforderungsfälscher](https://en.wikipedia.org/wiki/Cross-site_request_forgery) zu verhindern. In den Beispielen wird eine zufällig generierte GUID für die `state` Daten verwendet.

5. Auf der Website des Anbieters anmeldet sich der Benutzer und gewährt Zugriff auf die Registerkarte.
6. Der Anbieter führt den Benutzer mit einem Zugriffstoken zur OAuth 2.0-Umleitungsseite der Registerkarte.
7. Die Registerkarte überprüft, ob der zurückgegebene `state` Wert mit dem übereinstimmt, was zuvor gespeichert wurde, und ruft `microsoftTeams.authentication.notifySuccess()`auf, wodurch wiederum die `successCallback` in Schritt 3 registrierte Funktion aufgerufen wird.
8. Teams schließt das Popupfenster.
9. Die Registerkarte zeigt entweder die Konfigurationsbenutzeroberfläche an, aktualisiert oder lädt den Inhalt der Registerkarten neu, je nachdem, wo der Benutzer begonnen hat.

## <a name="treat-tab-context-as-hints"></a>Behandeln des Registerkartenkontexts als Hinweise

Obwohl der Registerkartenkontext hilfreiche Informationen zum Benutzer bereitstellt, verwenden Sie diese Informationen nicht, um den Benutzer zu authentifizieren. Authentifizieren Sie den Benutzer auch dann, wenn Sie die Informationen als URL-Parameter für die URL des Registerkarteninhalts abrufen oder indem Sie die `microsoftTeams.getContext()` Funktion im Microsoft Teams Client-SDK aufrufen. Ein böswilliger Akteur kann ihre URL für Registerkarteninhalte mit eigenen Parametern aufrufen. Der Akteur kann auch eine Webseite aufrufen, die die Identität Microsoft Teams angibt, um die URL des Registerkarteninhalts in einem iframe zu laden und eigene Daten an die `getContext()` Funktion zurückzugeben. Sie müssen die identitätsbezogenen Informationen im Registerkartenkontext als Hinweis behandeln und vor der Verwendung überprüfen. Lesen Sie die Hinweise in [der Navigation zur Autorisierungsseite von Ihrer Popupseite aus](~/tabs/how-to/authentication/auth-tab-aad.md#navigate-to-the-authorization-page-from-your-pop-up-page).

## <a name="code-sample"></a>Codebeispiel

Beispielcode für den Vorgang der Registerkartenauthentifizierung:

| **Beispielname** | **Beschreibung** | **C#** | **Node.js** |
|-----------------|-----------------|-------------|------------|
| Teams Registerkartenauthentifizierung | Authentifizierungsprozess für Registerkarten mit Microsoft Azure Active Directory (Azure AD). | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-complete-sample/csharp) | [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-complete-sample/nodejs) |

## <a name="see-also"></a>Siehe auch

Eine ausführliche Implementierung für die Registerkartenauthentifizierung mit Microsoft Azure Active Directory (Azure AD) finden Sie unter:

* [Authentifizieren eines Benutzers auf einer Teams Registerkarte](~/tabs/how-to/authentication/auth-tab-AAD.md)
* [Automatische Authentifizierung](~/tabs/how-to/authentication/auth-silent-AAD.md)
