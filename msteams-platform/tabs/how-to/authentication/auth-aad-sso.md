---
title: Unterstützung für einmaliges Anmelden für Registerkarten
description: Beschreibt einmaliges Anmelden (Single Sign-On, SSO)
ms.topic: how-to
keywords: teams authentication SSO AAD single sign-on api
ms.openlocfilehash: e6bf278e446861556da8362905916cc030df723e
ms.sourcegitcommit: 82bda0599ba2676ab9348c2f4284f73c7dad0838
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2021
ms.locfileid: "51596681"
---
# <a name="single-sign-on-sso-support-for-tabs"></a>Unterstützung für einmaliges Anmelden (Single Sign-On, SSO) für Registerkarten

Benutzer melden sich bei Microsoft Teams über ihre Geschäfts-, Schul- oder Microsoft-Konten an, die Office 365, Outlook und so weiter sind. Sie können dies nutzen, indem Sie einer einmaligen Anmeldung erlauben, Ihre Registerkarte oder Ihr Aufgabenmodul für Teams auf Desktop- oder mobilen Clients zu autorisieren. Wenn ein Benutzer der Verwendung Ihrer App zuwilligt, muss er nicht erneut auf einem anderen Gerät zustimmen, da er automatisch angemeldet ist. Darüber hinaus wird Ihr Zugriffstoken vorab vorkonfetcht, um die Leistung und Ladezeiten zu verbessern.

> [!NOTE]
> **Mobile Clientversionen von Teams, die SSO unterstützen**  
>
> ✔Teams für Android (1416/1.0.0.2020073101 und höher)
>
> ✔Teams für iOS (_Version_: 2.0.18 und höher)  
>
> Verwenden Sie die neueste Version von iOS und Android, um die beste Erfahrung mit Teams zu bieten.

> [!NOTE]
> **Schnellstart**  
>
> Der einfachste Weg zu den ersten Schritten mit registerkarten-SSO ist das Teams Toolkit für Visual Studio Code. Weitere Informationen finden Sie unter [SSO with Teams toolkit and Visual Studio Code for tabs](../../../toolkit/visual-studio-code-tab-sso.md)

## <a name="how-sso-works-at-runtime"></a>Funktionsweise von SSO zur Laufzeit

Die folgende Abbildung zeigt, wie der SSO-Prozess funktioniert:

<!-- markdownlint-disable MD033 -->
<img src="~/assets/images/tabs/tabs-sso-diagram.png" alt="Tab single sign-on SSO diagram" width="75%"/>

1. In der Registerkarte wird ein JavaScript-Aufruf an `getAuthToken()` durchgeführt. Dies weist Teams an, ein Authentifizierungstoken für die Registerkartenanwendung abzurufen.
2. Wenn dies das erste Mal ist, dass der aktuelle Benutzer Ihre Registerkartenanwendung verwendet hat, gibt es eine Anforderungsaufforderung zur Zustimmung, wenn eine Zustimmung erforderlich ist, oder zur Verarbeitung der mehrstufigen Authentifizierung, z. B. der zweistufigen Authentifizierung.
3. Teams fordert das Registerkartenanwendungstoken vom Azure Active Directory (AAD)-Endpunkt für den aktuellen Benutzer an.
4. AAD sendet das Registerkartenanwendungstoken an die Teams-Anwendung.
5. Teams sendet das Registerkartenanwendungstoken als Teil des vom Aufruf zurückgegebenen Ergebnisobjekts an die `getAuthToken()` Registerkarte.
6. Das Token wird in der Registerkartenanwendung mithilfe von JavaScript analysiert, um die erforderlichen Informationen wie die E-Mail-Adresse des Benutzers zu extrahieren.

> [!NOTE]
> Der ist nur gültig für die Zustimmung zu einer begrenzten Gruppe von APIs auf Benutzerebene, d. h. `getAuthToken()` E-Mail, Profil, offline_access und OpenId. Es wird nicht für weitere Graph-Bereiche wie oder `User.Read` `Mail.Read` verwendet. Mögliche Problemumgehungen finden Sie [unter zusätzliche Graph-Bereiche](#apps-that-require-additional-graph-scopes).

Die SSO-API funktioniert auch in [Aufgabenmodulen,](../../../task-modules-and-cards/what-are-task-modules.md) die Webinhalte einbetten.

## <a name="develop-an-sso-microsoft-teams-tab"></a>Entwickeln einer Microsoft Teams-Registerkarte für SSO

In diesem Abschnitt werden die Aufgaben beim Erstellen einer Registerkarte Teams beschrieben, die SSO verwendet. Diese Aufgaben sind sprach- und frameworkunabhängig.

### <a name="1-create-your-aad-application"></a>1. Erstellen Ihrer AAD-Anwendung

**So registrieren Sie Ihre Anwendung im [AAD-Portal](https://azure.microsoft.com/features/azure-portal/) (Übersicht)**

1. Erhalten Sie [Ihre AAD-Anwendungs-ID](/azure/active-directory/develop/howto-create-service-principal-portal#get-values-for-signing-in).
2. Geben Sie die Berechtigungen an, die Ihre Anwendung für den AAD-Endpunkt benötigt, und optional Graph.
3. [Erteilen von Berechtigungen](/azure/active-directory/develop/howto-create-service-principal-portal#configure-access-policies-on-resources) für Desktop-, Web- und mobile Anwendungen von Teams.
4. Autorisieren Sie Teams, indem Sie **die** Schaltfläche Bereich hinzufügen  auswählen und geben Sie in dem geöffneten Bereich access_as_user **Bereichsnamen ein.**

> [!NOTE]
> Es gibt einige wichtige Einschränkungen, die Sie kennen müssen:
>
> * Es werden nur Graph-API-Berechtigungen auf Benutzerebene unterstützt, d. h. E-Mail, Profil, offline_access, OpenId. Wenn Sie Zugriff auf andere Graph-Bereiche wie oder haben `User.Read` `Mail.Read` müssen, lesen Sie [empfohlene Problemumgehung](#apps-that-require-additional-graph-scopes).
> * Es ist wichtig, dass der Domänenname Ihrer Anwendung mit dem Domänennamen identisch ist, den Sie für Ihre AAD-Anwendung registriert haben.
> * Derzeit werden mehrere Domänen pro App nicht unterstützt.
> * Anwendungen, die die Domäne verwenden, werden nicht unterstützt, da sie zu häufig sind `azurewebsites.net` und ein Sicherheitsrisiko darstellen können.

**So registrieren Sie Ihre App über das AAD-Portal**

1. Registrieren Sie eine neue Anwendung im [AAD-App-Registrierungsportal.](https://go.microsoft.com/fwlink/?linkid=2083908)
2. Wählen **Sie Neue Registrierung aus.** Die **Seite Anwendung registrieren** wird angezeigt.
3. Geben Sie **auf der Seite** Anwendung registrieren die folgenden Werte ein:
    1. Geben Sie einen **Namen** für Ihre App ein.
    2. Wählen Sie **die Unterstützten Kontotypen** aus, wählen Sie einzelnen Mandanten- oder mehrstufigen Kontotyp aus. ¹
    * Lassen Sie **URI umleiten** leer.
    3. Wählen Sie **Registrieren** aus.
4. Kopieren und speichern Sie auf der Übersichtsseite die **Anwendungs-ID (Client-ID).** Sie müssen dies später beim Aktualisieren Ihres Teams-Anwendungsmanifests haben.
5. Wählen Sie unter **Verwalten** die Option **Eine API verfügbar machen** aus.
6. Wählen Sie den **Link Set** aus, um den Anwendungs-ID-URI in Form von zu `api://{AppID}` generieren. Fügen Sie Ihren vollqualifizierten Domänennamen mit einem Schrägstrich "/" ein, der am Ende zwischen den doppelten Schrägstrichen und der GUID angefügt ist. Die gesamte ID muss die Form `api://fully-qualified-domain-name.com/{AppID}` haben. ² Beispiel: `api://subdomain.example.com/00000000-0000-0000-0000-000000000000` . Der vollqualifizierte Domänenname ist der lesbare Domänenname für den Menschen, aus dem Ihre App bedient wird. Wenn Sie einen Tunneldienst wie ngrok verwenden, müssen Sie diesen Wert aktualisieren, wenn sich ihre ngrok-Unterdomäne ändert.
7. Wählen Sie **Bereich hinzufügen**. Geben Sie im geöffneten Bereich **access_as_user** als **Bereichsnamen ein.**
8. Geben Sie **im Feld Wer kann zustimmen?** **Admins und Benutzer ein.**
9. Geben Sie die Details in die Felder für die Konfiguration der Administrator- und Benutzer-Zustimmungsaufforderungen mit Werten ein, die für den Bereich geeignet `access_as_user` sind:
    * **Titel der Administratoreinwilligung**: Teams kann auf das Benutzerprofil zugreifen.
    * **Administrator-Zustimmungsbeschreibung:** Teams kann die Web-APIs der App als aktuellen Benutzer aufrufen.
    * **Benutzer-Zustimmungstitel:** Teams kann auf Ihr Profil zugreifen und Anforderungen in Ihrem Namen stellen.
    * **Benutzer-Zustimmungsbeschreibung:** Teams kann die APIs dieser App mit denselben Rechten aufrufen wie Sie.
10. Stellen Sie sicher, **Zustand** auf **Aktiviert** festgelegt ist.
11. Wählen **Sie Bereich hinzufügen aus,** um die Details zu speichern. Der Domänenteil  des Bereichsnamens, der unterhalb des Textfelds angezeigt wird, muss automatisch mit dem **anwendungs-ID-URI** übereinstimmen, der im vorherigen Schritt festgelegt wurde, und am Ende `/access_as_user` angefügt `api://subdomain.example.com/00000000-0000-0000-0000-000000000000/access_as_user` werden.
12. Identifizieren Sie im Abschnitt Autorisierte **Clientanwendungen** die Anwendungen, die Sie für die Webanwendung Ihrer App autorisieren möchten. Wählen **Sie Clientanwendung hinzufügen aus.** Geben Sie die folgenden Client-IDs ein, und wählen Sie den autorisierten Bereich aus, den Sie im vorherigen Schritt erstellt haben:
    * `1fec8e78-bce4-4aaf-ab1b-5451cc387264` für mobile Teams- oder Desktopanwendung.
    * `5e3ce6c0-2b1f-4285-8d4b-75ee78787346` für die Teams-Webanwendung.
13. Navigieren Sie zu **API-Berechtigungen**. Wählen **Sie Microsoft** Graph Delegierte Berechtigungen hinzufügen aus, und fügen Sie dann die folgenden Berechtigungen aus der  >    >  Graph-API hinzu:
    * User.Read standardmäßig aktiviert
    * email
    * offline_access
    * OpenId
    * profile

14. Navigieren Sie zu **Authentifizierung**.

    Wenn einer App keine Zustimmung des IT-Admins erteilt wurde, müssen Benutzer bei der ersten Verwendung einer App ihre Zustimmung erteilen.

    So geben Sie einen Umleitungs-URI ein:
    * Wählen **Sie Plattform hinzufügen aus.**
    * Wählen Sie **Web** aus.
    * Geben Sie den **Umleitungs-URI** für Ihre App ein. Dies ist die Seite, auf der der Benutzer durch einen erfolgreichen impliziten Erteilungsfluss umgeleitet wird. Dies ist derselbe vollqualifizierte Domänenname, den Sie in Schritt 5 eingegeben haben, gefolgt von der API-Route, an die eine Authentifizierungsantwort gesendet wird. Wenn Sie einem der Teams-Beispiele folgen, ist dies `https://subdomain.example.com/auth-end` .

    Aktivieren Sie die implizite Gewährung, indem Sie die folgenden Kontrollkästchen aktivieren: ✔-ID-Token ✔ Zugriffstoken

Glückwunsch! Sie haben die erforderlichen Voraussetzungen für die App-Registrierung erfüllt, um mit der Registerkarte SSO-App fortzufahren.

> [!NOTE]
>
> * ¹ Wenn Ihre AAD-App im selben Mandanten registriert ist, in dem Sie eine Authentifizierungsanforderung in Teams stellen, kann der Benutzer nicht um Zustimmung gebeten werden und erhält sofort ein Zugriffstoken. Benutzer stimmen diesen Berechtigungen nur zu, wenn die AAD-App in einem anderen Mandanten registriert ist.
> * ² Wenn die benutzerdefinierte Domäne nicht zu AAD hinzugefügt wird, wird eine Fehlermeldung angezeigt, die besagt, dass der Hostname nicht auf einer bereits vorhandenen Domäne basieren darf. Um AAD eine benutzerdefinierte Domäne hinzuzufügen und zu registrieren, führen Sie die Schritte zum Hinzufügen eines benutzerdefinierten Domänennamens zur [AAD-Prozedur](/azure/active-directory/fundamentals/add-custom-domain) aus, und wiederholen Sie dann Schritt 5. Sie können diesen Fehler auch erhalten, wenn Sie im Office 365-Mandanz nicht mit Administratoranmeldeinformationen angemeldet sind.
> * Wenn Sie den Benutzerprinzipalnamen (User Principal Name, UPN) im zurückgegebenen Zugriffstoken nicht erhalten, können Sie ihn als [optionalen](https://docs.microsoft.com/azure/active-directory/develop/active-directory-optional-claims) Anspruch in AAD hinzufügen.

### <a name="2-update-your-teams-application-manifest"></a>2. Aktualisieren Des Anwendungsmanifests von Teams

Verwenden Sie den folgenden Code, um Ihrem Teams-Manifest neue Eigenschaften hinzuzufügen:

```json
"webApplicationInfo": {
  "id": "00000000-0000-0000-0000-000000000000",
  "resource": "api://subdomain.example.com/00000000-0000-0000-0000-000000000000"
}
```

* **WebApplicationInfo** ist das übergeordnete Element der folgenden Elemente:

> [!div class="checklist"]
> * **id** – Die Client-ID der Anwendung. Dies ist die Anwendungs-ID, die Sie im Rahmen der Registrierung der Anwendung bei Azure AD erhalten haben.
>* **resource** – Die Domäne und Unterdomäne Ihrer Anwendung. Dies ist der gleiche URI (einschließlich des Protokolls), den Sie beim Erstellen `api://` `scope` in Schritt 6 registriert haben. Sie dürfen den Pfad `access_as_user` nicht in Ihre Ressource verwenden. Der Domänenteil dieses URI muss mit der Domäne übereinstimmen, einschließlich aller Unterdomänen, die in den URLs Ihres Teams-Anwendungsmanifests verwendet werden.

> [!NOTE]
>
>* Die Ressource für eine AAD-App ist in der Regel der Stamm der Website-URL und der appID (z. B. `api://subdomain.example.com/00000000-0000-0000-0000-000000000000` ). Dieser Wert wird auch verwendet, um sicherzustellen, dass Ihre Anforderung von derselben Domäne kommt. Stellen Sie `contentURL` sicher, dass die Für Ihre Registerkarte dieselben Domänen wie Ihre Ressourceneigenschaft verwendet.
>* Sie müssen manifest Version 1.5 oder höher verwenden, um das Feld zu `webApplicationInfo` implementieren.

### <a name="3-get-an-authentication-token-from-your-client-side-code"></a>3. Erhalten eines Authentifizierungstokens aus Ihrem clientseitigen Code

Verwenden Sie die folgende Authentifizierungs-API:

```javascript
var authTokenRequest = {
  successCallback: function(result) { console.log("Success: " + result); },
  failureCallback: function(error) { console.log("Failure: " + error); }
};
microsoftTeams.authentication.getAuthToken(authTokenRequest);
```

Wenn Sie anrufen – und zusätzliche Zustimmung des Benutzers für Berechtigungen auf Benutzerebene erforderlich ist, wird dem Benutzer ein Dialogfeld angezeigt, um zusätzliche `getAuthToken` Zustimmung zu erteilen.

Nachdem Sie das Zugriffstoken im Erfolgsrückruf erhalten haben, können Sie das Zugriffstoken decodieren, um die diesem Token zugeordneten Ansprüche anzeigen zu können. Optional können Sie das Zugriffstoken manuell kopieren und in ein Tool einfügen, z. B. [jwt.ms,](https://jwt.ms/) um den Inhalt zu überprüfen. Wenn Sie den UPN nicht im zurückgegebenen Zugriffstoken erhalten, können Sie ihn als [optionalen](https://docs.microsoft.com/azure/active-directory/develop/active-directory-optional-claims) Anspruch in AAD hinzufügen.

<p>
    <img src="~/assets/images/tabs/tabs-sso-prompt.png" alt="Tab single sign-on SSO dialog prompt" width="75%"/>
</p>

## <a name="code-sample"></a>Codebeispiel

|**Beispielname**|**Beschreibung**|**C#**|**Node.js**|
|---------------|---------------|------|--------------|
| Registerkarte SSO |Microsoft Teams-Beispiel-App für Registerkarten Azure AD SSO| [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-sso/csharp)|[Ansicht](https://github.com/OfficeDev/Microsoft-Teams-Samples/blob/main/samples/tab-sso/nodejs), </br>[Teams Toolkit](../../../toolkit/visual-studio-code-tab-sso.md)|

## <a name="known-limitations"></a>Bekannte Einschränkungen

### <a name="apps-that-require-additional-graph-scopes"></a>Apps, die zusätzliche Graph-Bereiche erfordern

Unsere aktuelle Implementierung für SSO erteilt nur Zustimmung für Berechtigungen auf Benutzerebene, d. h. E-Mail, Profil, offline_access, OpenId und nicht für andere APIs wie User.Read oder Mail.Read. Wenn Ihre App weitere Graph-Bereiche benötigt, werden im nächsten Abschnitt einige Problemumgehungen zur Aktivierung beschrieben.

#### <a name="tenant-admin-consent"></a>Zustimmung des Mandantenadministrators

Der einfachste Ansatz besteht in der Vorab-Zustimmung eines Mandantenadministrators im Namen der Organisation. Dies bedeutet, dass Benutzer diesen Bereich nicht zustimmen müssen, und Sie können dann die Tokenserverseite mithilfe des [AAD-Im-Auftrag-von-Fluss](/azure/active-directory/develop/v1-oauth2-on-behalf-of-flow)austauschen. Diese Problemumgehung ist für interne Geschäftsanwendungen akzeptabel, reicht jedoch nicht für Drittanbieterentwickler aus, die sich nicht auf die Genehmigung des Mandantenadministrators verlassen können.

Eine einfache Möglichkeit der Zustimmung im Namen einer Organisation als Mandantenadministrator besteht im Verweisen auf `https://login.microsoftonline.com/common/adminconsent?client_id=<AAD_App_ID>` .

#### <a name="ask-for-additional-consent-using-the-auth-api"></a>Bitten Sie um zusätzliche Zustimmung mithilfe der Authentifizierungs-API

Ein weiterer Ansatz zum Abrufen zusätzlicher Graph-Bereiche ist das Präsentieren eines Zustimmungsdialogfelds mithilfe unseres vorhandenen webbasierten Azure AD-Authentifizierungsansatzes, bei dem ein Dialogfeld für die Azure [AD-Zustimmung](~/tabs/how-to/authentication/auth-tab-aad.md#navigate-to-the-authorization-page-from-your-popup-page) angezeigt wird. 

**So bitten Sie um zusätzliche Zustimmung mithilfe der Authentifizierungs-API**

1. Das mithilfe abgerufene Token muss serverseitig mithilfe von AAD im Auftrag des Datenflusses ausgetauscht werden, um Zugriff auf diese zusätzlichen `getAuthToken()` [Graph-APIs](/azure/active-directory/develop/v2-oauth2-on-behalf-of-flow) zu erhalten. Stellen Sie sicher, dass Sie den v2 Graph-Endpunkt für diesen Exchange verwenden.
2. Wenn der Exchange fehlschlägt, gibt AAD eine ungültige Erteilungsausnahme zurück. Es gibt in der Regel eine von zwei Fehlermeldungen oder `invalid_grant` `interaction_required` .
3. Wenn der Austausch fehlschlägt, müssen Sie um zusätzliche Zustimmung bitten. Zeigen Sie eine Benutzeroberfläche an, die den Benutzer um zusätzliche Zustimmung bittet. Diese Benutzeroberfläche muss eine Schaltfläche enthalten, die ein AAD-Zustimmungsdialogfeld mit unserer [AAD-Authentifizierungs-API auslöst.](~/concepts/authentication/auth-silent-aad.md)
4. Wenn Sie eine zusätzliche Zustimmung von AAD einholen, müssen Sie `prompt=consent` ihren [Query-string-parameter](~/tabs/how-to/authentication/auth-silent-aad.md#get-the-user-context) in AAD angeben, andernfalls fordert AAD die zusätzlichen Bereiche nicht an.
    * Statt `?scope={scopes}`
    * Verwenden Sie diese `?prompt=consent&scope={scopes}`
    * Stellen Sie sicher, dass alle Bereiche enthalten sind, für die Sie den Benutzer zur Eingabe aufgefordert haben, z. B. `{scopes}` Mail.Read oder User.Read.
5. Nachdem der Benutzer zusätzliche Berechtigungen erteilt hat, wiederholen Sie den Im-Auftrag-von-Fluss, um Zugriff auf diese zusätzlichen APIs zu erhalten.

### <a name="non-aad-authentication"></a>Nicht-AAD-Authentifizierung

Die oben beschriebene Authentifizierungslösung funktioniert nur für Apps und Dienste, die AAD als Identitätsanbieter unterstützen. Apps, die sich mit nicht AAD-basierten Diensten authentifizieren möchten, müssen weiterhin den Pop-up-basierten Webauthentifizierungsfluss [verwenden.](~/concepts/authentication.md)

> [!NOTE]
> SSO wird für Apps im Besitz von Kunden innerhalb der AAD B2C-Mandanten unterstützt.
