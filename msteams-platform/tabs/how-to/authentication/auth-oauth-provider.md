---
title: Verwenden externer OAuth-Anbieter
description: Beschreibt die Authentifizierung mit externen OAuth-Anbietern
ms.topic: how-to
ms.localizationpriority: high
keywords: Teams-Authentifizierung mit externem OAuth-Anbieter
ms.openlocfilehash: df9a9e36ecd203cd2b6c482af00b60ddfb145114
ms.sourcegitcommit: ca902f505a125641c379a917ee745ab418bd1ce6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2022
ms.locfileid: "63464259"
---
# <a name="use-external-oauth-providers"></a>Verwenden externer OAuth-Anbieter

Mithilfe der aktualisierten `authenticate()` API können Sie externe oder Drittanbieter (3P) OAuth-Anbieter wie Google, GitHub, LinkedIn und Facebook unterstützen:

```JavaScript
function authenticate(authenticateParameters?: AuthenticateParameters)
``` 

Folgendes wird der `authenticate()` API hinzugefügt, um externe OAuth-Anbieter zu unterstützen:

* `isExternal` Parameter
* Zwei Platzhalterwerte im vorhandenen `url` Parameter

Die folgende Tabelle enthält die Liste der `authenticate()` API-Parameter und -Funktionen zusammen mit ihren Beschreibungen:

| Parameter| Beschreibung|
| --- | --- |
|`isExternal` | Der Parametertyp ist Boolean, was angibt, dass das Authentifizierungsfenster in einem externen Browser geöffnet wird.|
|`failureCallback`| Die Funktion wird aufgerufen, wenn die Authentifizierung fehlschlägt, und das Authentifizierungs-Popup gibt den Grund für das Scheitern an.|
|`height` |Die bevorzugte Höhe für das Pop-up. Der Wert kann ignoriert werden, wenn er außerhalb der akzeptablen Grenzen liegt.|
|`successCallback`| Die Funktion wird aufgerufen, wenn die Authentifizierung erfolgreich ist, wobei das Ergebnis aus dem Authentifizierungs-Popup zurückgegeben wird. Der Authentifizierungscode ist das Ergebnis.|
|`url`  <br>|Die URL des 3P-App-Servers für das Authentifizierungs-Popup mit den folgenden zwei Parameterplatzhaltern:</br> <br> - `oauthRedirectMethod`: Übergeben Sie den Platzhalter in `{}`. Dieser Platzhalter wird von der Teams-Plattform durch einen Deeplink oder eine Webseite ersetzt, die den App-Server informiert, wenn der Anruf von einer mobilen Plattform kommt.</br> <br> - `authId`: Dieser Platzhalter wird durch UUID ersetzt. Der App-Server verwendet es, um die Sitzung aufrechtzuerhalten.| 
|`width`|Die bevorzugte Breite für das Pop-up. Der Wert kann ignoriert werden, wenn er außerhalb der akzeptablen Grenzen liegt.|

Weitere Informationen zu Parametern finden Sie unter [Parameterschnittstelle authentifizieren](/javascript/api/@microsoft/teams-js/microsoftteams.authentication.authenticateparameters?view=msteams-client-js-latest&preserve-view=true).

## <a name="add-authentication-to-external-browsers"></a>Authentifizierung zu externen Browsern hinzufügen

> [!NOTE]
> * Derzeit können Sie die Authentifizierung zu externen Browsern nur für Registerkarten auf Mobilgeräten hinzufügen. 
> * Verwenden Sie die Beta-Version von JS SDK, um die Funktionalität zu nutzen. Betaversionen sind über [NPM](https://www.npmjs.com/package/@microsoft/teams-js/v/1.12.0-beta.2) verfügbar.

Das folgende Bild zeigt den Ablauf zum Hinzufügen der Authentifizierung zu externen Browsern:

 :::image type="content" source="../../../assets/images/tabs/tabs-authenticate-OAuth.PNG" alt-text="authenticate-OAuth" border="true":::

**So fügen Sie die Authentifizierung zu externen Browsern hinzu**

1. Initiieren Sie den externen Authentifizierungs- und Anmeldeprozess.

   Die 3P-App ruft die SDK-Funktion `microsoftTeams.authentication.authenticate` auf, wobei `isExternal` auf „true“ gesetzt ist, um den externen Authentifizierungs-Anmeldeprozess zu initiieren. 

   Die übergebene `url` enthält Platzhalter für `{authId}` und `{oauthRedirectMethod}`.  


    ```JavaScript
    microsoftTeams.authentication.authenticate({
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

   Der Benutzer meldet sich beim externen Browser an. Die OAuth-Anbieter leiten zurück zum `redirect_uri` mit dem Authentifizierungscode und dem Zustandsobjekt.

6. Der 3P-App-Server überprüft Teams und antwortet darauf.

   Der 3P-App-Server verarbeitet die Antwort und prüft `oauthRedirectMethod`, die vom externen OAuth-Anbieter im Zustandsobjekt zurückgegeben wird, um zu bestimmen, ob die Antwort über den auth-callback-Deeplink oder über die Webseite, die `notifySuccess()` aufruft, zurückgegeben werden muss.

      ```JavaScript
      const state = JSON.parse(req.query.state)
      if (state.oauthRedirectMethod === 'deeplink') {
         return res.redirect('msteams://teams.microsoft.com/l/auth-callback?authId=${state.authId}&code=${req.query.code}')
      }
      else {
      // continue redirecting to a web-page that will call notifySuccsss() – usually this method is used in Teams-Web
      …
      ```

7. Die 3P-App generiert einen Deeplink.

   Die 3P-App generiert einen Deeplink für Teams Mobile im folgenden Format und sendet den Authentifizierungscode mit der Sitzungs-ID zurück an Teams.

   ```JavaScript
   return res.redirect(`msteams://teams.microsoft.com/l/auth-callback?authId=${state.authId}&code=${req.query.code}`)
   ```

 8. Teams ruft einen Erfolgsrückruf auf und sendet das Ergebnis.

    Teams ruft den Erfolgsrückruf auf und sendet das Ergebnis (Authentifizierungscode) an die 3P-App. Die 3P-App empfängt den Code im Erfolgsrückruf und verwendet den Code, um das Token und dann die Benutzerinformationen abzurufen und die Benutzeroberfläche zu aktualisieren.

      ```JavaScript
      successCallback: function (result) { 
      … 
      } 
      ```

## <a name="see-also"></a>Siehe auch

* [Identitätsanbieter konfigurieren](../../../concepts/authentication/configure-identity-provider.md)
* [Microsoft Teams-Authentifizierungsablauf für Registerkarten](auth-flow-tab.md)
