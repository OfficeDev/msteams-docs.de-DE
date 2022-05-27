---
title: Authentifizierungsablauf für Registerkarten
description: In diesem Artikel werden der Authentifizierungsablauf in Registerkarten, OAuth durch Azure AD beschrieben und Codebeispiele bereitgestellt.
ms.topic: conceptual
ms.localizationpriority: medium
keywords: Registerkarten Microsoft Teams-Authentifizierungsablauf
ms.openlocfilehash: a40a09b025949b36491534a4e8bdda9f523b24df
ms.sourcegitcommit: eeaa8cbb10b9dfa97e9c8e169e9940ddfe683a7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2022
ms.locfileid: "65756492"
---
# <a name="microsoft-teams-authentication-flow-for-tabs"></a>Microsoft Teams-Authentifizierungsablauf für Registerkarten

> [!NOTE]
> Damit die Authentifizierung für Ihre Registerkarte auf mobilen Clients funktioniert, müssen Sie sicherstellen, dass Sie mindestens die Version 1.4.1 des Microsoft Teams JavaScript-SDK verwenden.  
> Das Microsoft Teams SDK startet ein separates Fenster für den Authentifizierungsablauf. Legen Sie das `SameSite`-Attribut auf **Lax** fest. Microsoft Teams-Desktopclients oder ältere Versionen von Chrome oder Safari unterstützen `SameSite`=None nicht.

OAuth 2.0 ist ein offener Standard für Authentifizierung und Autorisierung, der von Microsoft Azure Active Directory (Azure AD) und vielen anderen Identitätsanbietern verwendet wird. Ein grundlegendes Verständnis von OAuth 2.0 ist Voraussetzung für die Arbeit mit der Authentifizierung in Microsoft Teams. Siehe [OAuth 2 Simplified](https://aaronparecki.com/oauth-2-simplified/) für weitere Informationen, das einfacher zu befolgen ist als die [formale Spezifikation](https://oauth.net/2/). Der Authentifizierungsablauf unterscheidet sich für Registerkarten und Bots, da Registerkarten Websites ähneln und OAuth 2.0 hier somit direkt verwendet werden kann. Bots führen einige Dinge anders aus, aber die Kernkonzepte sind dieselben.

Den Authentifizierungsablauf für Registerkarten und Bots, bei denen Node und der [impliziten OAuth 2.0-Genehmigungstyp](https://oauth.net/2/grant-types/implicit/) verwendet werden, finden Sie unter [Initiieren des Authentifizierungsablaufes für Registerkarten](~/tabs/how-to/authentication/auth-tab-aad.md#initiate-authentication-flow).

> [!NOTE]
> Bevor dem Benutzer eine **Anmeldeschaltfläche** angezeigt und die `microsoftTeams.authentication.authenticate`-API als Reaktion auf das Anklicken der Schaltfläche aufgerufen wird, muss gewartet werden, bis die SDK-Initialisierung abgeschlossen ist. Sie können einen Callback an die `microsoftTeams.initialize`-API übergeben, die aufgerufen wird, wenn die Initialisierung abgeschlossen ist.

![Darstellung der Sequenz bei der Registerkartenauthentifizierung](~/assets/images/authentication/tab_auth_sequence_diagram.png)

1. Der Benutzer interagiert mit dem Inhalt auf der Registerkartenkonfigurations- oder Inhaltsseite, in der Regel eine **Anmelde**- oder **Login**-Schaltfläche.
2. Die Registerkarte erstellt die URL für die Authentifizierungsstartseite. Optional werden Informationen aus URL-Platzhaltern verwendet oder die Microsoft Teams Client SDK-Methode `microsoftTeams.getContext()` aufgerufen, um den Authentifizierungsablauf für den Benutzer zu optimieren. Wenn z. B. bei der Authentifizierung mit A Azure AD der `login_hint` Parameter auf die E-Mail-Adresse des Benutzers festgelegt ist, muss sich der Benutzer nicht anmelden, wenn er dies kürzlich getan hat. Dies liegt daran, dass Azure AD die zwischengespeicherten Anmeldeinformationen des Benutzers verwendet. Das Popupfenster wird kurz angezeigt und dann ausgeblendet.
3. Auf der Registerkarte wird dann die `microsoftTeams.authentication.authenticate()`-Methode aufgerufen und die `successCallback`- und die `failureCallback`-Funktion registriert.
4. Microsoft Teams öffnet die Startseite in einem iFrame in einem Popupfenster. Die Startseite generiert zufällige `state`-Daten, speichert sie für die zukünftige Überprüfung und leitet sie zum `/authorize`-Endpunkt des Identitätsanbieters um, z. B. `https://login.microsoftonline.com/<tenant ID>/oauth2/authorize` für Azure AD. Ersetzen Sie `<tenant id>` durch Ihre eigene Mandanten-ID "context.tid".
Ähnlich wie bei anderen Authentifizierungsabläufen für Anwendungen in Microsoft Teams muss sich die Startseite in einer Domäne befinden, die in der `validDomains`-Liste enthalten ist, und sich in derselben Domäne wie die Umleitungsseite nach der Anmeldung befinden.

    > [!NOTE]
    > Beim Ablauf der impliziten OAuth 2.0-Genehmigung wird ein `state`-Parameter in der Authentifizierungsanforderung aufgerufen, der eindeutige Sitzungsdaten enthält, um einen [Angriff mittels websiteübergreifenden Anforderungsfälschungen](https://en.wikipedia.org/wiki/Cross-site_request_forgery) zu verhindern. In den Beispielen wird eine zufällig generierte GUID für die `state`-Daten verwendet.

5. Auf der Website des Anbieters meldet sich der Benutzer an und gewährt Zugriff auf die Registerkarte.
6. Der Anbieter leitet den Benutzer mit einem Zugriffstoken zur OAuth-2.0-Umleitungsseite der Registerkarte weiter.
7. Die Registerkarte überprüft, ob der zurückgegebene `state`-Wert mit jenem übereinstimmt, der zuvor gespeichert wurde, und ruft `microsoftTeams.authentication.notifySuccess()` auf, wodurch wiederum die in Schritt 3 registrierte `successCallback`-Funktion aufgerufen wird.
8. Microsoft Teams schließt das Popupfenster.
9. Auf der Registerkarte wird entweder die Konfigurationsbenutzeroberfläche angezeigt, oder es werden die Inhalte der Registerkarte aktualisiert oder neu geladen, je nachdem, wo der Benutzer begonnen hat.

> [!NOTE]
> Wenn die Anwendung SAML-SSO unterstützt, kann das auf der Registerkarte über SSO generierte JWT-Token nicht verwendet werden, da es nicht unterstützt wird.

## <a name="treat-tab-context-as-hints"></a>Registerkartenkontexte als Hinweise behandeln

Obwohl der Registerkartenkontext hilfreiche Informationen zum Benutzer bereitstellt, verwenden Sie diese Informationen nicht, um den Benutzer zu authentifizieren. Authentifizieren Sie den Benutzer auch dann, wenn Sie die Informationen als URL-Parameter zu Ihrer Registerkarteninhalts-URL erhalten oder indem Sie die `microsoftTeams.getContext()`-Funktion im Microsoft Teams-Client-SDK aufrufen. Ein böswilliger Akteur kann Ihre URL für Registerkarteninhalte mit eigenen Parametern aufrufen. Er kann auch eine Webseite aufrufen, die sich als Microsoft Teams ausgibt, um die URL der Registerkarteninhalte in einem iFrame zu laden und seine eigenen Daten an die `getContext()`-Funktion zurückzugeben. Sie müssen die identitätsbezogenen Informationen im Registerkartenkontext als Hinweis behandeln und vor der Verwendung validieren. Lesen Sie dazu die Anmerkungen in [Von Ihrer Popupseite zur Autorisierungsseite navigieren](~/tabs/how-to/authentication/auth-tab-aad.md#navigate-to-the-authorization-page-from-your-pop-up-page).

## <a name="code-sample"></a>Codebeispiel

Beispielcode mit dem Registerkartenauthentifizierungsprozess:

| **Beispielname** | **Beschreibung** | **C#** | **Node.js** |
|-----------------|-----------------|-------------|------------|
| Microsoft Teams-Registerkartenauthentifizierung | Authentifizierungsprozess für Registerkarten mit Azure AD. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-complete-sample/csharp) | [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-complete-sample/nodejs) |

## <a name="see-also"></a>Siehe auch

Informationen für eine detaillierte Implementierung der Registerkartenauthentifizierung mithilfe von Azure AD finden Sie unter:

* [Authentifizieren eines Benutzers über eine Microsoft Teams-Registerkarte](~/tabs/how-to/authentication/auth-tab-AAD.md)
* [Automatische Authentifizierung](~/tabs/how-to/authentication/auth-silent-AAD.md)
