---
title: Unterstützung für einmaliges Anmelden für Registerkarten
description: Beschreibt einmaliges Anmelden (Single Sign-On, SSO)
ms.topic: how-to
ms.localizationpriority: medium
keywords: Teams-Authentifizierungs-SSO AAD Single Sign-On-API
ms.openlocfilehash: 107c03fe7ecb2bc6fd38ede7797e6a2a23bac012
ms.sourcegitcommit: 9a06b09ea4bd265096b35c792aa43cf1c0671d5d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/23/2021
ms.locfileid: "61598948"
---
# <a name="single-sign-on-sso-support-for-tabs"></a>SSO-Unterstützung (Single Sign-On) für Registerkarten

Benutzer melden sich bei Microsoft Teams über ihr Geschäfts-, Schul- oder Microsoft-Konto an, das Office 365 Outlook ist. Sie können die Vorteile nutzen, indem Sie eine einmalige Anmeldung ermöglichen, um Ihre Teams Registerkarte oder ihr Aufgabenmodul auf Desktop- oder mobilen Clients zu autorisieren. Wenn sich ein Benutzer einmal anmeldet, muss er sich nicht erneut auf einem anderen Gerät anmelden, da er automatisch angemeldet ist. Ihr Zugriffstoken wird ebenfalls vorab abgerufen, um die Leistung und die Ladezeiten zu verbessern.

> [!NOTE]
> **Teams versionen mobiler Clients, die SSO unterstützen**  
>
> ✔Teams für Android (1416/1.0.0.2020073101 und höher)
>
> ✔Teams für iOS (_Version:_ 2.0.18 und höher)  
> 
> ✔Teams JavaScript SDK _(Version:_ 1.10 und höher) für SSO, um im Besprechungsseitigen Bereich zu arbeiten. 
>
> Um eine optimale Erfahrung mit Teams zu erzielen, verwenden Sie die neueste Version von iOS und Android.

> [!NOTE]
> **Schnellstart**  
>
> Der einfachste Weg für die ersten Schritte mit Registerkarten-SSO ist das Teams-Toolkit für Visual Studio Code. Weitere Informationen finden Sie unter [SSO mit Teams Toolkit und Visual Studio Code für Registerkarten.](../../../toolkit/visual-studio-code-tab-sso.md)

## <a name="how-sso-works-at-runtime"></a>Funktionsweise von SSO zur Laufzeit

Die folgende Abbildung zeigt, wie der SSO-Prozess funktioniert:

<!-- markdownlint-disable MD033 -->
<img src="~/assets/images/tabs/tabs-sso-diagram.png" alt="Tab single sign-on SSO diagram" width="75%"/>

1. In der Registerkarte wird ein JavaScript-Aufruf an `getAuthToken()` durchgeführt. `getAuthToken()`weist Teams an, ein Zugriffstoken für die Registerkartenanwendung abzurufen.
2. Wenn der aktuelle Benutzer Ihre Registerkartenanwendung zum ersten Mal verwendet, wird eine Aufforderung zur Zustimmung angefordert, wenn eine Zustimmung erforderlich ist. Alternativ gibt es eine Anforderungsaufforderung für die Verarbeitung der Schrittauthentifizierung, z. B. die zweistufige Authentifizierung.
3. Teams fordert das Registerkartenzugriffstoken vom Azure Active Directory(AAD)-Endpunkt für den aktuellen Benutzer an.
4. AAD sendet das Registerkartenzugriffstoken an die Teams Anwendung.
5. Teams sendet das Registerkartenzugriffstoken als Teil des ergebnisobjekts, das vom Aufruf zurückgegeben wird, an die `getAuthToken()` Registerkarte.
6. Das Token wird in der Registerkartenanwendung mithilfe von JavaScript analysiert, um die erforderlichen Informationen wie die E-Mail-Adresse des Benutzers zu extrahieren.

> [!NOTE]
> Dies `getAuthToken()` gilt nur für die Zustimmung zu einer begrenzten Gruppe von APIs auf Benutzerebene, die E-Mail, Profil, offline_access und OpenId sind. Es wird nicht für weitere Graph Bereichen wie `User.Read` oder `Mail.Read` verwendet. Empfohlene Problemumgehungen finden Sie unter [Abrufen eines Zugriffstokens mit Graph Berechtigungen.](#get-an-access-token-with-graph-permissions)

Die SSO-API funktioniert auch in [Aufgabenmodulen,](../../../task-modules-and-cards/what-are-task-modules.md) die Webinhalte einbetten.

## <a name="develop-an-sso-microsoft-teams-tab"></a>Entwickeln einer SSO-Microsoft Teams-Registerkarte

In diesem Abschnitt werden die Aufgaben zum Erstellen einer Teams Registerkarte beschrieben, die SSO verwendet. Diese Aufgaben sind sprach- und frameworkunabhängig.

### <a name="1-create-your-aad-application"></a>1. Erstellen Der AAD-Anwendung

> [!NOTE]
> Es gibt einige wichtige Einschränkungen, die Sie kennen müssen:
>
> * Es werden nur Graph API-Berechtigungen auf Benutzerebene unterstützt, d. h. E-Mail, Profil, offline_access, OpenId. Wenn Sie Zugriff auf andere Graph Bereiche haben müssen, z. B. `User.Read` oder , finden Sie weitere Informationen unter Abrufen eines `Mail.Read` [Zugriffstokens mit Graph Berechtigungen.](#get-an-access-token-with-graph-permissions)
> * Es ist wichtig, dass der Domänenname Ihrer Anwendung mit dem Domänennamen übereinstimmt, den Sie für Ihre AAD-Anwendung registriert haben.
> * Derzeit werden mehrere Domänen pro App nicht unterstützt.
> * Der Benutzer muss `accessTokenAcceptedVersion` `2` dies für eine neue Anwendung festlegen.

**So registrieren Sie Ihre App über das AAD Portal**

1. Registrieren Sie eine neue Anwendung im [AAD App-Registrierungsportal.](https://go.microsoft.com/fwlink/?linkid=2083908)
1. Wählen Sie **"Neue Registrierung"** aus. Die Seite **"Anwendung registrieren"** wird angezeigt.
1. Geben Sie auf der Seite **"Anwendung registrieren"** die folgenden Werte ein:
    1. Geben Sie einen **Namen** für Ihre App ein.
    2. Wählen Sie die **unterstützten Kontotypen** aus, wählen Sie den Kontotyp "Einzelner Mandant" oder "Mehrinstanzenkonto" aus. ¹
    * Lassen Sie **URI umleiten** leer.
    3. Wählen Sie **Registrieren** aus.
1. Kopieren und speichern Sie auf der Übersichtsseite die **Anwendungs-ID (Client-ID).** Sie müssen ihn später haben, wenn Sie Ihr Teams Anwendungsmanifest aktualisieren.
1. Wählen Sie unter **Verwalten** die Option **Eine API verfügbar machen** aus.

    > [!NOTE]
    > Wenn Sie eine App mit einem Bot und einer Registerkarte erstellen, geben Sie den Anwendungs-ID-URI als `api://fully-qualified-domain-name.com/botid-{YourBotId}` .

1. Wählen Sie den Link **"Festlegen"** aus, um den Anwendungs-ID-URI in Form von zu `api://{AppID}` generieren. Fügen Sie Ihren vollqualifizierten Domänennamen mit einem schrägen Schrägstrich "/" an das Ende zwischen den doppelten Schrägstrichen und der GUID ein. Die gesamte ID muss die Form von `api://fully-qualified-domain-name.com/{AppID}` aufweisen. ² Beispiel: `api://subdomain.example.com/00000000-0000-0000-0000-000000000000` . Der vollqualifizierte Domänenname ist der lesbare Domänenname, aus dem Ihre App bereitgestellt wird. Wenn Sie einen Tunneldienst wie ngrok verwenden, müssen Sie diesen Wert aktualisieren, wenn sich Ihre ngrok-Unterdomäne ändert.
1. Wählen Sie **Bereich hinzufügen**. Geben Sie im daraufhin geöffneten Bereich **access_as_user** als **Bereichsnamen** ein.
1. Geben Sie im Feld **Wer zustimmen können?** **Administratoren und Benutzer** ein.
1. Geben Sie die Details in die Felder für die Konfiguration der Aufforderungen zur Administrator- und Benutzerzustimmung mit werten ein, die für den Bereich geeignet `access_as_user` sind:
    * **Titel der Administratoreinwilligung**: Teams kann auf das Benutzerprofil zugreifen.
    * Beschreibung der **Administratorzustimmung:** Teams können die Web-APIs der App als aktueller Benutzer aufrufen.
    * Titel der **Benutzergenehmigung:** Teams können auf Ihr Profil zugreifen und Anforderungen in Ihrem Auftrag stellen.
    * Beschreibung der **Benutzergenehmigung:** Teams können die APIs dieser App mit den gleichen Rechten aufrufen wie Sie.
1. Stellen Sie sicher, **Zustand** auf **Aktiviert** festgelegt ist.
1. Wählen Sie **"Bereich hinzufügen"** aus, um die Details zu speichern. Der Domänenteil des **Bereichsnamens,** der unterhalb des Textfelds angezeigt wird, muss automatisch mit dem im vorherigen Schritt festgelegten **Anwendungs-ID-URI** übereinstimmen, `/access_as_user` wobei er am Ende angefügt `api://subdomain.example.com/00000000-0000-0000-0000-000000000000/access_as_user` wird.
1. Identifizieren Sie im Abschnitt **"Autorisierte Clientanwendungen"** die Anwendungen, die Sie für die Webanwendung Ihrer App autorisieren möchten. Wählen Sie **"Clientanwendung hinzufügen"** aus. Geben Sie jede der folgenden Client-IDs ein, und wählen Sie den autorisierten Bereich aus, den Sie im vorherigen Schritt erstellt haben:
    * `1fec8e78-bce4-4aaf-ab1b-5451cc387264`für Teams Mobile- oder Desktopanwendung.
    * `5e3ce6c0-2b1f-4285-8d4b-75ee78787346`für Teams Webanwendung.
1. Navigieren Sie zu **API-Berechtigungen.** Wählen **Sie "Microsoft** Graph Delegierte Berechtigungen" eine Berechtigung hinzufügen  >    >  aus, und fügen Sie dann die folgenden Berechtigungen aus Graph API hinzu:
    * User.Read ist standardmäßig aktiviert
    * email
    * offline_access
    * Openid
    * Profil

1. Navigieren Sie zur **Authentifizierung.**

    > [!IMPORTANT]
    > Wenn einer App keine IT-Administratorzustimmung erteilt wurde, müssen Benutzer die Zustimmung erteilen, wenn sie eine App zum ersten Mal verwenden.

    So geben Sie einen Umleitungs-URI ein:
    * Wählen Sie **"Plattform hinzufügen"** aus.
    * Wählen Sie **"Web"** aus.
    * Geben Sie den **Umleitungs-URI** für Ihre App ein. Dieser URI ist der gleiche vollqualifizierte Domänenname, den Sie in Schritt 5 eingegeben haben. Es folgt auch die API-Route, an die eine Authentifizierungsantwort gesendet wird. Wenn Sie einem der Teams Beispiele folgen, lautet der URI `https://subdomain.example.com/auth-end` . Weitere Informationen finden Sie unter [OAuth 2.0-Autorisierungscodefluss.](/azure/active-directory/develop/v2-oauth2-auth-code-flow)

    > [!NOTE]
    > Für Tab-SSO ist keine implizite Genehmigung erforderlich.

Herzlichen Glückwunsch! Sie haben die Voraussetzungen für die App-Registrierung erfüllt, um mit Ihrer Registerkarten-SSO-App fortzufahren.

> [!NOTE]
>
> * Wenn Ihre AAD-App im selben Mandanten registriert ist, in dem Sie eine Authentifizierungsanforderung in Teams stellen, kann der Benutzer nicht zur Zustimmung aufgefordert werden und erhält sofort ein Zugriffstoken. Benutzer stimmen diesen Berechtigungen nur zu, wenn die AAD App in einem anderen Mandanten registriert ist.
> * ² Wenn die benutzerdefinierte Domäne nicht zu AAD hinzugefügt wird, erhalten Sie einen Fehler, der besagt, dass der Hostname nicht auf einer bereits im Besitz befindlichen Domäne basieren darf. Um AAD eine benutzerdefinierte Domäne hinzuzufügen und zu registrieren, folgen Sie dem [Hinzufügen eines benutzerdefinierten Domänennamens zu AAD](/azure/active-directory/fundamentals/add-custom-domain) Prozedur, und wiederholen Sie dann Schritt 5. Sie können diesen Fehler auch erhalten, wenn Sie nicht mit Administratoranmeldeinformationen im Office 365 Mandanten angemeldet sind.
> * Wenn Sie den Benutzerprinzipalnamen (USER Principal Name, UPN) im zurückgegebenen Zugriffstoken nicht erhalten, können Sie ihn als [optionalen Anspruch](/azure/active-directory/develop/active-directory-optional-claims) in AAD hinzufügen.

### <a name="2-update-your-teams-application-manifest"></a>2. Aktualisieren Des Teams Anwendungsmanifests

Verwenden Sie den folgenden Code, um ihrem Teams Manifest neue Eigenschaften hinzuzufügen:

```json
"webApplicationInfo": {
  "id": "00000000-0000-0000-0000-000000000000",
  "resource": "api://subdomain.example.com/00000000-0000-0000-0000-000000000000"
}
```

* **WebApplicationInfo** ist das übergeordnete Element der folgenden Elemente:

> [!div class="checklist"]
> * **id** – Die Client-ID der Anwendung. Dies ist die Anwendungs-ID, die Sie beim Registrieren der Anwendung bei Azure AD erhalten haben.
>* **ressource** – Die Domäne und Unterdomäne Ihrer Anwendung. Dies ist der gleiche URI (einschließlich des `api://` Protokolls), den Sie beim Erstellen des in Schritt 6 registriert `scope` haben. Sie dürfen den Pfad nicht `access_as_user` in Ihre Ressource einschließen. Der Domänenteil dieses URI muss mit der Domäne übereinstimmen, einschließlich aller Unterdomänen, die in den URLs Ihres Teams Anwendungsmanifests verwendet werden.

> [!NOTE]
>
>* Die Ressource für eine AAD App ist in der Regel der Stamm der Website-URL und der appID (z. B. `api://subdomain.example.com/00000000-0000-0000-0000-000000000000` ). Dieser Wert wird auch verwendet, um sicherzustellen, dass Ihre Anforderung von derselben Domäne stammt. Stellen Sie sicher, dass die `contentURL` Registerkarte dieselben Domänen wie Ihre Ressourceneigenschaft verwendet.
>* Sie müssen die Manifestversion 1.5 oder höher verwenden, um das Feld zu `webApplicationInfo` implementieren.

### <a name="3-get-an-access-token-from-your-client-side-code"></a>3. Abrufen eines Zugriffstokens aus ihrem clientseitigen Code

Verwenden Sie die folgende Authentifizierungs-API:

```javascript
var authTokenRequest = {
  successCallback: function(result) { console.log("Success: " + result); },
  failureCallback: function(error) { console.log("Failure: " + error); }
};
microsoftTeams.authentication.getAuthToken(authTokenRequest);
```

Wenn Sie anrufen `getAuthToken` und die Zustimmung des Benutzers für Berechtigungen auf Benutzerebene erforderlich ist, wird dem Benutzer ein Dialogfeld angezeigt, um seine Zustimmung zu erteilen.

Nachdem Sie das Zugriffstoken im Erfolgsrückruf erhalten haben, decodieren Sie das Zugriffstoken, um Ansprüche für dieses Token anzuzeigen. Optional können Sie das Zugriffstoken manuell kopieren und in ein Tool einfügen, z. [B. jwt.ms](https://jwt.ms/). Wenn Sie den UPN im zurückgegebenen Zugriffstoken nicht erhalten, fügen Sie ihn als [optionalen Anspruch](/azure/active-directory/develop/active-directory-optional-claims) in AAD hinzu. Weitere Informationen finden Sie unter [Zugriffstoken.](/azure/active-directory/develop/access-tokens)

<p>
    <img src="~/assets/images/tabs/tabs-sso-prompt.png" alt="Tab single sign-on SSO dialog prompt" width="75%"/>
</p>

## <a name="code-sample"></a>Codebeispiel

|**Beispielname**|**Beschreibung**|**C#**|**Node.js**|
|---------------|---------------|------|--------------|
| Registerkarten-SSO |Microsoft Teams Beispiel-App für Registerkarten Azure AD SSO| [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-sso/csharp)|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/blob/main/samples/tab-sso/nodejs), </br>[Teams Toolkit](../../../toolkit/visual-studio-code-tab-sso.md)|

## <a name="known-limitations"></a>Bekannte Einschränkungen

### <a name="get-an-access-token-with-graph-permissions"></a>Abrufen eines Zugriffstokens mit Graph Berechtigungen

Unsere aktuelle Implementierung für SSO erteilt nur die Zustimmung für Berechtigungen auf Benutzerebene, die nicht für Graph Aufrufe verwendet werden können. Um die Berechtigungen (Bereiche) abzurufen, die zum Ausführen eines Graph Aufrufs erforderlich sind, müssen SSO-Lösungen einen benutzerdefinierten Webdienst implementieren, um das vom Teams JavaScript SDK abgerufene Token gegen ein Token auszutauschen, das die erforderlichen Bereiche enthält. Dies geschieht mithilfe [des Im-Auftrag-von-Flusses AAD.](/azure/active-directory/develop/v1-oauth2-on-behalf-of-flow)

#### <a name="tenant-admin-consent"></a>Mandantenadministratorzustimmung

Eine einfache Möglichkeit, im Namen einer Organisation als Mandantenadministrator zuzustimmen, besteht darin, auf diese zu `https://login.microsoftonline.com/common/adminconsent?client_id=<AAD_App_ID>` verweisen.

#### <a name="ask-for-consent-using-the-auth-api"></a>Anfordern der Zustimmung mithilfe der Auth-API

Ein weiterer Ansatz zum Abrufen Graph Bereichen besteht darin, ein Zustimmungsdialogfeld mithilfe unseres vorhandenen [webbasierten Azure AD Authentifizierungsansatz zu](~/tabs/how-to/authentication/auth-tab-aad.md#navigate-to-the-authorization-page-from-your-pop-up-page)präsentieren. Bei diesem Ansatz wird ein Azure AD Zustimmungsdialogfeld angezeigt.

**So fordern Sie eine zusätzliche Zustimmung mithilfe der Auth-API an**

1. Das abgerufene Token `getAuthToken()` muss serverseitig mit AAD [Im-Auftrag-von-Fluss](/azure/active-directory/develop/v2-oauth2-on-behalf-of-flow) ausgetauscht werden, um Zugriff auf diese anderen Graph-APIs zu erhalten. Stellen Sie sicher, dass Sie den v2-Graph-Endpunkt für diesen Austausch verwenden.
2. Wenn der Austausch fehlschlägt, gibt AAD eine Ausnahme für ungültige Genehmigungen zurück. Es gibt in der Regel eine von zwei Fehlermeldungen `invalid_grant` oder `interaction_required` .
3. Wenn der Austausch fehlschlägt, müssen Sie die Zustimmung anfordern. Zeigen Sie eine Benutzeroberfläche an, auf der der Benutzer aufgefordert wird, eine andere Zustimmung zu erteilen. Diese Benutzeroberfläche muss eine Schaltfläche enthalten, die mithilfe unserer [AAD-Authentifizierungs-API](~/concepts/authentication/auth-silent-aad.md)ein AAD Zustimmungsdialogfeld auslöst.
4. Wenn Sie mehr Zustimmung von AAD anfordern, müssen Sie `prompt=consent` den [Abfragezeichenfolgenparameter](~/tabs/how-to/authentication/auth-silent-aad.md#get-the-user-context) in AAD einschließen, andernfalls werden AAD nicht nach den anderen Bereichen gefragt.
    * Statt `?scope={scopes}`
    * Verwenden Sie diese `?prompt=consent&scope={scopes}`
    * Stellen Sie sicher, dass `{scopes}` alle Bereiche enthalten sind, für die Sie den Benutzer auffordern, z. B. Mail.Read oder User.Read.
5. Nachdem der Benutzer mehr Berechtigungen erteilt hat, wiederholen Sie den "Im Auftrag von"-Fluss, um Zugriff auf diese anderen APIs zu erhalten.

### <a name="non-aad-authentication"></a>Nicht-AAD-Authentifizierung

Die oben beschriebene Authentifizierungslösung funktioniert nur für Apps und Dienste, die AAD als Identitätsanbieter unterstützen. Apps, die sich mit nicht AAD basierten Diensten authentifizieren möchten, müssen weiterhin den Popup-basierten [Webauthentifizierungsfluss](~/concepts/authentication.md)verwenden.

> [!NOTE]
> SSO wird für Apps im Besitz von Kunden innerhalb der AAD B2C-Mandanten unterstützt.

## <a name="step-by-step-guides"></a>Schritt-für-Schritt-Anleitungen

* Befolgen Sie die [schrittweise Anleitung](../../../sbs-tabs-and-messaging-extensions-with-sso.yml) zum Authentifizieren von Registerkarten und Messaging-Erweiterungen.
* Befolgen Sie die [schrittweise Anleitung,](../../../sbs-tab-with-adaptive-cards.yml) um Registerkarten mit adaptiven Karten zu erstellen.

## <a name="see-also"></a>Siehe auch
[Teams Bot mit einmaligem Anmelden](../../../sbs-bots-with-sso.yml)
