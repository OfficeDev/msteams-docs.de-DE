---
title: Problembehandlung bei der Authentifizierung für Registerkarten mit SSO in Teams
description: Behandeln von Problemen mit der SSO-Authentifizierung (Single Sign-On) in Teams und deren Verwendung in der Registerkarten-App.
ms.topic: how-to
ms.localizationpriority: high
keywords: Fragen zu SSO-Fehlern bei Teams-Authentifizierungsregisterkarten in Microsoft Azure Active Directory (Azure AD)
ms.openlocfilehash: 8396b42c217ea58a0a4709e1dbd8580da32da991
ms.sourcegitcommit: 82c585d287d61924ce3a3bba3e9caeff35c9a27a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2022
ms.locfileid: "67586896"
---
# <a name="troubleshoot-sso-authentication-in-teams"></a>Fehlerbehebung bei der SSO-Authentifizierung in Teams

Hier ist eine Liste von Problemen und Fragen zu SSO und wie Sie diese beheben können.
<br>

## <a name="support-for-microsoft-graph"></a>Unterstützung für Microsoft Graph

<br>
<details>
<summary>1. Funktioniert die Graph-API in Postman?</summary>
<br>
Sie können die Microsoft Graph Postman-Sammlung für den Einstieg in Microsoft Graph-APIs verwenden.

Weitere Informationen finden Sie unter [Verwenden von Postman mit einer Microsoft Graph-API](/graph/use-postman).
</details>
<br>
<details>
<summary>2. Funktioniert die Graph-API im Microsoft Graph-Explorer?</summary>
<br>
Ja, die Graph-API funktioniert im Microsoft Graph-Explorer.

Weitere Informationen finden Sie unter [Graph-API](https://developer.microsoft.com/graph/graph-explorer).

</details>
<br>

## <a name="error-messages-and-how-to-handle-them"></a>Fehlermeldungen und deren Behandlung

<br>
<details>
<summary>1. Fehler: Zustimmung fehlt.</summary>
<br>
Wenn Azure AD eine Anforderung für den Zugriff auf eine Microsoft Graph-Ressource erhält, wird überprüft, ob der Benutzer (oder Mandantenadministrator) seine Zustimmung für diese Ressource erteilt hat. Wenn kein Datensatz für die Zustimmung des Benutzers oder Administrators vorhanden ist, sendet Azure AD eine Fehlermeldung an Ihren Webdienst.

Ihr Code muss dem Client (z. B. im Textkörper einer 403 Forbidden-Antwort) mitteilen, wie der Fehler behandelt werden soll:

- Wenn die Registerkarten-App Microsoft Graph-Bereiche benötigt, für die nur ein Administrator seine Zustimmung geben kann, sollte ihr Code einen Fehler generieren.
- Wenn die einzigen Bereiche, die benötigt werden, vom Benutzer zugewiesen werden können, sollte Ihr Code auf ein alternatives System zur Benutzerauthentifizierung zurückgreifen.

</details>
<br>
<details>
<summary>2. Fehler: Fehlender Bereich (Berechtigung).</summary>
<br>
Dieser Fehler wird nur während der Entwicklung angezeigt.

Um diesen Fehler zu behandeln, sollte Ihr serverseitiger Code eine 403 Forbidden-Antwort an den Client senden. Er sollte den Fehler in der Konsole protokollieren oder in einem Protokoll aufzeichnen.
</details>
<br>
<details>
<summary>3. Fehler: Ungültige Benutzergruppe im Zugriffstoken für Microsoft Graph.</summary>
<br>
Der serverseitige Code sollte eine 403 Forbidden-Antwort an den Client senden, um dem Benutzer eine Nachricht anzuzeigen. Es wird empfohlen, den Fehler auch in der Konsole zu protokollieren oder in einem Protokoll aufzuzeichnen.
</details>
<br>
<details>
<summary>4. Fehler: Der Hostname darf nicht auf einer bereits im Besitz befindlichen Domäne basieren.</summary>
<br>
Sie können diesen Fehler in einem der beiden Szenarien erhalten:

1. Die benutzerdefinierte Domäne wird Azure AD nicht hinzugefügt. Um Azure AD eine benutzerdefinierte Domäne hinzuzufügen und zu registrieren, folgen [Sie dem Hinzufügen eines benutzerdefinierten Domänennamens zum Azure AD-Verfahren](/azure/active-directory/fundamentals/add-custom-domain), und führen Sie dann erneut die Schritte zum [Konfigurieren des Zugriffstokenbereichs](tab-sso-register-aad.md#configure-scope-for-access-token) aus.
1. Sie sind nicht mit Administratoranmeldeinformationen im Microsoft 365-Mandanten angemeldet. Melden Sie sich bei Microsoft 365 als Administrator an.

</details>
<br>
<details>
<summary>5. Fehler: Der Benutzerprinzipalname (UPN) wurde im zurückgegebenen Zugriffstoken nicht empfangen.</summary>
<br>
Sie können UPN als optionalen Anspruch in Azure AD hinzufügen.

Weitere Informationen finden Sie unter [Bereitstellen optionaler Ansprüche für Ihre App](/azure/active-directory/develop/active-directory-optional-claims) und [Zugriffstoken](/azure/active-directory/develop/access-tokens).
</details>
<br>
<details>
<summary>6. Fehler: Teams SDK-Fehler: resourceDisabled.</summary>
<br>
Um diesen Fehler zu vermeiden, stellen Sie sicher, dass die Anwendungs-ID des URI in Azure AD App-Registrierung und in Ihrem Teams-Client ordnungsgemäß konfiguriert ist.

Weitere Informationen zur Anwendungs-ID des URI finden Sie unter [So machen Sie eine API verfügbar](tab-sso-register-aad.md#to-expose-an-api).

</details>
<br>

<details>
<summary>7. Fehler: Allgemeiner Fehler beim Ausführen der Registerkarten-App.</summary>
<br>
Ein allgemeiner Fehler kann angezeigt werden, wenn eine oder mehrere der in Azure AD vorgenommenen App-Konfigurationen falsch sind. Um diesen Fehler zu beheben, überprüfen Sie, ob die in Ihrem Code und Teams-Manifest konfigurierten App-Details den Werten in Azure AD entsprechen.

Die folgende Abbildung zeigt ein Beispiel für die in Azure AD konfigurierten App-Details.

:::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/azure-app-details.png" alt-text="App-Konfigurationswerte in Azure AD":::

Überprüfen Sie, ob die folgenden Werte zwischen Azure AD, clientseitigem Code und dem App-Manifest von Teams übereinstimmen:

- **App-ID**: Die App-ID, die Sie in Azure AD generiert haben, sollte im Code und in der Teams-Manifestdatei identisch sein. Überprüfen Sie, ob die App-ID im Teams-Manifest der **Anwendungs (Client)-ID** in Azure AD entspricht.

- **Geheimer App-Schlüssel**: Der im Back-End Ihrer App konfigurierte App-Schlüssel sollte mit den **Clientanmeldeinformationen** in Azure AD identisch sein.
    Sie sollten auch überprüfen, ob der geheime Clientschlüssel abgelaufen ist.

- **Anwendungs-ID-URI**: Der App-ID-URI im Code und in der Manifestdatei der Teams-App sollte mit dem **Anwendungs-ID-URI** in Azure AD übereinstimmen.

- **App-Berechtigungen**: Überprüfen Sie, ob die Berechtigungen, die Sie im Bereich definiert haben, Ihren App-Anforderungen entsprechen. Wenn ja, überprüfen Sie, ob sie dem Benutzer im Zugriffstoken gewährt wurden.

- **Administratorzustimmung**: Wenn für einen Bereich eine Administratorzustimmung erforderlich ist, überprüfen Sie, ob die Zustimmung für den betreffenden Bereich dem Benutzer erteilt wurde.

Überprüfen Sie außerdem das Zugriffstoken, das an die Registerkarten-App gesendet wurde, um zu überprüfen, ob die folgenden Werte korrekt sind:

- **Zielgruppe (aud):** Überprüfen Sie, ob die App-ID im Token korrekt ist, wie in Azure AD angegeben.
- **Mandanten-ID(tid)**: Überprüfen Sie, ob der im Token erwähnte Mandant korrekt ist.
- **Benutzeridentität (preferred_username)**: Überprüfen Sie, ob die Benutzeridentität dem Benutzernamen in der Anforderung des Zugriffstokens für den Bereich entspricht, auf den der aktuelle Benutzer zugreifen möchte.
- **Bereiche (scp)**: Überprüfen Sie, ob der Bereich, für den das Zugriffstoken angefordert wird, korrekt und wie in Azure AD definiert ist.
- **Azure AD Version 1.0 oder 2.0 (ver)**: Überprüfen Sie, ob die Azure AD-Version korrekt ist.

Sie können [JWT](https://jwt.ms) für die Überprüfung des Tokens verwenden.

</details>
