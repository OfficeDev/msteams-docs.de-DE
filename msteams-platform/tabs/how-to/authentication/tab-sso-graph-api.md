---
title: Erweitern der Registerkarten-App mit Microsoft Graph-Berechtigungen
description: Beschreibt das Konfigurieren von API-Berechtigungen mit Microsoft Graph
ms.topic: how-to
ms.localizationpriority: medium
keywords: Teams-Authentifizierungsregisterkarten Microsoft Azure Active Directory (Azure AD) Graph-API Delegierten Berechtigungszugriffstokenbereich
ms.openlocfilehash: 474d02c5b5f90e58bfc57f72ab6ce095a0323b62
ms.sourcegitcommit: c398dfdae9ed96f12e1401ac7c8d0228ff9c0a2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2022
ms.locfileid: "66558254"
---
# <a name="extend-tab-app-with-microsoft-graph-permissions-and-scope"></a>Erweitern der Registerkarten-App mit Microsoft Graph-Berechtigungen und -Bereich

Sie können Ihre Registerkarten-App erweitern, indem Sie Microsoft Graph verwenden, um Benutzern zusätzliche Berechtigungen zu ermöglichen, z. B. das Anzeigen des App-Benutzerprofils, das Lesen von E-Mails und vieles mehr. Ihre App muss bestimmte Berechtigungsbereiche anfordern, um die Zugriffstoken nach Zustimmung des App-Benutzers abzurufen.

Mit Diagrammbereichen wie `User.Read` oder `Mail.Read`können Sie angeben, wie Ihre App auf das Konto eines Teams-Benutzers zugreift. Sie müssen Ihre Bereiche in der Autorisierungsanforderung angeben.

In diesem Abschnitt lernen Sie Folgendes:

- [Konfigurieren von API-Berechtigungen in Azure AD](#configure-api-permissions-in-azure-ad)
- [Konfigurieren der Authentifizierung für verschiedene Plattformen](#configure-authentication-for-different-platforms)
- [Abrufen des Zugriffstokens für MS Graph](#acquire-access-token-for-ms-graph)

## <a name="configure-api-permissions-in-azure-ad"></a>Konfigurieren von API-Berechtigungen in Azure AD

Sie können zusätzliche Graph-Bereiche in Azure AD für Ihre App konfigurieren. Hierbei handelt es sich um delegierte Berechtigungen, die von Apps verwendet werden, die angemeldeten Zugriff erfordern. Ein angemeldeter App-Benutzer oder -Administrator muss dem zustimmen. Ihre Registerkarten-App kann im Namen des angemeldeten Benutzers zustimmen, wenn sie Microsoft Graph aufruft.

### <a name="to-configure-api-permissions"></a>So konfigurieren Sie API-Berechtigungen

1. Öffnen Sie die App, die Sie im [Azure-Portal registriert haben](https://ms.portal.azure.com/).

2. Wählen Sie im linken Bereich die **Berechtigung "API** **verwalten** > " aus.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/api-permission-menu.png" alt-text="Menüoption &quot;App-Berechtigungen&quot;.":::

    Die Seite **"API-Berechtigungen"** wird angezeigt.

3. Wählen Sie **"+ Berechtigungen hinzufügen**" aus, um Microsoft Graph-API-Berechtigungen hinzuzufügen.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/app-permission.png" alt-text="Seite &quot;App-Berechtigungen&quot;.":::

    Die Seite **"API-Berechtigungen anfordern** " wird angezeigt.

4. Wählen Sie **Microsoft Graph aus**.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/request-api-permission.png" alt-text="Seite &quot;API-Berechtigungen anfordern&quot;.":::

    Die Optionen für Graph-Berechtigungen werden angezeigt.

5. Wählen Sie **delegierte Berechtigungen** aus, um die Liste der Berechtigungen anzuzeigen.

   :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/delegated-permission.png" alt-text="Delegierte Berechtigungen.":::

6. Wählen Sie die relevanten Berechtigungen für Ihre App und dann **"Berechtigungen hinzufügen"** aus.

   :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/select-permission.png" alt-text="Wählen Sie Berechtigungen aus.":::

    Sie können auch den Berechtigungsnamen in das Suchfeld eingeben, um ihn zu finden.

    Im Browser wird eine Meldung angezeigt, die besagt, dass die Berechtigungen aktualisiert wurden.

   :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/updated-permission-msg.png" alt-text="Nachricht mit aktualisierten Berechtigungen.":::

    Die hinzugefügten Berechtigungen werden auf der **Api-Berechtigungsseite** angezeigt.

   :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/configured-permissions.png" alt-text="API-Berechtigungen sind konfiguriert.":::

    Sie haben Ihre App mit Microsoft Graph-Berechtigungen konfiguriert.

## <a name="configure-authentication-for-different-platforms"></a>Konfigurieren der Authentifizierung für verschiedene Plattformen

Je nach Plattform oder Gerät, auf die Bzw. das Sie Ihre App ausrichten möchten, ist möglicherweise eine zusätzliche Konfiguration erforderlich, z. B. Umleitungs-URIs, bestimmte Authentifizierungseinstellungen oder plattformspezifische Details.

> [!NOTE]
>
> - Wenn Ihrer Registerkarten-App keine ZUSTIMMUNG des IT-Administrators erteilt wurde, müssen App-Benutzer ihre Zustimmung erteilen, wenn sie Ihre App zum ersten Mal auf einer anderen Plattform verwenden.
> - Die implizite Gewährung ist nicht erforderlich, wenn SSO in einer Registerkarten-App aktiviert ist.

Sie können die Authentifizierung für mehrere Plattformen konfigurieren, solange die URL eindeutig ist.

### <a name="to-configure-authentication-for-a-platform"></a>So konfigurieren Sie die Authentifizierung für eine Plattform

1. Öffnen Sie die App, die Sie im [Azure-Portal registriert haben](https://ms.portal.azure.com/).

1. Wählen Sie im linken Bereich "**Authentifizierung** **verwalten** > " aus.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/azure-portal-platform.png" alt-text="Authentifizieren für Plattformen":::

    Die Seite **"Plattformkonfigurationen** " wird angezeigt.

1. Wählen Sie **eine Plattform aus, und fügen Sie sie hinzu**.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/add-platform.png" alt-text="Hinzufügen von Plattformen":::

    Die Seite **"Plattformen konfigurieren"** wird angezeigt.

1. Wählen Sie die Plattform aus, die Sie für Ihre Registerkarten-App konfigurieren möchten. Sie können den Plattformtyp aus dem Web oder spa auswählen.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/configure-platform.png" alt-text="Webplattform auswählen":::

    Sie können mehrere Plattformen für einen bestimmten Plattformtyp konfigurieren. Stellen Sie sicher, dass der Umleitungs-URI für jede von Ihnen konfigurierte Plattform eindeutig ist.

    Die Seite "Webseite konfigurieren" wird angezeigt.

    > [!NOTE]
    > Die Konfigurationen sind je nach ausgewählter Plattform unterschiedlich.

1. Geben Sie die Konfigurationsdetails für die Plattform ein.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/config-web-platform.png" alt-text="Konfigurieren der Webplattform":::

    1. Geben Sie den Umleitungs-URI ein. Der URI sollte eindeutig sein.
    2. Geben Sie die Url für das Front-Channel-Abmelden ein.
    3. Wählen Sie die Token aus, die Azure AD für Ihre App senden soll.

1. Wählen Sie **Konfigurieren** aus.

    Die Plattform wird konfiguriert und auf der Seite " **Plattformkonfigurationen** " angezeigt.

## <a name="acquire-access-token-for-ms-graph"></a>Abrufen des Zugriffstokens für MS Graph

Sie müssen ein Zugriffstoken für Microsoft Graph erwerben. Sie können dies mithilfe des Azure AD OBO-Flusses tun.

Die aktuelle Implementierung für SSO erteilt nur Berechtigungen auf Benutzerebene, die nicht für Graph-Aufrufe verwendet werden können. Um die Berechtigungen (Bereiche) abzurufen, die für einen Graph-Aufruf erforderlich sind, müssen SSO-Apps einen benutzerdefinierten Webdienst implementieren, um das vom Teams JavaScript SDK empfangene Token gegen ein Token auszutauschen, das die erforderlichen Bereiche enthält. Sie können die Microsoft-Authentifizierungsbibliothek (MSAL) verwenden, um das Token von der Clientseite abzurufen.

Nachdem Sie Graph-Berechtigungen in Azure AD konfiguriert haben:

- [Konfigurieren Des clientseitigen Codes zum Abrufen des Zugriffstokens mithilfe von MSAL](#configure-code-to-fetch-access-token-using-msal)
- [Übergeben des Zugriffstokens an serverseitigen Code](#pass-the-access-token-to-server-side-code)

### <a name="configure-code-to-fetch-access-token-using-msal"></a>Konfigurieren von Code zum Abrufen des Zugriffstokens mithilfe von MSAL

Der folgende Code enthält ein Beispiel für den OBO-Fluss zum Abrufen des Zugriffstokens vom Teams-Client mithilfe von MSAL.

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

Wenn Sie auf Microsoft Graph-Daten zugreifen müssen, konfigurieren Sie Ihren serverseitigen Code für Folgendes:

1. Überprüfen Sie das Zugriffstoken. Weitere Informationen finden Sie unter [Überprüfen des Zugriffstokens](tab-sso-code.md#validate-the-access-token).
1. Initiieren Sie den OAuth 2.0-OBO-Fluss mit einem Aufruf der Microsoft Identity Platform, die das Zugriffstoken, einige Metadaten zum Benutzer und die Anmeldeinformationen der Registerkarten-App (app-ID und geheimer Clientschlüssel) enthält. Die Microsoft-Identitätsplattform gibt ein neues Zugriffstoken zurück, das für den Zugriff auf Microsoft Graph verwendet werden kann.
1. Rufen Sie Daten aus Microsoft Graph unter Verwendung des neuen Tokens ab.
1. Verwenden Sie die Tokencache-Serialisierung in MSAL.NET, um das neue Zugriffstoken bei Bedarf für mehrere zwischenzuspeichern.

> [!IMPORTANT]
> Als bewährte Methode für die Sicherheit sollten Sie immer den serverseitigen Code verwenden, um Microsoft Graph-Aufrufe oder andere Aufrufe auszuführen, für die das Übergeben eines Zugriffstokens erforderlich ist. Geben Sie niemals das OBO-Token an den Client zurück, damit der Client direkte Aufrufe an Microsoft Graph durchführen kann. Dadurch wird verhindert, dass der Token abgefangen oder weitergegeben werden kann.

## <a name="known-limitations"></a>Bekannte Einschränkungen

Zustimmung des Mandantenadministrators: Eine einfache Möglichkeit, [im Namen einer Organisation als Mandantenadministrator zuzustimmen](/azure/active-directory/manage-apps/consent-and-permissions-overview#admin-consent) , besteht darin, die [Zustimmung des Administrators](/azure/active-directory/manage-apps/grant-admin-consent) einzugeben.

Sie können mithilfe der Auth-API um Zustimmung bitten. Ein weiterer Ansatz zum Abrufen von Graph-Bereichen besteht darin, ein Zustimmungsdialogfeld mit unserem vorhandenen [OAuth-Anbieterauthentifizierungsansatz von Drittanbietern](~/tabs/how-to/authentication/auth-tab-aad.md#navigate-to-the-authorization-page-from-your-pop-up-page) zu präsentieren. Bei diesem Ansatz wird ein Azure AD-Zustimmungsdialogfeld angezeigt.

<details>
<summary>Führen Sie die folgenden Schritte aus, um mithilfe der Auth-API um zusätzliche Zustimmung zu bitten:</summary>

1. Das mithilfe `getAuthToken()` des abgerufenen Tokens muss serverseitig mithilfe von Azure AD [im Auftrag von Flow](/azure/active-directory/develop/v2-oauth2-on-behalf-of-flow) ausgetauscht werden, um Zugriff auf diese anderen Graph-APIs zu erhalten. Stellen Sie sicher, dass Sie den v2-Graph-Endpunkt für diesen Austausch verwenden.
2. Wenn der Austausch fehlschlägt, gibt Azure AD eine Ausnahme für ungültige Genehmigungen zurück. Er antwortet in der Regel mit einer der beiden Fehlermeldungen oder `invalid_grant` `interaction_required`.
3. Wenn der Austausch fehlschlägt, müssen Sie die Zustimmung anfordern. Verwenden Sie die Benutzeroberfläche (UI), um den App-Benutzer aufzufordern, eine andere Zustimmung zu erteilen. Diese Benutzeroberfläche muss eine Schaltfläche enthalten, die ein Azure AD-Zustimmungsdialogfeld mithilfe der [automatischen Authentifizierung](~/concepts/authentication/auth-silent-aad.md) auslöst.
4. Wenn Sie mehr Zustimmung von Azure AD anfordern, müssen Sie ihren [Abfragezeichenfolgenparameter](~/tabs/how-to/authentication/auth-silent-aad.md#get-the-user-context) in Azure AD einschließen`prompt=consent`, andernfalls würde Azure AD keine anderen Bereiche anfordern.
    - Anstelle von `?scope={scopes}`verwenden Sie `?prompt=consent&scope={scopes}`
    - Stellen Sie sicher, dass `{scopes}` alle Bereiche enthalten sind, für die Sie den Benutzer z. B. auffordern, `Mail.Read` oder `User.Read`.
5. Nachdem der App-Benutzer weitere Berechtigungen erteilt hat, wiederholen Sie den OBO-Fluss, um Zugriff auf diese anderen APIs zu erhalten.

    </details>

## <a name="see-also"></a>Siehe auch

- [OAuth 2.0-Fluss im Auftrag von](/azure/active-directory/develop/v2-oauth2-on-behalf-of-flow)
- [Zugriff auf MS Graph erhalten](/graph/auth-v2-user)
- [Tokencache-Serialisierung in MSAL.NET](/azure/active-directory/develop/msal-net-token-cache-serialization?tabs=aspnet)
- [Microsoft Teams MSAL2-Anbieter](/graph/toolkit/providers/teams-msal2)
