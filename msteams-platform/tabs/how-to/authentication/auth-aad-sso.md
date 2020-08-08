---
title: Einmaliges Anmelden
description: Beschreibt einmaliges Anmelden (Single Sign-on, SSO)
keywords: Teams-Authentifizierung SSO Aad Single Sign-on-API
ms.openlocfilehash: cf3c33cf9721243936890140d5bcce641c443e2e
ms.sourcegitcommit: 7a2da3b65246a125d441a971e7e6a6418355adbe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2020
ms.locfileid: "46587734"
---
# <a name="single-sign-on-sso"></a>Einmaliges Anmelden (SSO)

Benutzer melden sich über Ihre Arbeits-, Schul-oder Microsoft-Konten (Office 365, Outlook usw.) bei Microsoft Teams an. Sie können dies nutzen, indem Sie einer einmaligen Anmeldung die Autorisierung Ihrer Microsoft Teams-Registerkarte (oder des Aufgabenmoduls) auf Desktop-oder mobilen Clients ermöglichen. Wenn ein Benutzer also einwilligt, die APP zu verwenden, muss er sich nicht erneut auf einem anderen Gerät einverstanden erklären – er wird automatisch angemeldet. Außerdem rufen wir ihr Zugriffstoken ab, um die Leistung und die Ladezeiten zu verbessern.

## <a name="how-sso-works-at-runtime"></a>Funktionsweise von SSO zur Laufzeit

Das folgende Diagramm zeigt die Funktionsweise des SSO-Prozesses:

<img src="~/assets/images/tabs/tabs-sso-diagram.png" alt="Tab single sign-on SSO diagram" width="75%"/>

1. Auf der Registerkarte wird ein JavaScript-Aufruf ausgeführt `getAuthToken()` . Dadurch wird Microsoft Teams mitgeteilt, ein Authentifizierungstoken für die Registerkarten Anwendung zu erhalten.
2. Wenn der aktuelle Benutzer die Tab-Anwendung zum ersten Mal verwendet hat, wird eine Anforderungs Aufforderung zur Zustimmung (sofern Zustimmung erforderlich ist) oder zur Behandlung der Step-up-Authentifizierung (beispielsweise zweistufige Authentifizierung) angezeigt.
3. Teams fordert das Registerkarten-Anwendungs Token vom Azure AD Endpunkt für den aktuellen Benutzer an.
4. Azure AD sendet das Registerkarten-Anwendungs Token an die Teams-Anwendung.
5. Teams sendet das Registerkarten-Anwendungs Token als Teil des result-Objekts, das vom Aufruf zurückgegeben wird, an die Registerkarte `getAuthToken()` .
6. Das Token wird in der Tab-Anwendung über JavaScript analysiert, um die benötigten Informationen wie die e-Mail-Adresse des Benutzers zu extrahieren.

> [!NOTE]
> Die `getAuthToken()` gilt nur für Zustimmung zu einer begrenzten Gruppe von APIs auf Benutzerebene (e-Mail, Profil, offline_access und OpenID) und nicht für weitere Microsoft Graph-Bereiche wie `User.Read` oder `Mail.Read` . In unserem Abschnitt am Ende dieses Dokuments finden Sie Empfohlene Problemumgehungen, wenn Sie [zusätzliche Diagrammbereiche](#apps-that-require-additional-microsoft-graph-scopes)benötigen.

Die SSO-API funktioniert auch in [Aufgaben Modulen](../../../task-modules-and-cards/what-are-task-modules.md) , in denen Webinhalte eingebettet werden.

## <a name="develop-an-sso-microsoft-teams-tab"></a>Entwickeln einer SSO-Microsoft Teams-Registerkarte

In diesem Abschnitt werden die Aufgaben im Zusammenhang mit dem Erstellen einer Registerkarte Teams beschrieben, die SSO verwendet. Diese Aufgaben werden hier beschrieben, sind sprach-und Framework-Agnostiker.

### <a name="1-create-your-azure-active-directory-azure-ad-application"></a>1. Erstellen Ihrer Azure Active Directory (Azure AD)-Anwendung

Registrieren Sie Ihre Anwendung im[Azure AD Portal](https://azure.microsoft.com/features/azure-portal/). Dieser Prozess dauert fünf bis zehn Minuten und umfasst die folgenden Aufgaben:

1. Rufen Sie Ihre [Azure AD-Anwendungs-ID](/azure/active-directory/develop/howto-create-service-principal-portal#get-values-for-signing-in)ab.
2. Geben Sie die Berechtigungen an, die Ihre Anwendung für den Azure AD-Endpunkt und optional für Microsoft Graph benötigt.
3. [Erteilen von Berechtigungen](/azure/active-directory/develop/howto-create-service-principal-portal#configure-access-policies-on-resources) für Desktop-, Webanwendungen und Mobile Microsoft Teams-Anwendungen
4. Vorautorisieren von Teams durch Auswählen der Schaltfläche **Bereich hinzufügen** und Eingeben des `access_as_user` **Bereichsnamens**in das geöffnete Fenster.

> [!NOTE]
> Es gibt einige wichtige Einschränkungen, die Sie beachten sollten:
>
> * Wir unterstützen nur die Microsoft Graph-API-Berechtigungen auf Benutzerebene, also e-Mail, Profil, offline_access, OpenID. Wenn Sie Zugriff auf andere Microsoft Graph-Bereiche (wie `User.Read` oder) benötigen `Mail.Read` , lesen Sie unsere [empfohlene Problemumgehung](#apps-that-require-additional-microsoft-graph-scopes) am Ende dieser Dokumentation.
> * Es ist wichtig, dass der Domänenname Ihrer Anwendung mit dem Domänennamen identisch ist, den Sie für Ihre Azure AD Anwendung registriert haben.
> * Wir unterstützen derzeit nicht mehrere Domänen pro app.
> * Anwendungen, die die Domäne verwenden, werden nicht unterstützt, `azurewebsites.net` da dies zu häufig ist und möglicherweise ein Sicherheitsrisiko darstellt. Wir versuchen jedoch aktiv, diese Einschränkung zu entfernen.

#### <a name="steps"></a>Schritte

1. Registrieren Sie eine neue Anwendung im Portal [Azure Active Directory – App-Registrierung](https://go.microsoft.com/fwlink/?linkid=2083908) .
2. Wählen Sie **neue Registrierung** aus, und legen Sie auf der *Seite Anwendung registrieren*folgende Werte fest:
    * Legen Sie den **Namen** auf Ihren APP-Namen fest.
    * Wählen Sie die **unterstützten Kontotypen** (jeder Kontotyp ist funktionsfähig) ¹
    * Lassen Sie **URI umleiten** leer.
    * Wählen Sie **Registrieren** aus.
3. Kopieren und speichern Sie auf der Übersichtsseite die **Anwendungs-ID (Client)**. Sie benötigen Sie später beim Aktualisieren des Teams-Anwendungsmanifests.
4. Wählen Sie unter **Verwalten** die Option **Eine API verfügbar machen** aus. 
5. Wählen Sie den Link **festlegen** aus, um den Anwendungs-ID-URI in Form von zu generieren `api://{AppID}` . Fügen Sie den vollqualifizierten Domänennamen zwischen den doppelten Schrägstrichen und der GUID (mit einem Schrägstrich "/" am Ende hinzugefügt) ein. Die gesamte ID sollte die Form haben: `api://fully-qualified-domain-name.com/{AppID}` ²
    * Ex: `api://subdomain.example.com/00000000-0000-0000-0000-000000000000` .
6. Wählen Sie die Schaltfläche**Bereich hinzufügen** aus. Geben Sie im Bereich, der geöffnet wird, `access_as_user` für**Bereichsname** ein.
7. Legen Sie fest **, wer einwilligen kann.**`Admins and users`
8. Füllen Sie die Felder für die Konfiguration der Administrator-und Benutzer Zustimmungs Ansagen mit Werten aus, die für den Bereich geeignet sind `access_as_user` :
    * **Titel der Administrator Zustimmung:** Teams können auf das Profil des Benutzers zugreifen.
    * **Administrator-Zustimmungs Beschreibung**: ermöglicht Teams das Aufrufen der webapin der App als aktueller Benutzer.
    * **Benutzer Zustimmungs Titel**: Teams können auf das Benutzerprofil zugreifen und Anforderungen im Namen des Benutzers stellen.
    * **Beschreibung der Benutzer Zustimmung:** Aktivieren Sie Teams, um APIs dieser APP mit denselben Rechten wie der Benutzer aufzurufen.
9. Sicherstellen, dass der **Status** auf " **aktiviert** " festgelegt ist
10. **Bereich "hinzufügen** " auswählen
    * Der Domänenteil des **Bereichsnamens** , der direkt unterhalb des Textfelds angezeigt wird, sollte automatisch mit dem im vorherigen Schritt festgelegten **Anwendungs-ID** -URI übereinstimmen, wobei der Wert am `/access_as_user` Ende angefügt ist:
        * `api://subdomain.example.com/00000000-0000-0000-0000-000000000000/access_as_user`
11. Identifizieren Sie im Abschnitt **autorisierte Clientanwendungen** die Anwendungen, die Sie für die Webanwendung Ihrer APP autorisieren möchten. Jeder der folgenden IDs muss eingegeben werden:
    * `1fec8e78-bce4-4aaf-ab1b-5451cc387264`(Mobile Teams/Desktopanwendung)
    * `5e3ce6c0-2b1f-4285-8d4b-75ee78787346`(Microsoft Teams-Webanwendung)
12. Navigieren Sie zu **API-Berechtigungen**, und stellen Sie sicher, dass Sie die folgenden Berechtigungen hinzufügen:
    * User. Read (standardmäßig aktiviert)
    * email
    * offline_access
    * OpenID
    * profile

13. Navigieren zur **Authentifizierung**

    Wenn der IT-Administrator keine Zustimmung für eine APP erteilt wurde, müssen die Benutzer die Zustimmung erteilen, wenn Sie die APP zum ersten Mal verwenden.

    Festlegen eines Umleitungs-URI:
    * Wählen Sie **Plattform hinzufügen**aus.
    * Wählen Sie **Internet**aus.
    * Geben Sie den **Umleitungs-URI** für Ihre APP ein. Dies ist die Seite, auf der der Benutzer durch einen erfolgreichen impliziten Grant-Fluss umgeleitet wird.

    Aktivieren Sie implizite Gewährung, indem Sie die folgenden Felder überprüfen:  
    ✔-ID-Token  
    ✔ Zugriffs Token  
    
    

> [!NOTE]
>
> * ¹ Wenn Ihre Azure AD-App in einem Mandanten registriert ist, _in dem Sie_ eine Authentifizierungsanforderung in Microsoft Teams stellen, wird der Benutzer nicht zur Zustimmung aufgefordert und erhält sofort ein Zugriffstoken. Benutzer müssen diesen Berechtigungen nur zustimmen, wenn die Azure AD-App in einem anderen Mandanten registriert ist.
> * ² Wenn Sie eine Fehlermeldung erhalten, dass die Domäne bereits im Besitz ist und Sie der Besitzer sind, führen Sie das Verfahren unter [Schnellstart: Hinzufügen eines benutzerdefinierten Domänennamens zu Azure Active Directory](/azure/active-directory/fundamentals/add-custom-domain) aus, um die Domäne zu registrieren, und wiederholen Sie dann Schritt 5 oben. (Dieser Fehler kann auch auftreten, wenn Sie nicht mit Administratoranmeldeinformationen im Office 365 Mandanten angemeldet sind).
> * Wenn Sie den UPN (Benutzerprinzipal Name) nicht im zurückgegebenen Zugriffstoken empfangen, können Sie ihn als [optionalen Anspruch](https://docs.microsoft.com/azure/active-directory/develop/active-directory-optional-claims) in Azure AD hinzufügen.

### <a name="2-update-your-microsoft-teams-application-manifest"></a>2. Aktualisieren des Microsoft Teams-Anwendungsmanifests

Fügen Sie Ihrem Microsoft Teams-Manifest neue Eigenschaften hinzu:

* **WebApplicationInfo** -das übergeordnete Element der folgenden Elemente:

> [!div class="checklist"]
> * **ID** – die Client-ID der Anwendung. Dies ist die Anwendungs-ID, die Sie im Rahmen der Registrierung der Anwendung mit Azure AD erhalten haben.
>* **Resource** – die Domäne und Unterdomäne Ihrer Anwendung. Hierbei handelt es sich um denselben URI (einschließlich des `api://` Protokolls), den Sie bei der Erstellung Ihres `scope` in Schritt 6 oben registriert haben. Sie sollten den `access_as_user` Pfad nicht in Ihre Ressource einschließen. Der Domänenteil dieses URIs sollte der Domäne entsprechen, einschließlich aller Unterdomänen, die in den URLs Ihres Teams-Anwendungsmanifests verwendet werden.

```json
"webApplicationInfo": {
  "id": "00000000-0000-0000-0000-000000000000",
  "resource": "api://subdomain.example.com/00000000-0000-0000-0000-000000000000"
}
```

> [!NOTE]
>
>* Die Ressource für eine Aad-APP ist in der Regel der Stamm der Website-URL und der Anwendungs-ID (beispielsweise `api://subdomain.example.com/00000000-0000-0000-0000-000000000000` ). Dieser Wert wird auch verwendet, um sicherzustellen, dass Ihre Anforderung aus derselben Domäne stammt. Stellen Sie daher sicher, dass `contentURL` auf der Registerkarte für Ihre Registerkarten dieselben Domänen wie die Ressourceneigenschaft verwendet werden.
>* Sie müssen manifestVersion Version 1,5 oder höher verwenden, um das `webApplicationInfo` Feld zu implementieren.

### <a name="3-get-an-authentication-token-from-your-client-side-code"></a>3. Abrufen eines Authentifizierungstokens von Ihrem clientseitigen Code

Hier sehen Sie, wie die Authentifizierungs-API aussieht:

```javascript
var authTokenRequest = {
  successCallback: function(result) { console.log("Success: " + result); },
  failureCallback: function(error) { console.log("Failure: " + error); },
};
microsoftTeams.authentication.getAuthToken(authTokenRequest);
```

Wenn Sie anrufen `getAuthToken` und zusätzliche Benutzer Zustimmung erforderlich ist (für Berechtigungen auf Benutzerebene), wird dem Benutzer ein Dialogfeld angezeigt, in dem Sie ermutigt werden, zusätzliche Zustimmung zu gewähren. 

Nachdem Sie das Zugriffstoken im success-Rückruf erhalten haben, können Sie das Zugriffstoken decodieren, um die diesem Token zugeordneten Ansprüche anzuzeigen. (Optional können Sie das Zugriffstoken manuell kopieren/einfügen in ein Tool wie [JWT.IO](https://jwt.io/) , um den Inhalt zu überprüfen). Wenn Sie den UPN (Benutzerprinzipal Name) nicht im zurückgegebenen Zugriffstoken empfangen, können Sie ihn als [optionalen Anspruch](https://docs.microsoft.com/azure/active-directory/develop/active-directory-optional-claims) in Azure AD hinzufügen.

<p>
    <img src="~/assets/images/tabs/tabs-sso-prompt.png" alt="Tab single sign-on SSO dialog prompt" width="75%"/>
</p>

## <a name="sample-code"></a>Beispielcode

Besuchen Sie unsere Beispielanwendung: [MSTeams Tabs SSO Sample-Nodejs](https://github.com/OfficeDev/msteams-tabs-sso-sample-nodejs)

In der Infodatei wird erklärt, wie Sie Ihre Entwicklungsumgebung einrichten und wie Sie Ihre Anwendung in Azure AD konfigurieren. Weitere Informationen zur Strukturierung des Beispiels im [Abschnitt App-Struktur](https://github.com/OfficeDev/msteams-tabs-sso-sample-nodejs#app-structure) finden Sie auch, um sich mit der CodeBase vertraut zu machen.

## <a name="known-limitations"></a>Bekannte Einschränkungen

### <a name="apps-that-require-additional-microsoft-graph-scopes"></a>Apps, die zusätzliche Microsoft Graph-Bereiche erfordern

Unsere aktuelle Implementierung für SSO erteilt nur Zustimmung für Berechtigungen auf Benutzerebene – e-Mail, Profil, offline_access, OpenID – nicht für andere APIs (wie "User. Read" oder "Mail. Read"). Wenn Ihre APP weitere Microsoft Graph-Bereiche benötigt, finden Sie hier einige Workarounds für die Aktivierung:

#### <a name="tenant-admin-consent"></a>Zustimmung des Mandanten Administrators

Der einfachste Ansatz besteht darin, einen mandantenadministrator zur Vorabgenehmigung im Namen der Organisation zu erhalten. Dies bedeutet, dass Benutzer diesen Bereichen nicht zustimmen müssen und Sie dann frei sein können, die tokenserver-Seite mithilfe [von Azure AD im Auftrag von Flow](/azure/active-directory/develop/v1-oauth2-on-behalf-of-flow)auszutauschen. Diese Problemumgehung ist für interne Branchenanwendungen akzeptabel, aber möglicherweise nicht ausreichend für Drittanbieterentwickler, die möglicherweise nicht auf mandantenadministrator Genehmigung vertrauen können.

Eine einfache Möglichkeit, im Namen einer Organisation (als mandantenadministrator) einzuwilligen, ist das Besuchen von:

* `https://login.microsoftonline.com/common/adminconsent?client_id=<AAD_App_ID>`

#### <a name="asking-for-additional-consent-using-the-auth-api"></a>Bitten um zusätzliche Zustimmung mithilfe der Authentifizierungs-API

Ein weiterer Ansatz für das Aufrufen zusätzlicher Microsoft Graph-Bereiche besteht darin, einen Zustimmungs Dialog mit unserem vorhandenen [webbasierten Azure AD Authentifizierungs Ansatz](~/tabs/how-to/authentication/auth-tab-aad.md#navigate-to-the-authorization-page-from-your-popup-page) zu präsentieren, der das Auftauchen eines Azure AD Zustimmungs Dialogs beinhaltet. Es gibt einige bemerkenswerte Ergänzungen:

1. Das mit dem abgerufenen Token verwendete `getAuthToken()` muss serverseitig mit Azure AD [im Auftrag von Flow](/azure/active-directory/develop/v2-oauth2-on-behalf-of-flow) ausgetauscht werden, um Zugriff auf diese zusätzlichen Microsoft Graph-APIs zu erhalten.
    * Stellen Sie sicher, dass Sie den Microsoft Graph-Endpunkt v2 für diesen Exchange verwenden.
2. Wenn der Exchange-Fehler auftritt, gibt Azure AD eine ungültige Grant-Ausnahme zurück. Normalerweise gibt es eine von zwei Fehlermeldungen: `invalid_grant` oder`interaction_required`
3. Wenn der Exchange-Fehler auftritt, müssen Sie um zusätzliche Zustimmung bitten. Es wird empfohlen, einige Benutzeroberflächen anzuzeigen, in denen der Benutzer aufgefordert wird, zusätzliche Zustimmung zu erteilen. Diese Benutzeroberfläche sollte eine Schaltfläche enthalten, mit der ein Azure AD Zustimmungsdialogfeld mithilfe unserer [Azure AD-Authentifizierungs-API](~/concepts/authentication/auth-silent-aad.md)ausgelöst wird.
4. Wenn Sie eine zusätzliche Zustimmung von Azure AD anfordern, müssen Sie den `prompt=consent` [Abfrage-String-Parameter](~/tabs/how-to/authentication/auth-silent-aad.md#get-the-user-context) in Azure AD einbeziehen, andernfalls wird Azure AD nicht nach den zusätzlichen Bereichen gefragt.
    * Statt:`?scope={scopes}`
    * Verwenden Sie Folgendes:`?prompt=consent&scope={scopes}`
    * Stellen Sie sicher, dass `{scopes}` alle Bereiche eingeschlossen sind, für die Sie den Benutzer auffordern (z. b.: Mail. Read oder User. Read).
5. Nachdem der Benutzer zusätzliche Berechtigungen erteilt hat, wiederholen Sie den Vorgang im Auftrag von Flow, um Zugriff auf diese zusätzlichen APIs zu erhalten.

### <a name="non-azure-ad-authentication"></a>Nicht Azure AD Authentifizierung

Die oben beschriebene Authentifizierungslösung funktioniert nur für apps und Dienste, die Azure AD als Identitätsanbieter unterstützen. Apps, die mit nicht Azure AD basierten Diensten authentifiziert werden möchten, müssen weiterhin den Popup basierten [Webauthentifizierungs Fluss](~/concepts/authentication.md)verwenden.
