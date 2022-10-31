---
title: Erweitern der Registerkarten-App mit Microsoft Graph-Berechtigungen
description: Konfigurieren Sie zusätzliche Berechtigungen und Bereiche mit Microsoft Graph zum Aktivieren des einmaligen Anmeldens (Single Sign-On, SSO).
ms.topic: how-to
ms.localizationpriority: high
keywords: Delegierter Berechtigungszugriffstokenbereich für Teams-Authentifizierungsregisterkarten in Microsoft Azure Active Directory (Azure AD)-Graph-API
ms.openlocfilehash: 11620e10ed736ce9fe88e3bb755acfbabfec3f47
ms.sourcegitcommit: 84747a9e3c561c2ca046eda0b52ada18da04521d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2022
ms.locfileid: "68791720"
---
# <a name="extend-tab-app-with-microsoft-graph-permissions-and-scope"></a>Erweitern der Registerkarten-App mit Microsoft Graph-Berechtigungen und -Bereich

Sie können Ihre Registerkarten-App erweitern, indem Sie Microsoft Graph verwenden, um Benutzern zusätzliche Berechtigungen zu gewähren, z. B. das Anzeigen des App-Benutzerprofils, das Lesen von E-Mails und vieles mehr. Ihre App muss bestimmte Berechtigungsbereiche anfordern, um die Zugriffstoken nach Zustimmung des App-Benutzers abzurufen.

Mit Graph-Bereichen wie `User.Read` oder `Mail.Read` können Sie angeben, wie Ihre App auf das Konto eines Teams-Benutzers zugreift. Sie müssen Ihre Bereiche in der Autorisierungsanforderung angeben.

In diesem Abschnitt lernen Sie Folgendes:

- [Konfigurieren von API-Berechtigungen in Azure AD](#configure-api-permissions-in-azure-ad)
- [Konfigurieren der Authentifizierung für verschiedene Plattformen](#configure-authentication-for-different-platforms)
- [Abrufen des Zugriffstokens für MS Graph](#acquire-access-token-for-ms-graph)

## <a name="configure-api-permissions-in-azure-ad"></a>Konfigurieren von API-Berechtigungen in Azure AD

Sie können in Azure AD zusätzliche Graph-Bereiche für Ihre App konfigurieren. Hierbei handelt es sich um delegierte Berechtigungen, die von Apps verwendet werden, die angemeldeten Zugriff erfordern. Ein angemeldeter App-Benutzer oder Administrator muss dem zustimmen. Ihre Registerkarten-App kann im Namen des angemeldeten Benutzers zustimmen, wenn sie Microsoft Graph aufruft.

### <a name="to-configure-api-permissions"></a>So konfigurieren Sie API-Berechtigungen

1. Öffnen Sie die App, die Sie im [Azure-Portal](https://ms.portal.azure.com/) registriert haben.

2. Wählen Sie im linken Bereich **Verwalten** > **API-Berechtigung** aus.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/api-permission-menu.png" alt-text="Menüoption &quot;App-Berechtigungen&quot;.":::

    Die Seite **API-Berechtigungen** wird angezeigt.

3. Wählen Sie **Berechtigungen hinzufügen +** aus, um Microsoft Graph-API-Berechtigungen hinzuzufügen.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/app-permission.png" alt-text="Seite &quot;App-Berechtigungen&quot;.":::

    Die Seite **API-Berechtigungen anfordern** wird angezeigt.

4. Wählen Sie **Microsoft Graph** aus.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/request-api-permission.png" alt-text="Seite &quot;API-Berechtigungen anfordern&quot;.":::

    Die Optionen für Graph-Berechtigungen werden angezeigt.

5. Wählen Sie **Delegierte Berechtigungen** aus, um die Liste der Berechtigungen anzuzeigen.

   :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/delegated-permission.png" alt-text="Delegierte Berechtigungen.":::

6. Wählen Sie die relevanten Berechtigungen für Ihre App und dann **Berechtigungen hinzufügen** aus.

   :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/select-permission.png" alt-text="Berechtigungen auswählen.":::

    Sie können auch den Berechtigungsnamen in das Suchfeld eingeben, um ihn zu finden.

    Im Browser wird eine Meldung angezeigt, die besagt, dass die Berechtigungen aktualisiert wurden.

   :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/updated-permission-msg.png" alt-text="Nachricht über aktualisierte Berechtigungen.":::

    Die hinzugefügten Berechtigungen werden auf der Seite **API-Berechtigungen** angezeigt.

   :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/configured-permissions.png" alt-text="API-Berechtigungen sind konfiguriert.":::

    Sie haben Ihre App mit Microsoft Graph-Berechtigungen konfiguriert.

## <a name="configure-authentication-for-different-platforms"></a>Konfigurieren der Authentifizierung für verschiedene Plattformen

Je nach Plattform oder Gerät, auf die bzw. das Sie Ihre App ausrichten möchten, ist möglicherweise eine zusätzliche Konfiguration erforderlich, wie z. B. Umleitungs-URIs, bestimmte Authentifizierungseinstellungen oder plattformspezifische Details.

> [!NOTE]
>
> - Wenn Ihrer App keine IT-Administratorzustimmung erteilt wurde, müssen Benutzer die Zustimmung erteilen, wenn sie Ihre App zum ersten Mal verwenden.
> - Die implizite Gewährung ist nicht erforderlich, wenn SSO in einer Registerkarten-App aktiviert ist.

Sie können die Authentifizierung für mehrere Plattformen konfigurieren, solange die URL eindeutig ist.

### <a name="to-configure-authentication-for-a-platform"></a>So konfigurieren Sie die Authentifizierung für eine Plattform

1. Öffnen Sie die App, die Sie im [Azure-Portal](https://ms.portal.azure.com/) registriert haben.

1. Wählen Sie im linken Bereich **Verwalten** > **Authentifizierung** aus.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/azure-portal-platform.png" alt-text="Authentifizieren für Plattformen":::

    Die Seite **Plattformkonfigurationen** wird angezeigt.

1. Wählen Sie **Plattform hinzufügen +** aus.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/add-platform.png" alt-text="Hinzufügen von Plattformen":::

    Die Seite **Plattformen konfigurieren** wird angezeigt.

1. Wählen Sie die Plattform aus, die Sie für Ihre Registerkarten-App konfigurieren möchten. Sie können den Plattformtyp Web oder SPA auswählen.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/configure-platform.png" alt-text="Webplattform auswählen":::

    Sie können mehrere Plattformen für einen bestimmten Plattformtyp konfigurieren. Stellen Sie sicher, dass der Umleitungs-URI für jede von Ihnen konfigurierte Plattform eindeutig ist.

    Die Seite "Web konfigurieren" wird angezeigt.

    > [!NOTE]
    > Die Konfigurationen sind je nach ausgewählter Plattform unterschiedlich.

1. Geben Sie die Konfigurationsdetails für die Plattform ein.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/config-web-platform.png" alt-text="Konfigurieren der Webplattform":::

    1. Geben Sie den Umleitungs-URI ein. Der URI sollte eindeutig sein.
    2. Geben Sie die URL für Front-Channel-Abmeldung ein.
    3. Wählen Sie die Token aus, die Azure AD für Ihre App senden soll.

1. Wählen Sie **Konfigurieren** aus.

    Die Plattform wird konfiguriert und auf der Seite **Plattformkonfigurationen** angezeigt.

## <a name="acquire-access-token-for-ms-graph"></a>Abrufen des Zugriffstokens für MS Graph

Sie müssen ein Zugriffstoken für Microsoft Graph abrufen. Sie können dies mithilfe des Azure AD OBO-Flusses tun.

Die aktuelle Implementierung für SSO erteilt die Zustimmung nur für Berechtigungen auf Benutzerebene, die nicht für Graph-Aufrufe verwendet werden können. Um die Berechtigungen (Bereiche) abzurufen, die zum Ausführen eines Graph-Aufrufs erforderlich sind, müssen SSO-Apps einen benutzerdefinierten Webdienst implementieren, um das vom Teams JavaScript SDK empfangene Token gegen ein Token auszutauschen, das die erforderlichen Bereiche enthält. Sie können die Microsoft-Authentifizierungsbibliothek (MSAL) verwenden, um das Token von der Clientseite abzurufen.

Nachdem Sie Graph-Berechtigungen in Azure AD konfiguriert haben:

- [Konfigurieren der clientseitigen Codes zum Abrufen des Zugriffstokens mithilfe der MSAL](#configure-code-to-fetch-access-token-using-msal)
- [Übergeben des Zugriffstokens an serverseitigen Code](#pass-the-access-token-to-server-side-code)

### <a name="configure-code-to-fetch-access-token-using-msal"></a>Konfigurieren des Codes zum Abrufen des Zugriffstokens mithilfe der MSAL

Der folgende Code enthält ein Beispiel für den OBO-Fluss zum Abrufen des Zugriffstokens mithilfe der MSAL.

### <a name="c"></a>[C#](#tab/dotnet)

```csharp

IConfidentialClientApplication app = ConfidentialClientApplicationBuilder.Create(<"Client id">)
                                                .WithClientSecret(<"Client secret">)
                                                .WithAuthority($"https://login.microsoftonline.com/<"Tenant id">")
                                                .Build();
 
            try
            {
                var idToken = <"Client side token">;
                UserAssertion assert = new UserAssertion(idToken);
                List<string> scopes = new List<string>();
                scopes.Add("https://graph.microsoft.com/User.Read");
                var responseToken = await app.AcquireTokenOnBehalfOf(scopes, assert).ExecuteAsync();
                return responseToken.AccessToken.ToString();
            }
            catch (Exception ex)
            {
                return ex.Message;
            }
        }
```

### <a name="nodejs"></a>[Node.js](#tab/nodejs)

```Node.js

// Exchange client Id side token with server token
  app.post('/getProfileOnBehalfOf', function(req, res) {
        var tid = < "Tenant id" >
    var token = < "Client side token" >
    var scopes = ["https://graph.microsoft.com/User.Read"];

        // Creating MSAL client
        const msalClient = new msal.ConfidentialClientApplication({
            auth: {
                clientId: < "Client ID" >,
                clientSecret: < "Client Secret" >
      }
        });

        var oboPromise = new Promise((resolve, reject) => {
            msalClient.acquireTokenOnBehalfOf({
                authority: `https://login.microsoftonline.com/${tid}`,
                oboAssertion: token,
                scopes: scopes,
                skipCache: true
            }).then(result => {
                console.log("Token is: " + result.accessToken);
            }).catch(error => {
                reject({ "error": error.errorCode });
            });
        });
```

---

### <a name="pass-the-access-token-to-server-side-code"></a>Übergeben des Zugriffstokens an serverseitigen Code

Wenn Sie auf Microsoft Graph-Daten zugreifen müssen, konfigurieren Sie Ihren serverseitigen Code wie folgt:

1. Überprüfen des Zugriffstokens. Weitere Informationen finden Sie unter [Überprüfen des Zugriffstokens](tab-sso-code.md#validate-the-access-token).
1. Initiieren Sie den OAuth 2.0 OBO-Fluss mit einem Aufruf an die Microsoft-Identitätsplattform, der das Zugriffstoken, einige Metadaten über den Benutzer und die Anmeldedaten der Registerkarten-App (ihre App-ID und ihren geheimen Clientschlüssel) enthält. Die Microsoft-Identitätsplattform gibt ein neues Zugriffstoken zurück, das für den Zugriff auf Microsoft Graph verwendet werden kann.
1. Rufen Sie Daten aus Microsoft Graph unter Verwendung des neuen Tokens ab.
1. Verwenden Sie die Token-Cache-Serialisierung in MSAL.NET, um das neue Zugriffstoken bei Bedarf für mehrere zwischenzuspeichern.

> [!IMPORTANT]
> Als bewährte Sicherheitsmethode sollten Sie immer den serverseitigen Code verwenden, um Microsoft Graph-Aufrufe oder andere Aufrufe auszuführen, welche die Übergabe eines Zugriffstokens erfordern. Geben Sie niemals das OBO-Token an den Client zurück, damit der Client direkte Aufrufe an Microsoft Graph durchführen kann. Dadurch wird verhindert, dass der Token abgefangen oder weitergegeben werden kann.

## <a name="known-limitations"></a>Bekannte Einschränkungen

Zustimmung des Mandantenadministrators: Eine einfache Möglichkeit, [im Namen einer Organisation als Mandantenadministrator zuzustimmen](/azure/active-directory/manage-apps/consent-and-permissions-overview#admin-consent), besteht darin, die [Zustimmung des Administrators](/azure/active-directory/manage-apps/grant-admin-consent) einzuholen.

Sie können die Zustimmung mithilfe der Auth-API anfordern. Ein weiterer Ansatz zum Abrufen von Graph-Bereichen besteht darin, ein Zustimmungsdialogfeld mithilfe unseres vorhandenen [OAuth-Drittanbieter-Authentifizierungsansatzes](~/tabs/how-to/authentication/auth-tab-aad.md#navigate-to-the-authorization-page-from-your-pop-up-page) anzuzeigen. Bei diesem Ansatz wird ein Azure AD-Zustimmungsdialogfeld angezeigt.

<details>
<summary>Führen Sie die folgenden Schritte aus, um mithilfe der Auth-API um zusätzliche Zustimmung zu bitten:</summary>

1. Das mit `getAuthToken()` abgerufene Token muss auf der Serverseite mit dem Azure AD-[OBO-Fluss](/azure/active-directory/develop/v2-oauth2-on-behalf-of-flow) ausgetauscht werden, um Zugriff auf diese anderen Graph-APIs zu erhalten. Stellen Sie sicher, dass Sie den v2-Graph-Endpunkt für diesen Austausch verwenden.
2. Wenn der Austausch fehlschlägt, gibt Azure AD eine Ausnahme für ungültige Genehmigungen zurück. Er antwortet in der Regel mit einer der beiden Fehlermeldungen `invalid_grant` oder `interaction_required`.
3. Wenn der Austausch fehlschlägt, müssen Sie die Zustimmung anfordern. Verwenden Sie die Benutzeroberfläche (UI), um den App-Benutzer aufzufordern, eine andere Zustimmung zu erteilen. Diese UI muss eine Schaltfläche enthalten, die ein Azure AD-Zustimmungsdialogfeld mit [Automatischer Authentifizierung](~/concepts/authentication/auth-silent-aad.md) auslöst.
4. Wenn Sie weitere Zustimmungen von Azure AD anfordern, müssen Sie `prompt=consent` in den [Abfragezeichenfolgenparameter](~/tabs/how-to/authentication/auth-silent-aad.md#get-the-user-context) in Azure AD einschließen, andernfalls würde Azure AD nicht nach den anderen Bereichen fragen.
    - Verwenden Sie `?prompt=consent&scope={scopes}` anstelle von `?scope={scopes}`
    - Stellen Sie sicher, dass `{scopes}` alle Bereiche enthält, für die Sie den Benutzer auffordern, z. B. `Mail.Read` oder `User.Read`.

    Informationen zum Verarbeiten der inkrementellen Zustimmung für tab-Apps finden Sie unter [Inkrementelle und dynamische Benutzerzustimmung](/azure/active-directory/develop/v2-permissions-and-consent).
5. Nachdem der App-Benutzer mehr Berechtigungen erteilt hat, wiederholen Sie den OBO-Fluss, um Zugriff auf diese anderen APIs zu erhalten.
    </details>

## <a name="see-also"></a>Siehe auch

- [OAuth 2.0 – On-Behalf-Of-Fluss](/azure/active-directory/develop/v2-oauth2-on-behalf-of-flow).
- [Zugriff für MS Graph erhalten](/graph/auth-v2-user)
- [Token-Cache-Serialisierung in MSAL.NET](/azure/active-directory/develop/msal-net-token-cache-serialization?tabs=aspnet)
- [Microsoft Teams MSAL2-Anbieter](/graph/toolkit/providers/teams-msal2)
