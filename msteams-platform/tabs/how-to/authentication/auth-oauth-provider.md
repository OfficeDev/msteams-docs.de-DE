---
title: Verwenden externer OAuth-Anbieter
description: Authentifizieren Sie Ihre App-Benutzer mithilfe externer OAuth-Anbieter, und erfahren Sie, wie Sie sie dem externen Browser hinzufügen.
ms.topic: how-to
ms.localizationpriority: high
ms.openlocfilehash: 4892dc23174e34015a02a9afff64269e01871fb5
ms.sourcegitcommit: c1032ea4f48c4bbf5446798ff7d46d7e6e9f55d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2022
ms.locfileid: "68027319"
---
# <a name="use-external-oauth-providers"></a>Verwenden externer OAuth-Anbieter

[!INCLUDE [sdk-include](~/includes/sdk-include.md)]

Mithilfe der aktualisierten `authenticate()` API können Sie externe oder Drittanbieter (3P) OAuth-Anbieter wie Google, GitHub, LinkedIn und Facebook unterstützen:

```JavaScript
function authenticate(authenticateParameters: AuthenticatePopUpParameters): Promise<string>
```

Folgendes wird der `authenticate()` API hinzugefügt, um externe OAuth-Anbieter zu unterstützen:

* `isExternal` Parameter
* Zwei Platzhalterwerte im vorhandenen `url` Parameter

Die folgende Tabelle enthält die Liste der `authenticate()` API-Parameter (`AuthenticatePopUpParameters`) und Funktionen sowie deren Beschreibungen:

| Parameter| Beschreibung|
| --- | --- |
|`isExternal` | Der Parametertyp ist Boolean, was angibt, dass das Authentifizierungsfenster in einem externen Browser geöffnet wird.|
|`height` |Die bevorzugte Höhe für das Pop-up. Der Wert kann ignoriert werden, wenn er außerhalb der akzeptablen Grenzen liegt.|
|`url`  <br>|Die URL des 3P-App-Servers für das Authentifizierungs-Popup mit den folgenden zwei Parameterplatzhaltern:</br> <br> - `oauthRedirectMethod`: Pass placeholder in `{}`. This placeholder is replaced by deeplink or web page by Teams platform, which informs app server if the call is coming from mobile platform.</br> <br> - `authId`: Dieser Platzhalter wird durch UUID ersetzt. Der App-Server verwendet es, um die Sitzung aufrechtzuerhalten.|
|`width`|Die bevorzugte Breite für das Pop-up. Der Wert kann ignoriert werden, wenn er außerhalb der akzeptablen Grenzen liegt.|

Weitere Informationen zu Parametern finden Sie unter der [Authenticate(AuthenticatePopUpParameters)](/javascript/api/@microsoft/teams-js/authentication#@microsoft-teams-js-authentication-authenticate) -Funktion.

## <a name="add-authentication-to-external-browsers"></a>Authentifizierung zu externen Browsern hinzufügen

> [!NOTE]
>
> * Derzeit können Sie die Authentifizierung zu externen Browsern nur für Registerkarten auf Mobilgeräten hinzufügen.
> * Verwenden Sie die Beta-Version von JS SDK, um die Funktionalität zu nutzen. Betaversionen sind über [NPM](https://www.npmjs.com/package/@microsoft/teams-js/v/1.12.0-beta.2) verfügbar.

Das folgende Bild zeigt den Ablauf zum Hinzufügen der Authentifizierung zu externen Browsern:

 :::image type="content" source="../../../assets/images/tabs/tabs-authenticate-OAuth.PNG" alt-text="authenticate-OAuth":::

**So fügen Sie die Authentifizierung zu externen Browsern hinzu**

1. Initiieren Sie den externen Authentifizierungs- und Anmeldeprozess.

   Die 3P-App ruft die SDK-Funktion `authentication.authenticate` auf, wobei `isExternal` auf „true“ gesetzt ist, um den externen Authentifizierungs-Anmeldeprozess zu initiieren.

   Die übergebene `url` enthält Platzhalter für `{authId}` und `{oauthRedirectMethod}`.  

    ```JavaScript
    import { authentication } from "@microsoft/teams-js";
    authentication.authenticate({
       url: 'https://3p.app.server/auth?oauthRedirectMethod={oauthRedirectMethod}&authId={authId}',
       isExternal: true,
       successCallback: function (result) {
       //sucess 
       } failureCallback: function (reason) {
       //failure 
        }
    });
    ```

2. Der Teams-Link öffnet sich in einem externen Browser.

   Die Teams Clients öffnen die URL in einem externen Browser, nachdem sie die Platzhalter für `oauthRedirectMethod` und `authId` durch geeignete Werte ersetzt haben.

   #### <a name="example"></a>Beispiel

   ```http
    https://3p.app.server/auth?oauthRedirectMethod=deeplink&authId=1234567890 
   ```

3. Der 3P-App-Server antwortet.

   Der 3P-App-Server empfängt und speichert die `url` mit den folgenden beiden Abfrageparametern:

   | Parameter | Beschreibung|
   | --- | --- |
   | `oauthRedirectMethod` |Gibt an, wie die 3P-App die Antwort der Authentifizierungsanforderung zurück an Teams senden muss, mit einem der beiden Werte: Deeplink oder Seite.|
   |`authId` | Die Anforderungs-ID, die Teams für diese spezifische Authentifizierungsanforderung erstellt haben und die über Deeplink an Teams zurückgesendet werden muss.|

    > [!TIP]
    > Die 3P-App kann `authId`, `oauthRedirectMethod` im OAuth `state` Abfrageparameter marshallen, während sie die Anmelde-URL für den OAuthProvider generiert. Die `state` enthält die übergebenen `authId` und `oauthRedirectMethod`, wenn OAuthProvider zurück an den 3P-Server umleitet und die 3P-App die Werte zum Senden der Authentifizierungsantwort an Teams verwendet, wie in **beschrieben 6. Die Antwort des 3P-App-Servers auf Teams**.

4. Der 3P-App-Server leitet zur angegeben `url` weiter.

   Der 3P-App-Server leitet zur Authentifizierungsseite des OAuth-Anbieters im externen Browser um. Die `redirect_uri` ist eine dedizierte Route auf dem 3P-App-Server. Sie können `redirect_uri` in der Entwicklungskonsole des OAuth-Anbieters als statisch registrieren, die Parameter müssen über das Zustandsobjekt gesendet werden.

   #### <a name="example"></a>Beispiel

    ```http
    https://accounts.google.com/o/oauth2/v2/auth?redirect_uri=https://3p.app.server/authredirect&state={"authId":"…","oauthRedirectMethod":"…"}&client_id=…    &response_type=code&access_type=offline&scope= … 
    ```

5. Melden Sie sich beim externen Browser an.

   User signs in to the external browser. The OAuth providers redirects back to the `redirect_uri` with the auth code and the state object.

6. Der 3P-App-Server überprüft Teams und antwortet darauf.

   Der 3P-App-Server verarbeitet die Antwort und prüft `oauthRedirectMethod`, die vom externen OAuth-Anbieter im Zustandsobjekt zurückgegeben wird, um zu bestimmen, ob die Antwort über den auth-callback-Deeplink oder über die Webseite, die `notifySuccess()` aufruft, zurückgegeben werden muss.

      ```JavaScript
      const state = JSON.parse(req.query.state)
      if (state.oauthRedirectMethod === 'deeplink') {
         return res.redirect('msteams://teams.microsoft.com/l/auth-callback?authId=${state.authId}&result=${req.query.code}')
      }
      else {
      // continue redirecting to a web-page that will call notifySuccess() – usually this method is used in Teams-Web
      …
      ```

7. Die 3P-App generiert einen Deeplink.

   Die 3P-App generiert einen Deeplink für Teams Mobile im folgenden Format und sendet den Authentifizierungscode mit der Sitzungs-ID zurück an Teams.

   ```JavaScript
   return res.redirect(`msteams://teams.microsoft.com/l/auth-callback?authId=${state.authId}&result=${req.query.code}`)
   ```

8. Teams ruft einen Erfolgsrückruf auf und sendet das Ergebnis.

    Teams ruft den Erfolgsrückruf auf und sendet das Ergebnis (Authentifizierungscode) an die 3P-App. Die 3P-App empfängt den Code im Erfolgsrückruf und verwendet den Code, um das Token und dann die Benutzerinformationen abzurufen und die Benutzeroberfläche zu aktualisieren.

      ```JavaScript
      successCallback: function (result) { 
      … 
      } 
      ```

## <a name="see-also"></a>Siehe auch

* [Identitätsanbieter konfigurieren](~/concepts/authentication/authentication.md)
* [Microsoft Teams-Authentifizierungsablauf für Registerkarten](auth-flow-tab.md)
