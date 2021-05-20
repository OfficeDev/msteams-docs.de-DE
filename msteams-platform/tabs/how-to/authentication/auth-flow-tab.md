---
title: Authentifizierungsfluss für Registerkarten
description: Beschreibt den Authentifizierungsfluss in Registerkarten
ms.topic: conceptual
localization_priority: Normal
keywords: Teams Authentifizierungsflussregisterkarten
ms.openlocfilehash: 1282c149beba0ff5b424585f566a703f48234fa2
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566691"
---
# <a name="microsoft-teams-authentication-flow-for-tabs"></a>Microsoft Teams Authentifizierungsablauf für Registerkarten

> [!NOTE]
> Damit die Authentifizierung für Ihre Registerkarte auf mobilen Clients funktioniert, müssen Sie sicherstellen, dass Sie mindestens die Version 1.4.1 des Microsoft Teams JavaScript SDK verwenden.
> Teams SDK startet ein separates Fenster für den Authentifizierungsfluss. Legen Sie das `SameSite` Attribut auf **Lax** fest. Teams Desktop-Client oder ältere Versionen von Chrome oder Safari unterstützen `SameSite` =Keine.

OAuth 2.0 ist ein offener Standard für die Authentifizierung und Autorisierung, der von Azure Active Directory (AAD) und vielen anderen Identitätsanbietern verwendet wird. Ein grundlegendes Verständnis von OAuth 2.0 ist eine Voraussetzung für die Arbeit mit der Authentifizierung in Teams. Weitere Informationen finden Sie unter [OAuth 2 vereinfacht,](https://aaronparecki.com/oauth-2-simplified/) der einfacher zu befolgen ist als die [formale Spezifikation](https://oauth.net/2/). Der Authentifizierungsfluss für Registerkarten und Bots unterscheidet sich, da Registerkarten Websites ähneln, sodass sie OAuth 2.0 direkt verwenden können. Bots machen ein paar Dinge anders, aber die Kernkonzepte sind identisch.

Ein Beispiel für den Authentifizierungsfluss für Registerkarten und Bots, die Node und den [impliziten Aktivierungstyp OAuth 2.0](https://oauth.net/2/grant-types/implicit/)verwenden, finden Sie unter Initiieren des [Authentifizierungsflusses für Registerkarten](~/tabs/how-to/authentication/auth-tab-aad.md#initiate-authentication-flow).

> [!NOTE]
> Bevor Sie dem Benutzer eine **Login-Schaltfläche** anzeigen und die `microsoftTeams.authentication.authenticate` API als Reaktion auf die Auswahl der Schaltfläche aufrufen, müssen Sie warten, bis die SDK-Initialisierung abgeschlossen ist. Sie können einen Rückruf an die API übergeben, die aufgerufen wird, wenn die `microsoftTeams.initialize` Initialisierung abgeschlossen ist.

![Tabauthentifizierungssequenzdiagramm](~/assets/images/authentication/tab_auth_sequence_diagram.png)

1. Der Benutzer interagiert mit dem Inhalt auf der Registerkartenkonfiguration oder Inhaltsseite, in der Regel eine **Schaltfläche Anmelden** oder **Anmelden.**
2. Die Registerkarte erstellt die URL für die Auth-Startseite. Optional werden Informationen von URL-Platzhaltern oder Aufrufen `microsoftTeams.getContext()` Teams Client-SDK-Methode verwendet, um die Authentifizierung für den Benutzer zu optimieren. Wenn der Parameter z. B. bei der Authentifizierung bei AAD `login_hint` auf die E-Mail-Adresse des Benutzers festgelegt ist, muss er sich nicht anmelden, wenn er dies in letzter Zeit getan hat. Dies liegt daran, dass AAD die zwischengespeicherten Anmeldeinformationen des Benutzers verwendet. Das Popupfenster wird kurz angezeigt und verschwindet dann.
3. Auf der Registerkarte wird dann die `microsoftTeams.authentication.authenticate()`-Methode aufgerufen und die `successCallback`- und die `failureCallback`-Funktion registriert.
4. Teams öffnet die Startseite in einem iframe in einem Popupfenster. Die Startseite generiert zufällige `state` Daten, speichert sie für die zukünftige Validierung und leitet sie zum Endpunkt des Identitätsanbieters um, z. B. `/authorize` für Azure `https://login.microsoftonline.com/<tenant ID>/oauth2/authorize` AD. Ersetzen Sie dies `<tenant id>` durch Ihre eigene Mandanten-ID, die context.tid ist.
Ähnlich wie bei anderen Anwendungsauthentifizierungsflüssen in Teams muss sich die Startseite in einer Domäne befinden, die sich in ihrer `validDomains` Liste befindet, und in derselben Domäne wie die Postzeichen-In-Umleitungsseite.

    > [!NOTE]
    > Der implizite Aktivierungsfluss von OAuth 2.0 ruft einen `state` Parameter in der Authentifizierungsanforderung auf, der eindeutige Sitzungsdaten enthält, um einen [standortübergreifenden Anforderungsfälschungsangriff](https://en.wikipedia.org/wiki/Cross-site_request_forgery)zu verhindern. In den Beispielen wird eine zufällig generierte GUID für die `state` Daten verwendet.

5. Auf der Website des Anbieters meldet sich der Benutzer an und gewährt Zugriff auf die Registerkarte.
6. Der Anbieter führt den Benutzer mit einem Zugriffstoken auf die OAuth 2.0-Umleitungsseite der Registerkarte.
7. Die Registerkarte überprüft, ob der zurückgegebene Wert mit dem `state` übereinstimmt, was zuvor gespeichert wurde, und ruft `microsoftTeams.authentication.notifySuccess()` auf , die wiederum die in Schritt 3 registrierte Funktion `successCallback` aufruft.
8. Teams schließt das Popupfenster.
9. Die Registerkarte zeigt entweder die Konfigurationsbenutzeroberfläche an, aktualisiert oder lädt den Inhalt der Registerkarten neu, je nachdem, von wo aus der Benutzer gestartet hat.

## <a name="treat-tab-context-as-hints"></a>Behandeln des Registerkartenkontexts als Hinweise

Obwohl der Registerkartenkontext hilfreiche Informationen zum Benutzer bereitstellt, verwenden Sie diese Informationen nicht, um den Benutzer zu authentifizieren. Authentifizieren Sie den Benutzer auch dann, wenn Sie die Informationen als URL-Parameter an Ihre Tab-Content-URL abrufen oder die `microsoftTeams.getContext()` Funktion im Microsoft Teams Client-SDK aufrufen. Ein böswilliger Akteur kann Ihre Tab-Inhalts-URL mit eigenen Parametern aufrufen. Der Akteur kann auch eine Webseite aufrufen, die die Identität Microsoft Teams angibt, um die TAB-Inhalts-URL in einen iframe zu laden und eigene Daten an die `getContext()` Funktion zurückzugeben. Sie müssen die identitätsbezogenen Informationen im Registerkartenkontext einfach als Hinweise behandeln und sie vor der Verwendung überprüfen. Lesen Sie die Hinweise in [Navigieren zur Autorisierungsseite von Ihrer Popup-Seite](~/tabs/how-to/authentication/auth-tab-aad.md#navigate-to-the-authorization-page-from-your-popup-page).

## <a name="code-sample"></a>Codebeispiel

Beispielcode, der den Tabauthentifizierungsprozess anzeigt:

| **Beispielname** | **Beschreibung** | **C#** | **Node.js** |
|-----------------|-----------------|-------------|------------|
| Teams-Registerkartenauthentifizierung | Authentifizierungsprozess für Registerkarten mit AAD. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-complete-sample/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-complete-sample/nodejs) |

## <a name="more-details"></a>Weitere Informationen

Eine detaillierte Implementierung für die Tab-Authentifizierung mit AAD finden Sie unter:

* [Authentifizieren eines Benutzers auf einer Teams Registerkarte](~/tabs/how-to/authentication/auth-tab-AAD.md)
* [Automatische Authentifizierung](~/tabs/how-to/authentication/auth-silent-AAD.md)
