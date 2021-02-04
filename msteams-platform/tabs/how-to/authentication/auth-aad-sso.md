---
title: Unterstützung für einmaliges Anmelden für Registerkarten
description: Beschreibt einmaliges Anmelden (Single Sign-On, SSO)
ms.topic: how-to
keywords: Teams authentication SSO AAD single sign-on api
ms.openlocfilehash: ed8b52416dd1499f50d561ceb2c1edf03e5457d3
ms.sourcegitcommit: f74b74d5bed1df193e59f46121ada443fb57277b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2021
ms.locfileid: "50093267"
---
# <a name="single-sign-on-sso-support-for-tabs"></a>Unterstützung für einmaliges Anmelden (Single Sign-On, SSO) für Registerkarten

Benutzer melden sich über ihre Geschäfts-, Schul- oder Microsoft-Konten (Office 365, Outlook usw.) bei Microsoft Teams an. Sie können dies nutzen, indem Sie einer einmaligen Anmeldung erlauben, Ihre Microsoft Teams-Registerkarte (oder Ihr Aufgabenmodul) auf Desktop- oder mobilen Clients zu autorisieren. Wenn ein Benutzer also der Verwendung Ihrer App zuwilligt, muss er nicht erneut auf einem anderen Gerät zustimmen– er wird automatisch angemeldet. Darüber hinaus wird ihr Zugriffstoken vorab vorkonfetcht, um die Leistung und Ladezeiten zu verbessern.

> [!NOTE]
> **Mobile Clientversionen von Teams, die SSO unterstützen**  
>
> ✔Teams für Android (1416/1.0.0.2020073101 und höher)
>
> ✔Teams für iOS (_Version_: 2.0.18 und höher)  
>
> Um teams optimal zu nutzen, verwenden Sie bitte die neueste Version von iOS und Android.

> [!NOTE]
> **Schnellstart**  
>
> Der einfachste Weg für die ersten Schritte mit dem Registerkarten-SSO ist das Microsoft Teams Toolkit for Visual Studio Code. [Weitere Informationen](../../../toolkit/visual-studio-code-tab-sso.md)

## <a name="how-sso-works-at-runtime"></a>Funktionsweise von SSO zur Laufzeit

Das folgende Diagramm zeigt die Funktionsweise des SSO-Prozesses:

<!-- markdownlint-disable MD033 -->
<img src="~/assets/images/tabs/tabs-sso-diagram.png" alt="Tab single sign-on SSO diagram" width="75%"/>

1. Auf der Registerkarte wird ein JavaScript-Aufruf `getAuthToken()` an . Dies weist Teams an, ein Authentifizierungstoken für die Registerkartenanwendung abzurufen.
2. Wenn der aktuelle Benutzer die Registerkartenanwendung zum ersten Mal verwendet hat, wird eine Aufforderung zur Zustimmung (sofern eine Zustimmung erforderlich ist) oder zur Verarbeitung der Schrittweisen Authentifizierung (z. B. zweistufige Authentifizierung) angezeigt.
3. Teams fordert das Registerkartenanwendungstoken vom Azure AD-Endpunkt für den aktuellen Benutzer an.
4. Azure AD sendet das Registerkartenanwendungstoken an die Teams-Anwendung.
5. Teams sendet das Registerkartenanwendungstoken als Teil des Ergebnisobjekts, das vom Aufruf zurückgegeben wird, an die `getAuthToken()` Registerkarte.
6. Das Token wird in der Registerkartenanwendung über JavaScript analysiert, um die erforderlichen Informationen zu extrahieren, z. B. die E-Mail-Adresse des Benutzers.

> [!NOTE]
> Dies gilt nur für die Zustimmung zu einer begrenzten Gruppe von APIs auf Benutzerebene `getAuthToken()` – E-Mail, Profil, offline_access und OpenId – und nicht für weitere Microsoft Graph-Bereiche wie oder `User.Read` `Mail.Read` . In unserem Abschnitt am Ende dieses Dokuments finden Sie Vorschläge für Problemumgehungen, wenn Sie zusätzliche [Graph-Bereiche benötigen.](#apps-that-require-additional-microsoft-graph-scopes)

Die SSO-API funktioniert auch in [Aufgabenmodulen,](../../../task-modules-and-cards/what-are-task-modules.md) die Webinhalte einbetten.

## <a name="develop-an-sso-microsoft-teams-tab"></a>Entwickeln einer Microsoft Teams-SSO-Registerkarte

In diesem Abschnitt werden die Aufgaben beschrieben, die beim Erstellen einer Registerkarte "Teams" mit SSO ausgeführt werden. Diese Aufgaben werden hier sprach- und frameworkunabhängig beschrieben.

### <a name="1-create-your-azure-active-directory-azure-ad-application"></a>1. Erstellen Ihrer Azure Active Directory (Azure AD)-Anwendung

#### <a name="registering-your-application-in-theazure-ad-portal-overview"></a>Registrieren Ihrer Anwendung im[Azure AD-Portal (](https://azure.microsoft.com/features/azure-portal/) Übersicht):

1. Erhalten Sie [Ihre Azure AD-Anwendungs-ID.](/azure/active-directory/develop/howto-create-service-principal-portal#get-values-for-signing-in)
2. Geben Sie die Berechtigungen an, die Ihre Anwendung für den Azure AD-Endpunkt und optional Microsoft Graph benötigt.
3. [Erteilen von Berechtigungen](/azure/active-directory/develop/howto-create-service-principal-portal#configure-access-policies-on-resources) für Desktop-, Web- und mobile Anwendungen von Teams.
4. Autorisieren Sie Teams vorab, indem Sie **die** Schaltfläche "Bereich hinzufügen" auswählen, und geben Sie im bereich, der geöffnet wird, `access_as_user` den **Bereichsnamen ein.**

> [!NOTE]
> Es gibt einige wichtige Einschränkungen, die Sie beachten sollten:
>
> * Wir unterstützen nur Microsoft Graph-API-Berechtigungen auf Benutzerebene, d. h. E-Mail, Profil, offline_access, OpenId. Wenn Sie Zugriff auf andere Microsoft Graph-Bereiche benötigen (z. B. oder ), lesen Sie unsere empfohlene Problemumgehung am Ende `User.Read` `Mail.Read` dieser Dokumentation. [](#apps-that-require-additional-microsoft-graph-scopes)
> * Es ist wichtig, dass der Domänenname Ihrer Anwendung mit dem Domänennamen identisch ist, den Sie für Ihre Azure AD-Anwendung registriert haben.
> * Wir unterstützen derzeit nicht mehrere Domänen pro App.
> * Anwendungen, die die Domäne verwenden, werden nicht unterstützt, da sie zu häufig verwendet werden und `azurewebsites.net` möglicherweise ein Sicherheitsrisiko darstellen. Wir versuchen jedoch aktiv, diese Einschränkung zu entfernen.

#### <a name="registering-your-app-through-the-azure-active-directory-portal-in-depth"></a>Ausführliche Registrierung Ihrer App über das Azure Active Directory-Portal:

1. Registrieren Sie eine neue Anwendung im [Azure Active Directory – App-Registrierungsportal.](https://go.microsoft.com/fwlink/?linkid=2083908)
2. Wählen **Sie "Neue Registrierung"** aus, und legen Sie auf der *Seite "Anwendung registrieren"* die folgenden Werte ein:
    * Legen **Sie den** Namen auf ihren App-Namen.
    * Wählen Sie **die unterstützten Kontotypen** aus (jeder Kontotyp funktioniert) ¹
    * Lassen Sie **URI umleiten** leer.
    * Wählen Sie **Registrieren** aus.
3. Kopieren und speichern Sie auf der Übersichtsseite die **Anwendungs-ID (Client-ID).** Sie benötigen sie später beim Aktualisieren Ihres Teams-Anwendungsmanifests.
4. Wählen Sie unter **Verwalten** die Option **Eine API verfügbar machen** aus. 
5. Wählen Sie den **Link "Set"** aus, um den Anwendungs-ID-URI in Form von zu `api://{AppID}` generieren. Fügen Sie Ihren vollqualifizierten Domänennamen (mit einem Schrägstrich "/" am Ende) zwischen den doppelten Schrägstrichen und der GUID ein. Die gesamte ID sollte die Form `api://fully-qualified-domain-name.com/{AppID}` 1 haben:
    * Beispiel: `api://subdomain.example.com/00000000-0000-0000-0000-000000000000` .
    
    Der vollqualifizierte Domänenname ist der lesbare Domänenname, von dem aus Ihre App bedient wird. Wenn Sie einen Tunnelingdienst wie ngrok verwenden, müssen Sie diesen Wert aktualisieren, sobald sich Ihre ngrok-Unterdomäne ändert. 
6. Wählen Sie die Schaltfläche **Bereich hinzufügen** aus. Geben Sie im Bereich, der geöffnet wird, `access_as_user` für **Bereichsname** ein.
7. Festlegen, **wer zustimmen kann?**`Admins and users`
8. Füllen Sie die Felder für die Konfiguration der Eingabeaufforderungen für Administratoren und Benutzer mit Werten aus, die für den Bereich geeignet `access_as_user` sind:
    * **Titel der Administrator-Zustimmung:** Teams können auf das Profil des Benutzers zugreifen.
    * **Beschreibung der** Administrator-Zustimmung: Ermöglicht Teams das Aufrufen der App-Web-APIs als aktuellen Benutzer.
    * **Titel der Benutzer-Zustimmung:** Teams kann auf das Benutzerprofil zugreifen und Anforderungen im Namen des Benutzers stellen.
    * **Beschreibung der Benutzer zustimmung:** Ermöglichen Sie Teams, die APIs dieser App mit denselben Rechten wie der Benutzer auf aufruft.
9. Stellen Sie **sicher, dass "State"** auf **"Enabled" festgelegt ist.**
10. Select the **Add scope** button to save 
    * Der Domänenteil  des Bereichsnamens, der direkt unterhalb des Textfelds angezeigt wird, sollte automatisch mit dem **anwendungs-ID-URI** übereinstimmen, der im vorherigen Schritt festgelegt wurde, und am Ende angefügt `/access_as_user` werden:
        * `api://subdomain.example.com/00000000-0000-0000-0000-000000000000/access_as_user`
11. Identifizieren Sie **im Abschnitt "Autorisierte Clientanwendungen"** die Anwendungen, die Sie für die Webanwendung Ihrer App autorisieren möchten. Wählen *Sie "Clientanwendung hinzufügen" aus.* Geben Sie jede der folgenden Client-IDs ein, und wählen Sie den autorisierten Bereich aus, den Sie im vorherigen Schritt erstellt haben:
    * `1fec8e78-bce4-4aaf-ab1b-5451cc387264` (Mobile Teams-/Desktopanwendung)
    * `5e3ce6c0-2b1f-4285-8d4b-75ee78787346` (Teams-Webanwendung)
12. Navigieren Sie zu **API-Berechtigungen.** Wählen *Sie "Delegierte Berechtigungen für* Microsoft Graph hinzufügen" aus, und fügen Sie dann die folgenden Berechtigungen aus der Microsoft  >    >  Graph-API hinzu:
    * User.Read (standardmäßig aktiviert)
    * email
    * offline_access
    * OpenId
    * Profil

13. Navigieren zur **Authentifizierung**

    Wenn einer App keine Zustimmung des IT-Admins erteilt wurde, müssen Benutzer ihre Zustimmung erteilen, wenn sie eine App zum ersten Mal verwenden.

    Festlegen eines Umleitungs-URI:
    * Wählen Sie **"Plattform hinzufügen" aus.**
    * Wählen Sie **Web** aus.
    * Geben Sie den **Umleitungs-URI** für Ihre App ein. Dies ist die Seite, auf der der Benutzer durch einen erfolgreichen impliziten Genehmigungsfluss umgeleitet wird. Dies ist derselbe vollqualifizierte Domänenname, den Sie in Schritt 5 eingegeben haben, gefolgt von der API-Route, an die eine Authentifizierungsantwort gesendet werden soll. Wenn Sie einem der Teams-Beispiele folgen, ist dies Folgendes: `https://subdomain.example.com/auth-end`

    Aktivieren Sie als Nächstes die implizite Gewährung, indem Sie die folgenden Kontrollkästchen aktivieren:  
    ✔-ID-Token  
    ✔ Zugriffstoken  
    
Herzlichen Glückwunsch! Sie haben die Voraussetzungen für die App-Registrierung erfüllt, um mit ihrer Registerkarten-SSO-App fortzufahren.     

> [!NOTE]
>
> * ¹ Wenn Ihre Azure AD-App im selben Mandanten registriert ist, in dem Sie eine Authentifizierungsanforderung in Teams stellen, wird der Benutzer nicht zur Zustimmung aufgefordert und erhält sofort ein Zugriffstoken.  Benutzer müssen diesen Berechtigungen nur zustimmen, wenn die Azure AD-App in einem anderen Mandanten registriert ist.
> * Wenn Sie eine Fehlermeldung erhalten, die besagt, dass die Domäne bereits im Besitz ist und Sie der Besitzer sind, führen Sie das Verfahren unter [Schnellstart aus:](/azure/active-directory/fundamentals/add-custom-domain) Fügen Sie Azure Active Directory einen benutzerdefinierten Domänennamen hinzu, um die Domäne zu registrieren, und wiederholen Sie dann Schritt 5 oben. (Dieser Fehler kann auch auftreten, wenn Sie nicht mit Administratoranmeldeinformationen im Office 365-Mandanz angemeldet sind).)
> * Wenn Sie den UPN (Benutzerprinzipalnamen) im zurückgegebenen Zugriffstoken nicht erhalten, können Sie ihn als [optionalen](https://docs.microsoft.com/azure/active-directory/develop/active-directory-optional-claims) Anspruch in Azure AD hinzufügen.

### <a name="2-update-your-microsoft-teams-application-manifest"></a>2. Aktualisieren Ihres Microsoft Teams-Anwendungsmanifests

Fügen Sie Ihrem Microsoft Teams-Manifest neue Eigenschaften hinzu:

* **WebApplicationInfo** – Das übergeordnete Element der folgenden Elemente:

> [!div class="checklist"]
> * **id** – Die Client-ID der Anwendung. Dies ist die Anwendungs-ID, die Sie im Rahmen der Registrierung der Anwendung bei Azure AD erhalten haben.
>* **resource** – Die Domäne und Unterdomäne Ihrer Anwendung. Dies ist der gleiche URI (einschließlich des Protokolls), den Sie beim Erstellen in Schritt `api://` `scope` 6 oben registriert haben. Sie sollten den Pfad nicht `access_as_user` in Ihre Ressource verwenden. Der Domänenteil dieses URI sollte mit der Domäne übereinstimmen, einschließlich aller Unterdomänen, die in den URLs Ihres Anwendungsmanifests von Teams verwendet werden.

```json
"webApplicationInfo": {
  "id": "00000000-0000-0000-0000-000000000000",
  "resource": "api://subdomain.example.com/00000000-0000-0000-0000-000000000000"
}
```

> [!NOTE]
>
>* Die Ressource für eine AAD-App ist in der Regel der Stamm der Website-URL und der appID (z. `api://subdomain.example.com/00000000-0000-0000-0000-000000000000` B.). Wir verwenden diesen Wert auch, um sicherzustellen, dass Ihre Anforderung von derselben Domäne kommt. Stellen Sie daher sicher, dass die `contentURL` Registerkarte für Ihre Registerkarte dieselben Domänen wie Ihre Ressourceneigenschaft verwendet.
>* Sie müssen die Manifestversion 1.5 oder höher verwenden, um das Feld zu `webApplicationInfo` implementieren.

### <a name="3-get-an-authentication-token-from-your-client-side-code"></a>3. Erhalten eines Authentifizierungstokens aus Ihrem clientseitigen Code

So sieht die Authentifizierungs-API aus:

```javascript
var authTokenRequest = {
  successCallback: function(result) { console.log("Success: " + result); },
  failureCallback: function(error) { console.log("Failure: " + error); }
};
microsoftTeams.authentication.getAuthToken(authTokenRequest);
```

Wenn Sie anrufen – und zusätzliche Zustimmung des Benutzers ist erforderlich (für Berechtigungen auf Benutzerebene) – wird dem Benutzer ein Dialogfeld angezeigt, in dem er dazu ermuntert wird, zusätzliche `getAuthToken` Zustimmung zu erteilen. 

Nachdem Sie das Zugriffstoken im Erfolgsrückruf erhalten haben, können Sie das Zugriffstoken decodieren, um die diesem Token zugeordneten Ansprüche anzeigen zu können. (Optional können Sie das Zugriffstoken manuell kopieren/in ein Tool einfügen, z. B. [JWT.io,](https://jwt.io/) um den Inhalt zu überprüfen). Wenn Sie den UPN (Benutzerprinzipalnamen) im zurückgegebenen Zugriffstoken nicht erhalten, können Sie ihn als [optionalen](https://docs.microsoft.com/azure/active-directory/develop/active-directory-optional-claims) Anspruch in Azure AD hinzufügen.

<p>
    <img src="~/assets/images/tabs/tabs-sso-prompt.png" alt="Tab single sign-on SSO dialog prompt" width="75%"/>
</p>

## <a name="sample-code"></a>Beispielcode

Besuchen Sie unsere Beispielanwendung: [MSTeams PnP-SSO-Beispiel](https://github.com/pnp/teams-dev-samples/tree/master/samples/tab-sso)

ReadME erläutert, wie Sie Ihre Entwicklungsumgebung einrichten und Ihre Anwendung in Azure AD konfigurieren. Weitere Informationen zur Struktur des Beispiels finden [](https://github.com/OfficeDev/msteams-tabs-sso-sample-nodejs#app-structure) Sie auch im Abschnitt "App-Struktur", um sich mit der Codebasis vertraut zu machen.

## <a name="known-limitations"></a>Bekannte Einschränkungen

### <a name="apps-that-require-additional-microsoft-graph-scopes"></a>Apps, die zusätzliche Microsoft Graph-Bereiche erfordern

Unsere aktuelle Implementierung für SSO erteilt nur zustimmungsberechtigungen auf Benutzerebene – E-Mail, Profil, offline_access, OpenId – nicht für andere APIs (z. B. User.Read oder Mail.Read). Wenn Ihre App weitere Microsoft Graph-Bereiche benötigt, finden Sie hier einige mögliche Problemumgehungen:

#### <a name="tenant-admin-consent"></a>Mandantenadministrator-Zustimmung

Der einfachste Ansatz besteht in der Vorab zustimmung eines Mandantenadministrators im Namen der Organisation. Dies bedeutet, dass Benutzer diesen Bereich nicht zustimmen müssen, und Sie können dann die Tokenserverseite mithilfe des [Im-Auftrag-von-Ablaufs](/azure/active-directory/develop/v1-oauth2-on-behalf-of-flow)von Azure AD austauschen. Diese Problemumgehung ist für interne Line-of-Business-Anwendungen akzeptabel, reicht aber möglicherweise nicht für Drittanbieterentwickler aus, die sich möglicherweise nicht auf die Genehmigung des Mandantenadministrators verlassen können.

Eine einfache Möglichkeit der Zustimmung im Namen einer Organisation (als Mandantenadministrator) besteht im Besuch:

* `https://login.microsoftonline.com/common/adminconsent?client_id=<AAD_App_ID>`

#### <a name="asking-for-additional-consent-using-the-auth-api"></a>Bitten um zusätzliche Zustimmung mithilfe der Authentifizierungs-API

Ein weiterer Ansatz zum Abrufen zusätzlicher Microsoft Graph-Bereiche ist die Darstellung eines Zustimmungsdialogfelds mithilfe unseres vorhandenen webbasierten Azure AD-Authentifizierungsansatzes, bei dem ein Azure [AD-Zustimmungsdialogfeld](~/tabs/how-to/authentication/auth-tab-aad.md#navigate-to-the-authorization-page-from-your-popup-page) angezeigt wird. Es gibt einige wichtige Ergänzungen:

1. Das mithilfe von Abruf abgerufene Token muss serverseitig mithilfe des `getAuthToken()` Azure [AD-Im-Auftrag-von-Ablaufs](/azure/active-directory/develop/v2-oauth2-on-behalf-of-flow) ausgetauscht werden, um Zugriff auf diese zusätzlichen Microsoft Graph-APIs zu erhalten.
    * Verwenden Sie den v2 Microsoft Graph-Endpunkt für diesen Austausch.
2. Wenn der Austausch fehlschlägt, gibt Azure AD eine ungültige Erteilungsausnahme zurück. Es gibt in der Regel eine von zwei Fehlermeldungen: `invalid_grant` oder `interaction_required`
3. Wenn der Austausch fehlschlägt, müssen Sie um zusätzliche Zustimmung bitten. Es wird empfohlen, eine Benutzeroberfläche zu zeigen, in der der Benutzer aufgefordert wird, eine zusätzliche Zustimmung zu erteilen. Diese Benutzeroberfläche sollte eine Schaltfläche enthalten, die ein Azure AD-Zustimmungsdialogfeld mithilfe unserer [Azure AD-Authentifizierungs-API auslöst.](~/concepts/authentication/auth-silent-aad.md)
4. Wenn Sie eine zusätzliche Zustimmung von Azure AD einholen, müssen Sie `prompt=consent` ihren [Abfragezeichenfolgenparameter](~/tabs/how-to/authentication/auth-silent-aad.md#get-the-user-context) in Azure AD angeben, andernfalls fordert Azure AD die zusätzlichen Bereiche nicht an.
    * Statt: `?scope={scopes}`
    * Verwenden Sie dies: `?prompt=consent&scope={scopes}`
    * Achten Sie darauf, dass alle Bereiche enthalten sind, für die Sie den Benutzer zur Eingabe aufgefordert haben (z. B. `{scopes}` Mail.Read oder User.Read).
5. Nachdem der Benutzer zusätzliche Berechtigungen erteilt hat, wiederholen Sie den Im-Auftrag-von-Fluss, um Zugriff auf diese zusätzlichen APIs zu erhalten.

### <a name="non-azure-ad-authentication"></a>Nicht-Azure AD-Authentifizierung

Die oben beschriebene Authentifizierungslösung funktioniert nur für Apps und Dienste, die Azure AD als Identitätsanbieter unterstützen. Apps, die sich mit nicht azure AD-basierten Diensten authentifizieren möchten, müssen weiterhin den Pop-up-basierten [Webauthentifizierungsfluss verwenden.](~/concepts/authentication.md)

> [!NOTE] 
> SSO wird für Apps im Besitz von Kunden innerhalb der Azure AD B2C-Mandanten unterstützt.