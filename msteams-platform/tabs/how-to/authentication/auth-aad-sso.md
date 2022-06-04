---
title: Unterstützung für einmaliges Anmelden für Registerkarten
description: Beschreibt Einmaliges Anmelden (SSO)
ms.topic: how-to
ms.localizationpriority: high
keywords: Teams-Authentifizierungs-SSO – Microsoft Azure Active Directory (Azure AD)-Single Sign-On-API
ms.openlocfilehash: d9391489c8bafafa24ba52528f5d0b8440319a55
ms.sourcegitcommit: b7b41ec2a1f022eb15a1980d1b31d22df1170913
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2022
ms.locfileid: "65888346"
---
# <a name="single-sign-on-sso-support-for-tabs"></a>Unterstützung für einmaliges Anmelden (SSO) für Registerkarten

Benutzer melden sich bei Microsoft Teams über ihr Geschäfts-, Schul- oder Microsoft-Konto an, das Office 365, Outlook ist. Sie können die Vorteile nutzen, indem Sie einer einmaligen Anmeldung erlauben, Ihre Teams-Registerkarte oder Ihr Aufgabenmodul auf Desktop- oder mobilen Clients zu autorisieren. Wenn sich ein Benutzer einmal anmeldet, muss er sich auf einem anderen Gerät nicht erneut anmelden, da er automatisch angemeldet ist. Ihr Zugriffstoken wird ebenfalls vorab abgerufen, um die Leistung und die Ladezeiten zu verbessern.

> [!NOTE]
> **Mobile Teams-Clients, die SSO unterstützen**  
>
> ✔Teams für Android (1416/1.0.0.2020073101 und höher)
>
> ✔Teams für iOS (_Version_: 2.0.18 und höher)  
>
> ✔Teams JavaScript SDK (_Version_: 1.11 und höher) für SSO, um im Besprechungsseitenbereich zu arbeiten.
>
> Für eine optimale Benutzererfahrung verwenden Sie die jeweils neueste Version von iOS und Android.[!NOTE]
> **Schnellstart**  
>
> Der einfachste Weg, um mit der Registerkarte SSO zu beginnen, ist das Teams-Toolkit für Microsoft Visual Studio Code. Weitere Informationen finden Sie unter [SSO mit Teams Toolkit und Visual Studio Code für Tabs](../../../toolkit/visual-studio-code-tab-sso.md)

<!--- TBD: Edit this article.
* Admonitions/alerts seem to be overused.
* Don't add note for a list of items.
* Don't add numbers to headings.
* Don't copy-paste superscript characters as is. Use HTML entities. See https://sitefarm.ucdavis.edu/training/all/using-wysiwyg/special-characters for the values.
* Same for the check marks added in the content in the note above. The content should not be in a note anyway.
--->

## <a name="how-sso-works-at-runtime"></a>Funktionsweise von SSO zur Laufzeit

Das folgende Bild veranschaulicht die Funktionsweise des SSO-Prozesses:

<!-- markdownlint-disable MD033 -->
<img src="~/assets/images/tabs/tabs-sso-diagram.png" alt="Tab single sign-on SSO diagram" width="75%"/>

1. In der Registerkarte wird ein JavaScript-Aufruf an `getAuthToken()` durchgeführt. `getAuthToken()` weist Teams an, ein Zugriffstoken für die Registerkartenanwendung abzurufen.
2. Wenn der aktuelle Benutzer Ihre Registerkartenanwendung zum ersten Mal verwendet, wird eine Aufforderung zur Zustimmung angefordert, wenn eine Zustimmung erforderlich ist. Alternativ gibt es eine Anforderungsaufforderung für die Verarbeitung der schrittweisen Authentifizierung, z. B. die zweistufige Authentifizierung.
3. Teams fordert das Registerkartenzugriffstoken vom Azure AD-Endpunkt für den aktuellen Benutzer an.
4. Azure AD sendet das Registerkartenzugriffstoken an die Teams Anwendung.
5. Teams sendet das Registerkartenzugriffstoken als Teil des Ergebnisobjekts, das vom `getAuthToken()`-Aufruf zurückgegeben wird, an die Registerkarte.
6. Das Token wird in der Registerkartenanwendung mithilfe von JavaScript analysiert, um die erforderlichen Informationen wie die E-Mail-Adresse des Benutzers zu extrahieren.

> [!NOTE]
> Dies `getAuthToken()` gilt nur für die Zustimmung zu einer begrenzten Gruppe von APIs auf Benutzerebene, d. h. E-Mail, Profil, offline_access und OpenId. Es wird nicht für weitere Graph-Bereiche wie `User.Read` oder `Mail.Read` verwendet. Vorgeschlagene Problemumgehungen finden Sie unter [Abrufen eines Zugriffstokens mit Graph-Berechtigungen](#get-an-access-token-with-graph-permissions).

Die SSO-API funktioniert auch in [Aufgabenmodulen](../../../task-modules-and-cards/what-are-task-modules.md), die Webinhalte einbetten.

## <a name="develop-an-sso-microsoft-teams-tab"></a>Entwickeln einer Microsoft Teams-Registerkarte für einmaliges Anmelden

In diesem Abschnitt werden die Aufgaben beschrieben, die bei der Erstellung einer Teams-Registerkarte, die SSO verwendet, ausgeführt werden müssen. Diese Aufgaben sind sprach- und frameworkunabhängig.

### <a name="1-create-your-azure-ad-application"></a>1. Erstellen einer Azure AD-Anwendung

> [!NOTE]
> Es gibt einige wichtige Einschränkungen, die Sie kennen müssen:
>
> * Es werden nur Graph API-Berechtigungen auf Benutzerebene unterstützt, d. h. E-Mail, Profil, offline_access, OpenId. Wenn Sie Zugriff auf andere Graph-Bereiche haben müssen, z. B. `User.Read` oder `Mail.Read`, finden Sie weitere Informationen unter [Abrufen eines Zugriffstokens mit Graph-Berechtigungen](#get-an-access-token-with-graph-permissions).
> * Es ist wichtig, dass der Domänenname Ihrer Anwendung mit dem Domänennamen übereinstimmt, den Sie für Ihre Azure AD-Anwendung registriert haben.
> * Derzeit werden mehrere Domänen pro App nicht unterstützt.
> * Der Benutzer muss für eine neue Anwendung `accessTokenAcceptedVersion` auf `2` festlegen.

Führen Sie die folgenden Schritte aus, um Ihre App über das Azure AD-Portal zu registrieren:

1. Registrieren Sie eine neue Anwendung im Portal [Azure AD-App-Registrierungen](https://go.microsoft.com/fwlink/?linkid=2083908).
1. Wählen Sie **Neue Registrierung** aus. Die Seite **Anwendung registrieren** wird angezeigt.
1. Geben Sie auf der Seite **Registrierung einer Anwendung** folgende Werte ein:
    1. Geben Sie einen **Namen** für Ihre App ein.
    2. Wählen Sie **Unterstützte Kontotypen** aus, wählen Sie den Kontotyp „Einzelmandant“ oder „Mehrfachmandant“ aus. ¹
    * Lassen Sie **URI umleiten** leer.
    3. Wählen Sie **Registrieren** aus.
1. Kopieren Sie auf der Übersichtsseite den **Application (client) ID** und speichern Sie ihn. Sie müssen ihn später haben, wenn Sie Ihr Teams-Anwendungsmanifest aktualisieren.
1. Wählen Sie unter **Verwalten** die Option **Eine API verfügbar machen** aus.

    > [!NOTE]
    >
    > * Wenn Sie eine App mit einem Bot und einer Registerkarte erstellen, geben Sie den Anwendungs-ID-URI als `api://fully-qualified-domain-name.com/botid-{YourBotId}` ein.
    >
    > * Verwenden Sie Kleinbuchstaben als Domänennamen, keine Großbuchstaben. Um beispielsweise einen App-Dienst oder eine Web-App zu erstellen, geben Sie den Basisressourcennamen als `demoapplication` ein, dann wird die URL `https://demoapplication.azurewebsites.net` sein. Wenn Sie jedoch den Basisressourcennamen als `DemoApplication` verwenden, dann wird die URL `https://DemoApplication.azurewebsites.net` sein und wird in Desktop, Web und iOS unterstützt, aber nicht in Android.

1. Wählen Sie den Link **Festlegen** aus, um die Anwendungs-ID-URI im Formular `api://{AppID}` zu generieren. Fügen Sie Ihren vollqualifizierten Domänennamen mit am Ende angehängten Schrägstrich „/“ zwischen den doppelten Schrägstrichen und der GUID ein. Die gesamte ID muss die Form von `api://fully-qualified-domain-name.com/{AppID}` aufweisen. ² Zum Beispiel `api://subdomain.example.com/00000000-0000-0000-0000-000000000000`. Der vollqualifizierte Domänenname ist der lesbare Domänenname, aus dem Ihre App bereitgestellt wird. Wenn Sie einen Tunneldienst wie ngrok verwenden, müssen Sie diesen Wert aktualisieren, wenn sich Ihre ngrok-Unterdomäne ändert.
1. Wählen Sie **Bereich hinzufügen** aus. Geben Sie im Bereich, der nun geöffnet wird, **access_as_user** für **Bereichsname** ein.
1. Geben Sie im Feld **Wer kann zustimmen?** **Administratoren und Benutzer** ein.
1. Geben Sie die Details in die Felder für die Konfiguration der Aufforderungen zur Administrator- und Benutzereinwilligung mit werten ein, die für den Bereich geeignet `access_as_user` sind:
    * **Titel der Administratoreinwilligung**: Teams kann auf das Benutzerprofil zugreifen.
    * **Beschreibung der Administratoreinwilligung**: Teams können die Web-APIs der App als aktueller Benutzer aufrufen.
    * **Titel der Benutzereinwilligung**: Teams können auf Ihr Profil zugreifen und Anforderungen in Ihrem Namen senden.
    * **Beschreibung der Benutzereinwilligung**: Teams können die APIs dieser App mit denselben Rechten wie Sie aufrufen.
1. Stellen Sie sicher, **Zustand** auf **Aktiviert** festgelegt ist.
1. Wählen Sie **Bereich hinzufügen** aus, um die Details zu speichern. Der Domänenteil des **Bereichsnamen**, der unter dem Textfeld angezeigt wird, muss automatisch mit dem im vorherigen Schritt festgelegten **Anwendungs-ID**-URI übereinstimmen, wobei `/access_as_user` an das Ende `api://subdomain.example.com/00000000-0000-0000-0000-000000000000/access_as_user` angefügt wird.
1. Identifizieren Sie im Bereich **Autorisierte Clientanwendungen** die Anwendungen, die Sie für die Webanwendung Ihrer App autorisieren möchten. **Hinzufügen einer Clientanwendung** auswählen. Geben Sie jede der folgenden Client-IDs ein, und wählen Sie den autorisierten Bereich aus, den Sie im vorherigen Schritt erstellt haben:
    * `1fec8e78-bce4-4aaf-ab1b-5451cc387264` für Teams Mobile oder Desktopanwendung.
    * `5e3ce6c0-2b1f-4285-8d4b-75ee78787346` für Teams-Webanwendung.
1. Navigieren Sie zu **API-Berechtigungen**. Wählen Sie **Eine Berechtigung Hinzufügen** > **Microsoft Graph** > **Delegierte Berechtigungen** aus, und fügen Sie dann die folgenden Berechtigungen aus Graph-API hinzu:
    * User.Read ist standardmäßig aktiviert
    * email
    * offline_access
    * OpenId
    * Profil

1. Navigieren Sie zur **Authentifizierung**.

    > [!IMPORTANT]
    > Wenn einer App keine IT-Administratorzustimmung erteilt wurde, müssen Benutzer die Zustimmung erteilen, wenn sie eine App zum ersten Mal verwenden.

    So geben Sie einen Umleitungs-URI:
    * Wählen Sie **Plattform hinzufügen** aus.
    * Klicken Sie auf **Web**.
    * Geben Sie den **Umleitungs-URI** für Ihre App ein. Dieser URI ist der gleiche vollqualifizierte Domänenname, den Sie in Schritt 5 eingegeben haben. Es folgt auch die API-Route, an die eine Authentifizierungsantwort gesendet wird. Wenn Sie einem der Teams-Beispiele folgen, lautet der URI `https://subdomain.example.com/auth-end`. Weitere Informationen finden Sie unter [OAuth 2.0-Autorisierungscodefluss](/azure/active-directory/develop/v2-oauth2-auth-code-flow).

    > [!NOTE]
    > Für Registerkarten-SSO ist keine implizite Genehmigung erforderlich.

Glückwunsch! Sie haben die Voraussetzungen für die App-Registrierung erfüllt, um mit Ihrer Registerkarten-SSO-App fortzufahren.

> [!NOTE]
>
> * ¹ Wenn Ihre Azure AD-App im selben Mandanten registriert ist, in dem Sie eine Authentifizierungsanforderung in Teams stellen, kann der Benutzer nicht zur Zustimmung aufgefordert werden und erhält sofort ein Zugriffstoken. Benutzer stimmen diesen Berechtigungen nur zu, wenn die Azure AD-App in einem anderen Mandanten registriert ist.
> * ² Wenn die benutzerdefinierte Domäne nicht zu Azure AD hinzugefügt wird, erhalten Sie eine Fehlermeldung, die besagt, dass der Hostname nicht auf einer bereits im Besitz befindlichen Domäne basieren darf. Wenn Sie zu Azure AD eine benutzerdefinierte Domäne hinzufügen und registrieren möchten, befolgen Sie die Prozedur [Einen benutzerdefinierten Domänennamen zu Azure AD hinzuzufügen](/azure/active-directory/fundamentals/add-custom-domain), und wiederholen Sie dann Schritt 5. Dieser Fehler kann bei Ihnen auch aufträten, wenn Sie nicht mit den Anmeldeinformationen eines Administrators beim Office 365-Mandanten angemeldet sind.
> * Wenn Sie den Benutzerprinzipalnamen (User Principal Name, UPN) im zurückgegebenen Zugriffstoken nicht erhalten, können Sie ihn als [Optionalen Anspruch](/azure/active-directory/develop/active-directory-optional-claims) in Azure AD hinzufügen.

### <a name="2-update-your-teams-application-manifest"></a>2. Aktualisieren Des Teams-Anwendungsmanifests

Verwenden Sie den folgenden Code, um ihrem Teams Manifest neue Eigenschaften hinzuzufügen:

```json
"webApplicationInfo": {
  "id": "00000000-0000-0000-0000-000000000000",
  "resource": "api://subdomain.example.com/00000000-0000-0000-0000-000000000000"
}
```

* **WebApplicationInfo** ist das übergeordnete Element der folgenden Elemente:

> [!div class="checklist"]
>
> * **id** – Die Client-ID der Anwendung. Dies ist die Anwendungs-ID, die Sie beim Registrieren der Anwendung bei Azure AD erhalten haben.
>* **ressource** – Die Domäne und Unterdomäne Ihrer Anwendung. Hierbei handelt es sich um den gleichen URI (einschließlich des Protokolls `api://`), den Sie bei der Erstellung Ihres `scope` im Schritt 6 verwendet haben. Sie dürfen den Pfad `access_as_user` nicht in Ihre Ressource einschließen. Der Domänenteil dieses URI muss mit der Domäne übereinstimmen, einschließlich aller Unterdomänen, die in den URLs Ihres Teams-Anwendungsmanifests verwendet werden.
> [!NOTE]
>
>* Die Ressource für eine Azure AD-App ist in der Regel der Stamm der Website-URL und der App-ID (z. B. `api://subdomain.example.com/00000000-0000-0000-0000-000000000000`). Dieser Wert wird auch verwendet, um sicherzustellen, dass Ihre Anforderung von derselben Domäne stammt. Stellen Sie sicher, dass die `contentURL` für Ihre Registerkarte dieselben Domänen wie Ihre Ressourceneigenschaft verwendet.
>* Sie müssen die Manifestversion 1.5 oder höher verwenden, um das Feld `webApplicationInfo` zu implementieren.

### <a name="3-get-an-access-token-from-your-client-side-code"></a>3. Abrufen eines Zugriffstokens aus ihrem clientseitigen Code

> [!NOTE]
> Um Fehler wie beispielsweise `Teams SDK Error: resourceDisabled` zu vermeiden, stellen Sie sicher, dass der Anwendungs-ID-URI in Azure AD App-Registrierung und in Ihrer Teams-App ordnungsgemäß konfiguriert ist.

Verwenden Sie die folgende Authentifizierungs-API:

```javascript
var authTokenRequest = {
  successCallback: function(result) { console.log("Success: " + result); },
  failureCallback: function(error) { console.log("Failure: " + error); }
};
microsoftTeams.authentication.getAuthToken(authTokenRequest);
```

Wenn Sie `getAuthToken` anrufen und die Zustimmung des Benutzers für Berechtigungen auf Benutzerebene erforderlich ist, wird dem Benutzer ein Dialogfeld angezeigt, um seine Zustimmung zu erteilen.

Nachdem Sie das Zugriffstoken im Erfolgsrückruf erhalten haben, decodieren Sie das Zugriffstoken, um Ansprüche für dieses Token anzuzeigen. Optional können Sie das Zugriffstoken manuell kopieren und in ein Tool einfügen, z. B.[jwt.ms](https://jwt.ms/). Wenn Sie den UPN im zurückgegebenen Zugriffstoken nicht erhalten, fügen Sie ihn als [optionalen Anspruch](/azure/active-directory/develop/active-directory-optional-claims) in Azure AD hinzu. Weitere Informationen finden Sie unter [Zugriffstoken](/azure/active-directory/develop/access-tokens).

<p>
    <img src="~/assets/images/tabs/tabs-sso-prompt.png" alt="Tab single sign-on SSO dialog prompt" width="75%"/>
</p>

## <a name="code-snippets"></a>Codeausschnitte

Der folgende Code enthält ein Beispiel für den On-Behalf-of-Fluss zum Abrufen des Zugriffstokens mithilfe der MSAL-Bibliothek:

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

```javascript

// Exchange cliend side token with server token
  app.post('/getProfileOnBehalfOf', function(req, res) {
        var tid = < "Tenand id" >
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

## <a name="code-sample"></a>Codebeispiel

|**Beispielname**|**Beschreibung**|**C#**|**Node.js**|
|---------------|---------------|------|--------------|
| Registerkarten-SSO |Microsoft Teams-Beispiel-App für Azure AD SSO-Registerkarten| [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-sso/csharp)|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/blob/main/samples/tab-sso/nodejs), </br>[Teams Toolkit](../../../toolkit/visual-studio-code-tab-sso.md)|

## <a name="known-limitations"></a>Bekannte Einschränkungen

### <a name="get-an-access-token-with-graph-permissions"></a>Abrufen eines Zugriffstokens mit Graph-Berechtigungen

Unsere aktuelle Implementierung für SSO erteilt nur die Zustimmung für Berechtigungen auf Benutzerebene, die nicht für Graph-Aufrufe verwendet werden können. Um die Berechtigungen (Bereiche) abzurufen, die zum Ausführen eines Graph-Aufrufs erforderlich sind, müssen SSO-Lösungen einen benutzerdefinierten Webdienst implementieren, um das vom Teams JavaScript SDK empfangene Token gegen ein Token auszutauschen, das die erforderlichen Bereiche enthält. Dies wird mithilfe des Azure AD-[On-Behalf-Of-Fluss](/azure/active-directory/develop/v1-oauth2-on-behalf-of-flow) erreicht.

### <a name="tenant-admin-consent"></a>Mandantenadministratorzustimmung

Eine einfache Möglichkeit, im Namen einer Organisation als Mandantenadministrator zuzustimmen, besteht darin, auf `https://login.microsoftonline.com/common/adminconsent?client_id=<AAD_App_ID>` zu verweisen.

#### <a name="ask-for-consent-using-the-auth-api"></a>Anfordern der Zustimmung mithilfe der Auth-API

Ein weiterer Ansatz zum Abrufen von Graph-Bereichen besteht darin, ein Zustimmungsdialogfeld mithilfe unseres vorhandenen [webbasierten Azure AD-Authentifizierungsansatzes](~/tabs/how-to/authentication/auth-tab-aad.md#navigate-to-the-authorization-page-from-your-pop-up-page) anzuzeigen. Bei diesem Ansatz wird ein Azure AD-Zustimmungsdialogfeld angezeigt.

Führen Sie die folgenden Schritte aus, um mithilfe der Auth-API um zusätzliche Zustimmung zu bitten:

1. Das abgerufene Token `getAuthToken()` muss serverseitig mit dem Azure AD-[On-Behalf-Of-Fluss](/azure/active-directory/develop/v2-oauth2-on-behalf-of-flow) ausgetauscht werden, um Zugriff auf diese anderen Graph-APIs zu erhalten. Stellen Sie sicher, dass Sie den v2-Graph-Endpunkt für diesen Austausch verwenden.
2. Wenn der Austausch fehlschlägt, gibt Azure AD eine Ausnahme für ungültige Genehmigungen zurück. Es gibt in der Regel eine von zwei Fehlermeldungen, `invalid_grant` oder `interaction_required`.
3. Wenn der Austausch fehlschlägt, müssen Sie die Zustimmung anfordern. Zeigen Sie eine Benutzeroberfläche an, auf der der Benutzer aufgefordert wird, eine andere Zustimmung zu erteilen. Diese Benutzeroberfläche muss eine Schaltfläche enthalten, die ein Azure AD-Zustimmungsdialogfeld mithilfe unserer [Azure AD-Authentifizierungs-API](~/concepts/authentication/auth-silent-aad.md) auslöst.
4. Wenn Sie weitere Zustimmungen von Azure AD anfordern, müssen Sie `prompt=consent` in den [Abfragezeichenfolgenparameter](~/tabs/how-to/authentication/auth-silent-aad.md#get-the-user-context) in Azure AD einschließen, andernfalls fragt Azure AD nicht nach den anderen Bereichen.
    * Anstelle von `?scope={scopes}`
    * Verwenden Sie `?prompt=consent&scope={scopes}`
    * Stellen Sie sicher, dass `{scopes}` alle Bereiche enthält, für die Sie den Benutzer auffordern, z. B. Mail.Read oder User.Read.
5. Nachdem der Benutzer mehr Berechtigungen erteilt hat, wiederholen Sie den On-Behalf-Of-Fluss, um Zugriff auf diese anderen APIs zu erhalten.

### <a name="non-azure-ad-authentication"></a>Nicht-Azure AD-Authentifizierung

Die oben beschriebene Authentifizierungslösung funktioniert nur für Apps und Dienste, die Azure AD als Identitätsanbieter unterstützen. Apps, die sich mit nicht-Azure AD-basierten Diensten authentifizieren möchten, müssen weiterhin den Popup-basierten [Webauthentifizierungsfluss](~/concepts/authentication.md) verwenden.

> [!NOTE]
> SSO wird für Apps im Besitz von Kunden innerhalb der Azure AD B2C-Mandanten unterstützt.

## <a name="step-by-step-guides"></a>Schritt-für-Schritt-Anleitungen

* Befolgen Sie die [schrittweise Anleitung](../../../sbs-tabs-and-messaging-extensions-with-sso.yml) zum Authentifizieren von Registerkarten und Nachrichtenerweiterungen.
* Befolgen Sie die [Schritt-für-Schritt-Anleitung](../../../sbs-tab-with-adaptive-cards.yml), um Registerkarten mit adaptiven Karten zu erstellen.

## <a name="see-also"></a>Siehe auch

[Teams-Bot mit einmaligem Anmelden](../../../sbs-bots-with-sso.yml)
