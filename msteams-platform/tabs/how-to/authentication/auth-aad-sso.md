---
title: Einmaliges Anmelden
description: Beschreibt einmaliges Anmelden (Single Sign-on, SSO)
keywords: Teams-Authentifizierung SSO-Aad
ms.openlocfilehash: 1857651aecd902f04bd57f5b4e2fb0fda88eb348
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674092"
---
# <a name="single-sign-on"></a>Einmaliges Anmelden

> [!NOTE]
> Die API für einmaliges Anmelden wird derzeit nur in der _Entwicklervorschau_ unterstützt.

Benutzer melden sich bei Microsoft Teams mit Ihrem Schulkonto (Office 365) an, und Sie können dies mithilfe von Single Sign-on (SSO) nutzen, um den Benutzer auf Ihrer Microsoft Teams-Registerkarte zu autorisieren. Das heißt, wenn ein Benutzer einwilligt, die APP auf dem Desktop zu verwenden, muss er sich nicht erneut auf dem Handy anmelden und wird automatisch angemeldet. 

## <a name="how-sso-works-at-runtime"></a>Funktionsweise von SSO zur Laufzeit

Das folgende Diagramm zeigt die Funktionsweise des SSO-Prozesses:

<img src="~/assets/images/tabs/tabs-sso-diagram.png" alt="Tab single sign-on SSO diagram" width="75%"/>

1. In der Registerkarte ruft JavaScript getAuthToken () auf. Dadurch wird die Teams-Anwendung aufgefordert, ein Authentifizierungstoken für die Registerkarten Anwendung abzurufen.
2. Wenn der aktuelle Benutzer die Tab-Anwendung zum ersten Mal verwendet hat, wird er zur Zustimmung aufgefordert (falls eine Zustimmung erforderlich ist) oder aufgefordert, die Step-up-Authentifizierung zu behandeln (beispielsweise die zweistufige Authentifizierung).
3. Die Microsoft Teams-Anwendung fordert das Registerkarten-Anwendungs Token vom Azure AD v 1.0-Endpunkt für den aktuellen Benutzer an.
4. Azure AD sendet das Registerkarten-Anwendungs Token an die Teams-Anwendung.
5. Die Microsoft Teams-Anwendung sendet das Registerkarten-Anwendungs Token als Teil des result-Objekts, das vom Aufruf von getAuthToken () zurückgegeben wird.
6. JavaScript in der Registerkarten Anwendung kann das Token analysieren und die benötigten Informationen extrahieren, beispielsweise die e-Mail-Adresse des Benutzers.
    * Hinweis: dieses Token gilt nur für Zustimmung zu einer begrenzten Gruppe von APIs auf Benutzerebene (ex: e-Mail, Profil usw.) und nicht für weitere Diagrammbereiche (beispielsweise "Mail. Read"). In unserem Abschnitt am Ende dieses Dokuments finden Sie Empfohlene Problemumgehungen, wenn Sie zusätzliche Diagrammbereiche benötigen.

## <a name="develop-an-sso-microsoft-teams-tab"></a>Entwickeln einer SSO-Microsoft Teams-Registerkarte

In diesem Abschnitt werden die Aufgaben im Zusammenhang mit dem Erstellen einer Microsoft Teams-Registerkarte beschrieben, die SSO verwendet. Diese Aufgaben werden hier auf eine von Sprache und Framework unabhängige Weise beschrieben.

### <a name="1-create-your-aad-application-in-azure"></a>1. Erstellen der Aad-Anwendung in Azure

Registrieren Sie Ihre Anwendung im Registrierungs Portal für den Azure AD v 1.0-Endpunkt. Dieser Prozess dauert fünf bis zehn Minuten und umfasst die folgenden Aufgaben:

* Aad-Anwendungs-ID wird abgerufen
* Geben Sie die Berechtigungen an, die Ihre Anwendung für den Aad-Endpunkt (und optional für Microsoft Graph) benötigt. 
* Gewähren Sie der Microsoft Teams-Desktop-,-Webanwendung und der mobilen Anwendung eine Vertrauensstellung für Ihre Anwendung.
* Vorautorisieren der Microsoft Teams-Anwendung für Ihre APP mit dem Standardbereichs Namen `access_as_user`von.

> [!NOTE]
> Es gibt einige wichtige Einschränkungen, die Sie beachten sollten:
>
> * Wir unterstützen nur Graph-API-Berechtigungen auf Benutzerebene (IE: e-Mail, Profil, offline_access, OpenID. Wenn Sie Zugriff auf andere Diagrammbereiche benötigen, lesen Sie unsere empfohlene Problemumgehung am Ende dieser Dokumentation.
> * Es ist wichtig, dass der Domänenname Ihrer Anwendung bei ihrer Azure AD Anwendung registriert wird. Dabei muss es sich um den Domänennamen handeln, auf dem die Anwendung ausgeführt wird, wenn ein Authentifizierungstoken in Microsoft Teams angefordert wird, und auch, wenn die Resource-Eigenschaft in Ihrem Teams-Manifest angegeben wird (weitere Details im nächsten Abschnitt).
> * Wir unterstützen derzeit nicht mehrere Domänen pro app.
> * Wir unterstützen auch keine Anwendungen, die die `azurewebsites.net` Domäne verwenden, da diese Domäne zu häufig ist und möglicherweise ein Sicherheitsrisiko darstellt.

#### <a name="steps"></a>Schritte

1. Registrieren einer neuen Anwendung im [Azure Active Directory – App-Registrierungs](https://go.microsoft.com/fwlink/?linkid=2083908) Portal
2. Wählen Sie "neue Registrierung" aus. Legen Sie auf der Seite Anwendung registrieren die folgenden Werte fest:
    * **Name** auf Ihren APP-Namen festlegen
    * Festlegen **unterstützter Kontotypen** auf **Konten in einem Organisations Verzeichnis und persönlichen Microsoft-Konten**
    * Lassen Sie die **Umleitungs-URI** leer.
    * Wählen Sie **registrieren** aus.
3. Kopieren und speichern Sie auf der Übersichtsseite die **Anwendungs-ID (Client)**. Sie benötigen Sie später beim Aktualisieren des Teams-Anwendungsmanifests.
4. Wählen Sie unter **Verwalten** die Option **Eine API verfügbar machen** aus. Wählen Sie den Link **festlegen** aus, um den Anwendungs-ID-URI `api://{AppID}`in Form von zu generieren. Fügen Sie den vollqualifizierten Domänennamen zwischen den doppelten Schrägstrichen und der GUID (mit einem Schrägstrich "/" am Ende hinzugefügt) ein. Die gesamte ID sollte folgende Form haben:`api://fully-qualified-domain-name.com/{AppID}`
    * Ex: `api://subdomain.example.com:6789/c6c1f32b-5e55-4997-881a-753cc1d563b7`.

> [!NOTE]
> Wenn eine Fehlermeldung angezeigt wird, die besagt, dass die Domäne bereits beansprucht wird, Sie jedoch der Eigentümer sind, folgen Sie dem Verfahren unter [Schnellstart: Hinzufügen eines benutzerdefinierten Domänennamens zu Azure Active Directory](/azure/active-directory/fundamentals/add-custom-domain), um sie zu registrieren. Wiederholen Sie dann den Vorgang. (Dieser Fehler kann auch auftreten, wenn Sie nicht mit den Anmeldeinformationen eines Administrators im Office 365 Mandanten angemeldet sind).

5. Wählen Sie die Schaltfläche**Bereich hinzufügen** aus. Geben Sie im Bereich, der geöffnet wird, `access_as_user` für**Bereichsname** ein.
6. Festlegen, wer einwilligen kann? an Administratoren und Benutzer
7. Füllen Sie die Felder für die Konfiguration der Administrator-und Benutzer Zustimmungs Ansagen mit Werten aus `access_as_user` , die für den Bereich geeignet sind. Vorschläge:
    * **Titel der Administrator Zustimmung:** Teams können auf das Profil des Benutzers zugreifen
    * **Administrator-Zustimmungs Beschreibung**: ermöglicht Teams das Aufrufen der webapin der App als aktueller Benutzer.
    * **Benutzer Zustimmungs Titel**: Teams können auf Ihr Benutzerprofil zugreifen und in Ihrem Namen Anfragen stellen
    * **Beschreibung der Benutzer Zustimmung:** Aktivieren von Teams zum Aufrufen der APIs dieser APP mit den gleichen Rechten
8. Sicherstellen, dass der **Status** auf " **aktiviert** " festgelegt ist
9. **Bereich "hinzufügen** " auswählen
    * Hinweis: der Domänenteil des **Bereichsnamens** , der direkt unterhalb des Textfelds angezeigt wird, sollte automatisch mit dem im vorherigen Schritt festgelegten **Anwendungs-ID** -URI übereinstimmen, wobei `/access_as_user` der Wert am Ende angefügt ist. Zum Beispiel: 
        * `api://subdomain.example.com:6789/c6c1f32b-5e55-4997-881a-753cc1d563b7/access_as_user`
10. Im Abschnitt **autorisierte Clientanwendungen** identifizieren Sie die Anwendungen, die Sie für die Webanwendung Ihrer APP autorisieren möchten. Jeder der folgenden IDs muss eingegeben werden:
    * `1fec8e78-bce4-4aaf-ab1b-5451cc387264`(Mobile Teams/Desktopanwendung)
    * `5e3ce6c0-2b1f-4285-8d4b-75ee78787346`(Microsoft Teams-Webanwendung)
11. Navigieren Sie zu **API-Berechtigungen**, und stellen Sie sicher, dass Sie die folgenden Berechtigungen hinzufügen:
    * User. Read (standardmäßig aktiviert)
    * email
    * offline_access
    * openid
    * profile

### <a name="2-update-your-microsoft-teams-application-manifest"></a>2. Aktualisieren des Microsoft Teams-Anwendungsmanifests

Fügen Sie Ihrem Microsoft Teams-Manifest neue Eigenschaften hinzu:

* **WebApplicationInfo**: Das übergeordnete Element der folgenden Elemente.
* **ID** – die Client-ID der Anwendung. Hierbei handelt es sich um eine Anwendungs-ID, die Sie im Rahmen der Registrierung der Anwendung mit Azure AD 1,0-Endpunkt erhalten.
* **Resource** – die Domäne und Unterdomäne Ihrer Anwendung. Hierbei handelt es sich um den gleichen URI `api://` (einschließlich des Protokolls), den Sie bei der Registrierung der app in Aad verwendet haben. Der Domänenteil dieses URIs sollte der Domäne entsprechen, einschließlich aller Unterdomänen, die in den URLs im Abschnitt Ihres Teams-Anwendungsmanifests verwendet werden.

```json
"webApplicationInfo": {
  "id": "<application_GUID here>",
  "resource": "<web_API resource here>"
}
```

Hinweise:

* Die Ressource für eine Aad-APP ist in der Regel nur der Stamm der Website-URL und der Anwendungs- `api://subdomain.example.com/6789/c6c1f32b-5e55-4997-881a-753cc1d563b7`ID (beispielsweise). Dieser Wert wird auch verwendet, um sicherzustellen, dass Ihre Anforderung aus derselben Domäne stammt. Vergewissern Sie sich daher, `contentURL` dass für Ihre Registerkarte die gleichen Domänen wie für Ihre Ressourceneigenschaft verwendet werden.
* Sie müssen manifestVersion Version 1,5 oder höher verwenden, damit diese Felder verwendet werden.
* Bereiche werden im Manifest nicht unterstützt und sollten stattdessen im Abschnitt API-Berechtigungen im Azure-Portal angegeben werden.

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

<img src="~/assets/images/tabs/tabs-sso-prompt.png" alt="Tab single sign-on SSO dialog prompt" width="75%"/>

## <a name="demo-code"></a>Demo Code

Jetzt können Sie unsere Test Anwendungs [Aufgabe Meow](https://github.com/ydogandjiev/taskmeow) besuchen und das SSO-Manifest und das `teams.auth.service.js` Auschecken `sso.auth.service.js` der und-Datei verwenden, um zu sehen, wie der Authentifizierungs Workflow behandelt wird.

## <a name="known-limitations"></a>Bekannte Einschränkungen

### <a name="apps-that-require-additional-graph-scopes"></a>Apps, die zusätzliche Diagrammbereiche erfordern

Unsere aktuelle Implementierung für SSO erteilt nur Zustimmung für Berechtigungen auf Benutzerebene (e-Mail, Profil, offline_access, OpenID), jedoch nicht für andere APIs (wie "Mail. Read"). Wenn Ihre APP weitere Diagrammbereiche benötigt, gibt es einige Problemumgehungen, um dies zu ermöglichen.

#### <a name="tenant-admin-consent"></a>Zustimmung des Mandanten Administrators

Der einfachste Ansatz wäre, einen mandantenadministrator zur Vorabgenehmigung im Namen der Organisation zu verschaffen. Dies bedeutet, dass Benutzer diesen Bereichen nicht zustimmen müssen und Sie dann frei sein können, die tokenserver-Seite mithilfe des Aad [im Auftrag von Flow](/azure/active-directory/develop/v1-oauth2-on-behalf-of-flow)auszutauschen. Diese Problemumgehung ist für interne Branchenanwendungen akzeptabel, aber möglicherweise nicht ausreichend für ISVs, die sich möglicherweise nicht auf die Genehmigung des Mandanten Administrators verlassen können.

Eine einfache Möglichkeit, im Namen einer Organisation (als mandantenadministrator) einzuwilligen, ist das Besuchen von:

* `https://login.microsoftonline.com/common/adminconsent?client_id=<AAD_App_ID>`

#### <a name="asking-for-additional-consent-using-the-auth-api"></a>Bitten um zusätzliche Zustimmung mithilfe der Authentifizierungs-API

Ein weiterer Ansatz für das Hinzufügen zusätzlicher Diagrammbereiche wäre die Präsentation eines Zustimmungs Dialogs mithilfe unseres vorhandenen [webbasierten Aad-Authentifizierungs Ansatzes](~/tabs/how-to/authentication/auth-tab-aad.md#navigate-to-the-authorization-page-from-your-popup-page) , der das Auftauchen eines Aad-Zustimmungs Dialogs beinhaltet. Es gibt einige bemerkenswerte Ergänzungen:

1. Das mit getAuthToken abgerufene Token muss serverseitig mithilfe [von AADs im Auftrag von Flow](/azure/active-directory/develop/v1-oauth2-on-behalf-of-flow) ausgetauscht werden, um Zugriff auf diese zusätzlichen Graph-APIs zu erhalten.
    * Stellen Sie sicher, dass Sie den V2-Graph-Endpunkt für diesen Exchange verwenden.
2. Wenn der Exchange-Fehler auftritt, gibt Aad eine ungültige Grant-Ausnahme zurück. Normalerweise gibt es eine von zwei Fehler `ConsentRequired` Meldungen: oder`InteractionRequired`
3. Wenn der Exchange-Fehler auftritt, müssen Sie um zusätzliche Zustimmung bitten. Es wird empfohlen, einige Benutzeroberflächen anzuzeigen, in denen der Benutzer aufgefordert wird, zusätzliche Zustimmung zu erteilen. Diese Benutzeroberfläche sollte eine Schaltfläche enthalten, die ein Aad-Zustimmungsdialogfeld mithilfe unserer [Aad-Authentifizierungs-API](~/concepts/authentication/auth-silent-aad.md)auslöst.
4. Wenn Sie eine zusätzliche Zustimmung von Aad anfordern, müssen Sie den `prompt=consent` [Abfrage-String-Parameter](~/tabs/how-to/authentication/auth-silent-aad.md#get-the-user-context) in Aad einschließen, da andernfalls Aad keine weiteren Bereiche abgefragt wird.
    * Statt:`?scope={scopes}`
    * Verwenden Sie Folgendes:`?prompt=consent&scope={scopes}`
    * Stellen Sie sicher `{scopes}` , dass alle Bereiche eingeschlossen sind, für die Sie den Benutzer auffordern (z. b.: Mail. Read oder User. Read).
5. Nachdem der Benutzer zusätzliche Berechtigungen erteilt hat, wiederholen Sie den Vorgang im Auftrag von Flow, um Zugriff auf diese zusätzlichen APIs zu erhalten.

### <a name="non-aad-authentication"></a>Nicht-Aad-Authentifizierung

Die oben beschriebene Authentifizierungslösung funktioniert nur für apps und Dienste, die Azure AD als Identitätsanbieter unterstützen. Apps, die mit nicht-Aad basierten Diensten authentifiziert werden möchten, müssen weiterhin den Popup basierten [Webauthentifizierungs Fluss](~/concepts/authentication.md)verwenden.
