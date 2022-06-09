---
title: Codekonfiguration zum Aktivieren von SSO für Registerkarten
description: Beschreibt die Codekonfiguration zum Aktivieren von SSO für Registerkarten
ms.topic: how-to
ms.localizationpriority: medium
keywords: Teams-Authentifizierungsregisterkarten Microsoft Azure Active Directory (Azure AD) Graph-API
ms.openlocfilehash: 3f095f3e2b0737b7afcdfe3bdcc96bd36d2f3847
ms.sourcegitcommit: e16b51a49756e0fe4eaf239898e28d3021f552da
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2022
ms.locfileid: "65888001"
---
# <a name="add-code-to-enable-sso"></a>Hinzufügen von Code zum Aktivieren von SSO

Bevor Sie Code zum Aktivieren von SSO hinzufügen, stellen Sie sicher, dass Sie Ihre App bei Azure AD registriert haben.

> [!div class="nextstepaction"]
> [Registrieren bei Azure AD](tab-sso-register-aad.md)

Sie müssen den clientseitigen Code Ihrer Registerkarten-App konfigurieren, um ein Zugriffstoken von Azure AD abzurufen. Das Zugriffstoken wird im Namen der Registerkarten-App ausgegeben. Wenn Ihre Registerkarten-App zusätzliche Microsoft Graph-Berechtigungen erfordert, müssen Sie das Zugriffstoken an die serverseitige Seite übergeben und gegen das Microsoft Graph-Token austauschen.

:::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/sso-config-code.png" alt-text="Konfigurieren von Code für die Behandlung von Zugriffstoken" border="false":::

In diesem Abschnitt werden folgende Themen behandelt:

- [Hinzufügen des clientseitigen Codes](#add-client-side-code)
- [Übergeben des Zugriffstokens an serverseitigen Code](#pass-the-access-token-to-server-side-code)
- [Überprüfen des Zugriffstokens](#validate-the-access-token)

## <a name="add-client-side-code"></a>Hinzufügen des clientseitigen Codes

Um App-Zugriff für den aktuellen App-Benutzer zu erhalten, muss Ihr clientseitiger Code Teams aufrufen, um ein Zugriffstoken abzurufen. Sie müssen clientseitigen Code aktualisieren `getAuthToken()` , um den Überprüfungsprozess zu initiieren.

<br>
<details>
<summary>Weitere Informationen zu getAuthToken()</summary>
<br>
`getAuthToken()` ist eine Methode im Microsoft Teams JavaScript SDK. Es fordert ein Azure AD-Zugriffstoken an, das im Auftrag der App ausgestellt wird. Das Token wird aus dem Cache abgerufen, wenn es nicht abgelaufen ist. Wenn es abgelaufen ist, wird eine Anforderung an Azure AD gesendet, um ein neues Zugriffstoken abzurufen.

 Weitere Informationen finden Sie [unter getAuthToken](/javascript/api/@microsoft/teams-js/microsoftteams.authentication?view=msteams-client-js-latest#@microsoft-teams-js-microsoftteams-authentication-getauthtoken&preserve-view=true).
</details>

### <a name="when-to-call-getauthtoken"></a>Wann wird getAuthToken aufgerufen?

Verwenden Sie `getAuthToken()` den Zeitpunkt, zu dem Sie zugriffstoken für den aktuellen App-Benutzer benötigen:

| Wenn ein Zugriffstoken erforderlich ist... | getAuthToken()... |
| --- | --- |
| Wenn der App-Benutzer auf die App zugreift | Von innen `microsoftTeams.initialize()`. |
| So verwenden Sie eine bestimmte Funktionalität der App | Wenn der App-Benutzer eine Aktion ausführt, für die eine Anmeldung erforderlich ist. |

### <a name="add-code-for-getauthtoken"></a>Hinzufügen von Code für getAuthToken

Fügen Sie der Registerkarten-App JavaScript-Codeausschnitt hinzu, um:

- Aufrufen von `getAuthToken()`
- Analysieren Sie das Zugriffstoken, oder übergeben Sie es an den serverseitigen Code.

Der folgende Codeausschnitt zeigt ein Beispiel für das Aufrufen `getAuthToken()`von .

```javascript
microsoftTeams.initialize();
var authTokenRequest = {
  successCallback: function(result) { console.log("Success: " + result); },
  failureCallback: function(error) { console.log("Error getting token: " + error); }
};
microsoftTeams.authentication.getAuthToken(authTokenRequest);
```

Sie können Aufrufe aller `getAuthToken()` Funktionen und Handler hinzufügen, die eine Aktion initiieren, in der das Token benötigt wird.

<br>
<details>
<summary>Hier ist ein Beispiel für den clientseitigen Code:</summary>

:::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/config-client-code.png" alt-text="Konfigurieren von Clientcode" lightbox="../../../assets/images/authentication/teams-sso-tabs/config-client-code.png":::

</details>

Wenn Teams das Zugriffstoken empfängt, wird es zwischengespeichert und nach Bedarf wiederverwendet. Dieses Token kann verwendet werden, wenn `getAuthToken()` es aufgerufen wird, bis es abläuft, ohne einen weiteren Aufruf von Azure AD auszuführen.

> [!IMPORTANT]
> Als bewährte Methode für die Sicherheit des Zugriffstokens:
>
> - Rufen `getAuthToken()` Sie immer nur auf, wenn Sie ein Zugriffstoken benötigen.
> - Teams speichert das Zugriffstoken für Sie zwischen. Speichern Sie sie nicht zwischen, oder speichern Sie sie nicht im Code Ihrer App.

### <a name="consent-dialog-for-getting-access-token"></a>Zustimmungsdialogfeld zum Abrufen des Zugriffstokens

Wenn Sie aufrufen `getAuthToken()` und die Zustimmung des App-Benutzers für Berechtigungen auf Benutzerebene erforderlich ist, wird dem aktuell angemeldeten App-Benutzer ein Azure AD-Dialogfeld angezeigt.

:::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/tabs-sso-prompt.png" alt-text="Eingabeaufforderung für einmaliges Anmelden auf Registerkarten":::

Das angezeigte Zustimmungsdialogfeld gilt für open-ID-Bereiche, die in Azure AD definiert sind. Der App-Benutzer muss seine Zustimmung nur einmal erteilen. Nach der Zustimmung kann der App-Benutzer auf Ihre Registerkarten-App für die erteilten Berechtigungen und Bereiche zugreifen und diese verwenden.

> [!IMPORTANT]
> Szenarien, in denen Keine Zustimmungsdialogfelder erforderlich sind:
>
> - Wenn der Mandantenadministrator die Zustimmung im Namen des Mandanten erteilt hat, müssen App-Benutzer überhaupt nicht zur Zustimmung aufgefordert werden. Dies bedeutet, dass die App-Benutzer die Zustimmungsdialogfelder nicht sehen und nahtlos auf die App zugreifen können.
> - Wenn Ihre Azure AD-App in demselben Mandanten registriert ist, von dem aus Sie eine Authentifizierung in Teams anfordern, kann der App-Benutzer nicht zur Zustimmung aufgefordert werden und erhält sofort ein Zugriffstoken. App-Benutzer stimmen diesen Berechtigungen nur zu, wenn die Azure AD-App in einem anderen Mandanten registriert ist.

Wenn Fehler auftreten, lesen Sie [die Informationen zur Problembehandlung bei der SSO-Authentifizierung in Teams](tab-sso-troubleshooting.md).

### <a name="use-the-access-token-as-an-identity-token"></a>Verwenden des Zugriffstokens als Identitätstoken

Das an die Registerkarten-App zurückgegebene Token ist sowohl ein Zugriffstoken als auch ein ID-Token. Die Registerkarten-App kann das Token als Zugriffstoken verwenden, um authentifizierte HTTPS-Anforderungen an APIs auf der Serverseite zu senden.

Das zurückgegebene `getAuthToken()` Zugriffstoken kann verwendet werden, um die Identität des App-Benutzers anhand der folgenden Ansprüche im Token festzulegen:

- `name`: Der Anzeigename des App-Benutzers.
- `preferred_username`: Die E-Mail-Adresse des App-Benutzers.
- `oid`: Eine GUID, die die ID des App-Benutzers darstellt.
- `tid`: Eine GUID, die den Mandanten darstellt, bei dem sich der App-Benutzer anmeldet.

Teams kann diese Informationen, die der Identität des App-Benutzers zugeordnet sind, zwischenspeichern, z. B. die Einstellungen des Benutzers.

> [!NOTE]
> Wenn Sie eine eindeutige ID erstellen müssen, um den App-Benutzer in Ihrem System darzustellen, lesen Sie ["Verwenden von Ansprüchen zum zuverlässigen Identifizieren eines Benutzers](/azure/active-directory/develop/id-tokens#using-claims-to-reliably-identify-a-user-subject-and-object-id)".

## <a name="pass-the-access-token-to-server-side-code"></a>Übergeben des Zugriffstokens an serverseitigen Code

Wenn Sie auf Web-APIs auf Ihrem Server zugreifen müssen, müssen Sie das Zugriffstoken an Ihren serverseitigen Code übergeben. Die Web-APIs müssen das Zugriffstoken decodieren, um Ansprüche für dieses Token anzuzeigen.

> [!NOTE]
> Wenn Sie keinen Benutzerprinzipalnamen (User Principal Name, UPN) im zurückgegebenen Zugriffstoken erhalten, fügen Sie es als [optionalen Anspruch](/azure/active-directory/develop/active-directory-optional-claims) in Azure AD hinzu.
> Weitere Informationen finden Sie [unter Zugriffstoken](/azure/active-directory/develop/access-tokens).

Das Zugriffstoken, das beim Erfolgsrückruf von `getAuthToken()` empfangen wurde, bietet Zugriff (für den authentifizierten App-Benutzer) auf Ihre Web-APIs. Der serverseitige Code kann das Token bei Bedarf auch nach [Identitätsinformationen](#use-the-access-token-as-an-identity-token) analysieren.

Wenn Sie das Zugriffstoken übergeben müssen, um Microsoft Graph-Daten abzurufen, lesen Sie die [Registerkarten-App erweitern mit Microsoft Graph-Berechtigungen](tab-sso-graph-api.md).

### <a name="code-for-passing-access-token-to-server-side"></a>Code zum Übergeben des Zugriffstokens an die serverseitige

Der folgende Code zeigt ein Beispiel für die Übergabe des Zugriffstokens an die Server-Seite. Das Token wird in einem `Authorization` Header übergeben, wenn eine Anforderung an eine serverseitige Web-API gesendet wird. In diesem Beispiel werden JSON-Daten gesendet, sodass die `POST` Methode verwendet wird. Dies `GET` reicht aus, um das Zugriffstoken zu senden, wenn Sie nicht auf den Server schreiben.

```javascript
$.ajax({
    type: "POST",
    url: "/api/DoSomething",
    headers: {
        "Authorization": "Bearer " + accessToken
    },
    data: { /* some JSON payload */ },
    contentType: "application/json; charset=utf-8"
}).done(function (data) {
    // Handle success
}).fail(function (error) {
    // Handle error
}).always(function () {
    // Cleanup
});
```

### <a name="validate-the-access-token"></a>Überprüfen des Zugriffstokens

Web-APIs auf Ihrem Server müssen das Zugriffstoken decodieren und überprüfen, ob es vom Client gesendet wird. Der Token ist ein JSON-Webtoken (JWT), was bedeutet, dass die Überprüfung genauso wie die Tokenüberprüfung in den meisten standardmäßigen OAuth-Flüssen erfolgt. Die Web-APIs müssen das Zugriffstoken decodieren. Optional können Sie das Zugriffstoken manuell kopieren und in ein Tool einfügen, z. B. jwt.ms.

Es sind eine Reihe von Bibliotheken verfügbar, die die JWT-Überprüfung verarbeiten können. Die grundlegende Überprüfung umfasst:

- Überprüfen, ob der Token wohlgeformt ist
- Überprüfen, ob der Token von der vorgesehenen Autorität ausgestellt wurde
- Überprüfen, ob das Token auf die Web-API ausgerichtet ist

Beachten Sie bei der Überprüfung des Tokens die folgenden Richtlinien:

- Gültige SSO-Token werden von Azure AD ausgestellt. Der `iss`-Anspruch im Token sollte mit diesem Wert beginnen.
- Der Parameter des `aud1` Tokens wird auf die App-ID festgelegt, die während der Azure AD-App-Registrierung generiert wird.
- Der `scp`-Parameter des Tokens wird auf `access_as_user` festgelegt.

#### <a name="example-access-token"></a>Beispielzugriffstoken

Das folgende Beispiel zeigt eine typische dekodierte Nutzlast eines Zugriffstokens.

```javascript
{
    aud: "2c3caa80-93f9-425e-8b85-0745f50c0d24",
    iss: "https://login.microsoftonline.com/fec4f964-8bc9-4fac-b972-1c1da35adbcd/v2.0",
    iat: 1521143967,
    nbf: 1521143967,
    exp: 1521147867,
    aio: "ATQAy/8GAAAA0agfnU4DTJUlEqGLisMtBk5q6z+6DB+sgiRjB/Ni73q83y0B86yBHU/WFJnlMQJ8",
    azp: "e4590ed6-62b3-5102-beff-bad2292ab01c",
    azpacr: "0",
    e_exp: 262800,
    name: "Mila Nikolova",
    oid: "6467882c-fdfd-4354-a1ed-4e13f064be25",
    preferred_username: "milan@contoso.com",
    scp: "access_as_user",
    sub: "XkjgWjdmaZ-_xDmhgN1BMP2vL2YOfeVxfPT_o8GRWaw",
    tid: "fec4f964-8bc9-4fac-b972-1c1da35adbcd",
    uti: "MICAQyhrH02ov54bCtIDAA",
    ver: "2.0"
}
```

## <a name="code-samples"></a>Codebeispiele

| Beispielname | Beschreibung | C#/.NET| Node.js |
|---------------|---------------|------|--------------|
| Registerkarten-SSO |Microsoft Teams-Beispiel-App für Azure AD SSO-Registerkarten| [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-sso/csharp)|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/blob/main/samples/tab-sso/nodejs), </br>[Teams Toolkit](../../../toolkit/visual-studio-code-tab-sso.md)|
| Registerkarten-, Bot- und Nachrichtenerweiterungs-SSO (ME) | Dieses Beispiel zeigt SSO für Tab, Bot und ME – Suche, Aktion, linkunfurl. |  [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-sso/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-sso/nodejs) |

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Aktualisieren des Teams-App-Manifests und Anzeigen einer Vorschau der App](tab-sso-manifest.md)

## <a name="see-also"></a>Siehe auch

- [jwt.ms](https://jwt.ms/)
- [Optionaler Active Directory-Anspruch](/azure/active-directory/develop/active-directory-optional-claims)
- [Zugriffstoken](/azure/active-directory/develop/access-tokens)
- [Übersicht über die Microsoft-Authentifizierungsbibliothek (MSAL)](/azure/active-directory/develop/msal-overview)
- [Microsoft Identity Platform-ID-Token](/azure/active-directory/develop/id-tokens)
- [Microsoft Identity Platform – Zugriffstoken](/azure/active-directory/develop/access-tokens#validating-tokens)