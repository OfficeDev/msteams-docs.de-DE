---
title: Unterstützung für einmaliges Anmelden für Registerkarten
description: Beschreibt einmaliges Anmelden (Single Sign-On, SSO)
ms.topic: how-to
localization_priority: Normal
keywords: Teams-Authentifizierungs-SSO-AAD-Api für einmaliges Anmelden
ms.openlocfilehash: 681481d4d4f764c260729d37d7b5f5f2ce58d0ec
ms.sourcegitcommit: d9274ac2f32880e861b206ac6ce29467d631177f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2021
ms.locfileid: "52760881"
---
# <a name="single-sign-on-sso-support-for-tabs"></a>SSO-Unterstützung (Single Sign-On) für Registerkarten

Benutzer melden sich bei Microsoft Teams über ihre Geschäfts-, Schul- oder Microsoft-Konten an, die Office 365, Outlook usw. sind. Sie können dies nutzen, indem Sie einem einmaligen Anmelden erlauben, Ihre Teams Registerkarte oder ihr Aufgabenmodul auf Desktop- oder mobilen Clients zu autorisieren. Wenn ein Benutzer der Verwendung Ihrer App zustimmt, muss er auf einem anderen Gerät nicht erneut zustimmen, da er automatisch angemeldet ist. Darüber hinaus wird Ihr Zugriffstoken vorab abgerufen, um die Leistung und Ladezeiten zu verbessern.

> [!NOTE]
> **Teams versionen mobiler Clients, die SSO unterstützen**  
>
> ✔Teams für Android (1416/1.0.0.2020073101 und höher)
>
> ✔Teams für iOS (_Version:_ 2.0.18 und höher)  
>
> Um eine optimale Erfahrung mit Teams zu erzielen, verwenden Sie die neueste Version von iOS und Android.

> [!NOTE]
> **Schnellstart**  
>
> Der einfachste Weg zu den ersten Schritten mit Tab-SSO ist das Teams Toolkit für Visual Studio Code. Weitere Informationen finden Sie unter [SSO mit Teams Toolkit und Visual Studio Code für Registerkarten](../../../toolkit/visual-studio-code-tab-sso.md)

## <a name="how-sso-works-at-runtime"></a>Funktionsweise von SSO zur Laufzeit

Die folgende Abbildung zeigt, wie der SSO-Prozess funktioniert:

<!-- markdownlint-disable MD033 -->
<img src="~/assets/images/tabs/tabs-sso-diagram.png" alt="Tab single sign-on SSO diagram" width="75%"/>

1. In der Registerkarte wird ein JavaScript-Aufruf an `getAuthToken()` durchgeführt. Dadurch wird Teams angewiesen, ein Authentifizierungstoken für die Registerkartenanwendung abzurufen.
2. Wenn der aktuelle Benutzer ihre Registerkartenanwendung zum ersten Mal verwendet hat, wird eine Anforderungsaufforderung zur Zustimmung angezeigt, wenn eine Zustimmung erforderlich ist, oder um die schrittweise Authentifizierung wie die zweistufige Authentifizierung zu behandeln.
3. Teams fordert das Registerkartenanwendungstoken vom Azure Active Directory-Endpunkt (AAD) für den aktuellen Benutzer an.
4. AAD sendet das Registerkartenanwendungstoken an die Teams Anwendung.
5. Teams sendet das Token der Registerkartenanwendung als Teil des ergebnisobjekts, das vom Aufruf zurückgegeben wird, an die `getAuthToken()` Registerkarte.
6. Das Token wird in der Registerkartenanwendung mithilfe von JavaScript analysiert, um die erforderlichen Informationen wie die E-Mail-Adresse des Benutzers zu extrahieren.

> [!NOTE]
> Dies gilt nur für die `getAuthToken()` Zustimmung zu einer begrenzten Gruppe von APIs auf Benutzerebene, bei denen es sich um E-Mails, Profile, offline_access und OpenId handelt. Es wird nicht für weitere Graph Bereichen wie oder `User.Read` `Mail.Read` verwendet. Empfohlene Problemumgehungen finden Sie in [zusätzlichen Graph Bereichen.](#apps-that-require-additional-graph-scopes)

Die SSO-API funktioniert auch in [Aufgabenmodulen,](../../../task-modules-and-cards/what-are-task-modules.md) die Webinhalte einbetten.

## <a name="develop-an-sso-microsoft-teams-tab"></a>Entwickeln einer SSO-Microsoft Teams-Registerkarte

In diesem Abschnitt werden die Aufgaben zum Erstellen einer Teams Registerkarte beschrieben, die SSO verwendet. Diese Aufgaben sind sprach- und frameworkunabhängig.

### <a name="1-create-your-aad-application"></a>1. Erstellen Der AAD-Anwendung

**So registrieren Sie Ihre Anwendung in der [AAD-Portalübersicht](https://azure.microsoft.com/features/azure-portal/)**

1. Rufen Sie Ihre [AAD-Anwendungs-ID ab.](/azure/active-directory/develop/howto-create-service-principal-portal#get-values-for-signing-in) 
1. Geben Sie die Berechtigungen an, die Ihre Anwendung für den AAD-Endpunkt benötigt, und optional Graph.
1. [Erteilen von Berechtigungen](/azure/active-directory/develop/howto-create-service-principal-portal#configure-access-policies-on-resources) für Teams Desktop-, Web- und mobile Anwendungen.
1. Autorisieren Sie Teams vorab, indem Sie die Schaltfläche **"Bereich hinzufügen"** auswählen, und geben Sie im daraufhin geöffneten Bereich **access_as_user** als **Bereichsnamen** ein.

> [!NOTE]
> Es gibt einige wichtige Einschränkungen, die Sie kennen müssen:
>
> * Es werden nur Graph API-Berechtigungen auf Benutzerebene unterstützt, d. h. E-Mail, Profil, offline_access, OpenId. Wenn Sie Zugriff auf andere Graph Bereichen haben müssen, z. B. `User.Read` oder , lesen Sie die empfohlene `Mail.Read` [Problemumgehung.](#apps-that-require-additional-graph-scopes)
> * Es ist wichtig, dass der Domänenname Ihrer Anwendung mit dem Domänennamen übereinstimmt, den Sie für Ihre AAD-Anwendung registriert haben.
> * Derzeit werden mehrere Domänen pro App nicht unterstützt.

**So registrieren Sie Ihre App über das AAD-Portal**

1. Registrieren Sie eine neue Anwendung im [AAD-App-Registrierungsportal.](https://go.microsoft.com/fwlink/?linkid=2083908)
1. Wählen Sie **"Neue Registrierung"** aus. Die Seite **"Anwendung registrieren"** wird angezeigt.
1. Geben Sie auf der Seite **"Anwendung registrieren"** die folgenden Werte ein:
    1. Geben Sie einen **Namen** für Ihre App ein.
    2. Wählen Sie die **unterstützten Kontotypen** aus, wählen Sie den Kontotyp "Einzelner Mandant" oder "Mehrinstanzenkonto" aus. ¹
    * Lassen Sie **URI umleiten** leer.
    3. Wählen Sie **Registrieren** aus.
1. Kopieren und speichern Sie auf der Übersichtsseite die **Anwendungs-ID (Client-ID).** Sie benötigen ihn später, wenn Sie Ihr Teams Anwendungsmanifest aktualisieren.
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
    * `1fec8e78-bce4-4aaf-ab1b-5451cc387264`für Teams mobile oder Desktopanwendung.
    * `5e3ce6c0-2b1f-4285-8d4b-75ee78787346`für Teams Webanwendung.
1. Navigieren Sie zu **API-Berechtigungen.** Wählen **Sie "Microsoft** Graph Delegierte Berechtigungen" eine Berechtigung hinzufügen  >    >  aus, und fügen Sie dann die folgenden Berechtigungen aus Graph API hinzu:
    * User.Read ist standardmäßig aktiviert
    * email
    * offline_access
    * Openid
    * Profil

1. Navigieren Sie zur **Authentifizierung.**

    Wenn einer App keine IT-Administratorzustimmung erteilt wurde, müssen Benutzer die Zustimmung erteilen, wenn sie eine App zum ersten Mal verwenden.

    So geben Sie einen Umleitungs-URI ein:
    * Wählen Sie **"Plattform hinzufügen"** aus.
    * Wählen Sie **"Web"** aus.
    * Geben Sie den **Umleitungs-URI** für Ihre App ein. Dies ist die Seite, auf der ein erfolgreicher impliziter Genehmigungsfluss den Benutzer umleitet. Dies ist der gleiche vollqualifizierte Domänenname, den Sie in Schritt 5 eingegeben haben, gefolgt von der API-Route, an die eine Authentifizierungsantwort gesendet wird. Wenn Sie einem der Teams Beispiele folgen, ist dies `https://subdomain.example.com/auth-end` .

    Aktivieren Sie die implizite Genehmigung, indem Sie die folgenden Kontrollkästchen aktivieren: ✔ ID-Token ✔ Zugriffstoken

Glückwunsch! Sie haben die Voraussetzungen für die App-Registrierung erfüllt, um mit Ihrer Registerkarten-SSO-App fortzufahren.

> [!NOTE]
>
> * Wenn Ihre AAD-App im selben Mandanten registriert ist, in dem Sie eine Authentifizierungsanforderung in Teams stellen, kann der Benutzer nicht zur Zustimmung aufgefordert werden und erhält sofort ein Zugriffstoken. Benutzer stimmen diesen Berechtigungen nur zu, wenn die AAD-App in einem anderen Mandanten registriert ist.
> * ² Wenn die benutzerdefinierte Domäne nicht zu AAD hinzugefügt wird, erhalten Sie einen Fehler, der besagt, dass der Hostname nicht auf einer bereits im Besitz befindlichen Domäne basieren darf. Um AAD eine benutzerdefinierte Domäne hinzuzufügen und zu registrieren, folgen Sie der [AAD-Prozedur, um einen benutzerdefinierten Domänennamen hinzuzufügen,](/azure/active-directory/fundamentals/add-custom-domain) und wiederholen Sie dann Schritt 5. Sie können diesen Fehler auch erhalten, wenn Sie nicht mit Administratoranmeldeinformationen im Office 365 Mandanten angemeldet sind.
> * Wenn Sie den Benutzerprinzipalnamen (USER Principal Name, UPN) im zurückgegebenen Zugriffstoken nicht erhalten, können Sie ihn als [optionalen Anspruch](/azure/active-directory/develop/active-directory-optional-claims) in AAD hinzufügen.

### <a name="2-update-your-teams-application-manifest"></a>2. Aktualisieren Des Teams Anwendungsmanifests

Verwenden Sie den folgenden Code, um dem Teams Manifest neue Eigenschaften hinzuzufügen:

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
>* Die Ressource für eine AAD-App ist in der Regel der Stamm der Website-URL und der appID (z. B. `api://subdomain.example.com/00000000-0000-0000-0000-000000000000` ). Dieser Wert wird auch verwendet, um sicherzustellen, dass Ihre Anforderung von derselben Domäne stammt. Stellen Sie sicher, dass die `contentURL` Registerkarte dieselben Domänen wie Ihre Ressourceneigenschaft verwendet.
>* Sie müssen die Manifestversion 1.5 oder höher verwenden, um das Feld zu `webApplicationInfo` implementieren.

### <a name="3-get-an-authentication-token-from-your-client-side-code"></a>3. Abrufen eines Authentifizierungstokens aus ihrem clientseitigen Code

Verwenden Sie die folgende Authentifizierungs-API:

```javascript
var authTokenRequest = {
  successCallback: function(result) { console.log("Success: " + result); },
  failureCallback: function(error) { console.log("Failure: " + error); }
};
microsoftTeams.authentication.getAuthToken(authTokenRequest);
```

Wenn Sie anrufen `getAuthToken` – und eine zusätzliche Benutzerzustimmung für Berechtigungen auf Benutzerebene erforderlich ist, wird dem Benutzer ein Dialogfeld angezeigt, um zusätzliche Zustimmung zu erteilen.

Nachdem Sie das Zugriffstoken im Erfolgsrückruf erhalten haben, können Sie das Zugriffstoken decodieren, um die diesem Token zugeordneten Ansprüche anzuzeigen. Optional können Sie das Zugriffstoken manuell kopieren und in ein Tool einfügen, z. [B. jwt.ms,](https://jwt.ms/) um dessen Inhalt zu überprüfen. Wenn Sie den UPN im zurückgegebenen Zugriffstoken nicht erhalten, können Sie ihn als [optionalen Anspruch](/azure/active-directory/develop/active-directory-optional-claims) in AAD hinzufügen.

<p>
    <img src="~/assets/images/tabs/tabs-sso-prompt.png" alt="Tab single sign-on SSO dialog prompt" width="75%"/>
</p>

## <a name="code-sample"></a>Codebeispiel

|**Beispielname**|**Beschreibung**|**C#**|**Node.js**|
|---------------|---------------|------|--------------|
| Registerkarten-SSO |Microsoft Teams Beispiel-App für Registerkarten azure AD SSO| [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-sso/csharp)|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/blob/main/samples/tab-sso/nodejs), </br>[Teams Toolkit](../../../toolkit/visual-studio-code-tab-sso.md)|

## <a name="known-limitations"></a>Bekannte Einschränkungen

### <a name="apps-that-require-additional-graph-scopes"></a>Apps, die zusätzliche Graph Bereiche erfordern

Unsere aktuelle Implementierung für SSO erteilt nur die Zustimmung für Berechtigungen auf Benutzerebene, die E-Mail, Profil, offline_access, OpenId und nicht für andere APIs wie User.Read oder Mail.Read sind. Wenn Ihre App weitere Graph Bereichen benötigt, finden Sie im nächsten Abschnitt einige Problemumgehungen für die Aktivierung.

#### <a name="tenant-admin-consent"></a>Mandantenadministratorzustimmung

Der einfachste Ansatz besteht darin, einen Mandantenadministrator zur Vorabzustimmung im Namen der Organisation zu bringen. Dies bedeutet, dass Benutzer diesen Bereichen nicht zustimmen müssen, und Sie können dann den Tokenserver mithilfe [des Im-Auftrag-of-Flusses von](/azure/active-directory/develop/v1-oauth2-on-behalf-of-flow)AAD austauschen. Diese Problemumgehung ist für interne Branchenanwendungen akzeptabel, reicht jedoch nicht für Drittanbieterentwickler aus, die sich nicht auf die Genehmigung durch den Mandantenadministrator verlassen können.

Eine einfache Möglichkeit, im Namen einer Organisation als Mandantenadministrator zuzustimmen, besteht darin, auf diese zu `https://login.microsoftonline.com/common/adminconsent?client_id=<AAD_App_ID>` verweisen.

#### <a name="ask-for-additional-consent-using-the-auth-api"></a>Anfordern zusätzlicher Zustimmung mithilfe der Authentifizierungs-API

Ein weiterer Ansatz zum Abrufen zusätzlicher Graph Bereiche besteht darin, ein Zustimmungsdialogfeld mithilfe unseres vorhandenen [webbasierten Azure AD-Authentifizierungsansatzes](~/tabs/how-to/authentication/auth-tab-aad.md#navigate-to-the-authorization-page-from-your-popup-page) anzuzeigen, bei dem ein Dialogfeld für die Azure AD-Zustimmung angezeigt wird. 

**So fordern Sie eine zusätzliche Zustimmung mithilfe der Auth-API an**

1. Das abgerufene Token `getAuthToken()` muss serverseitig mithilfe von AAD [im Auftrag von Fluss](/azure/active-directory/develop/v2-oauth2-on-behalf-of-flow) ausgetauscht werden, um Zugriff auf diese zusätzlichen Graph APIs zu erhalten. Stellen Sie sicher, dass Sie den v2-Graph-Endpunkt für diesen Austausch verwenden.
2. Wenn der Austausch fehlschlägt, gibt AAD eine Ausnahme für ungültige Genehmigungen zurück. Es gibt in der Regel eine von zwei Fehlermeldungen `invalid_grant` oder `interaction_required` .
3. Wenn der Austausch fehlschlägt, müssen Sie zusätzliche Zustimmung anfordern. Zeigen Sie eine Benutzeroberfläche an, auf der der Benutzer aufgefordert wird, eine zusätzliche Zustimmung zu erteilen. Diese Benutzeroberfläche muss eine Schaltfläche enthalten, die ein AAD-Zustimmungsdialogfeld mithilfe unserer [AAD-Authentifizierungs-API](~/concepts/authentication/auth-silent-aad.md)auslöst.
4. Wenn Sie weitere Zustimmung von AAD anfordern, müssen Sie `prompt=consent` AAD den [Abfragezeichenfolgenparameter](~/tabs/how-to/authentication/auth-silent-aad.md#get-the-user-context) hinzufügen, andernfalls fragt AAD nicht nach den zusätzlichen Bereichen.
    * Statt `?scope={scopes}`
    * Verwenden Sie diese `?prompt=consent&scope={scopes}`
    * Stellen Sie sicher, dass `{scopes}` alle Bereiche enthalten sind, für die Sie den Benutzer auffordern, z. B. Mail.Read oder User.Read.
5. Nachdem der Benutzer zusätzliche Berechtigungen erteilt hat, wiederholen Sie den "Im Auftrag von"-Fluss, um Zugriff auf diese zusätzlichen APIs zu erhalten.

### <a name="non-aad-authentication"></a>Nicht-AAD-Authentifizierung

Die oben beschriebene Authentifizierungslösung funktioniert nur für Apps und Dienste, die AAD als Identitätsanbieter unterstützen. Apps, die sich mit nicht-AAD-basierten Diensten authentifizieren möchten, müssen weiterhin den Popup-basierten [Webauthentifizierungsfluss verwenden.](~/concepts/authentication.md)

> [!NOTE]
> SSO wird für kundeneigene Apps innerhalb der AAD B2C-Mandanten unterstützt.
