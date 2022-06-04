---
title: Hinzufügen des einmaligen Anmeldens zu Ihren Teams-Apps
author: zyxiaoyuer
description: Describes Add single sign on of Teams Toolkit
ms.author: surbhigupta
ms.localizationpriority: medium
ms.topic: overview
ms.date: 05/20/2022
ms.openlocfilehash: 3b83104dd07d34989f85fa0b96182c5c43408d98
ms.sourcegitcommit: e16b51a49756e0fe4eaf239898e28d3021f552da
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2022
ms.locfileid: "65887590"
---
# <a name="add-single-sign-on-to-teams-app"></a>Hinzufügen des einmaligen Anmeldens zur Teams-App

Microsoft Teams bietet einmaliges Anmelden für die Anwendung, um ein angemeldetes Teams-Benutzertoken für den Zugriff auf Microsoft Graph und andere APIs abzurufen. Das Teams-Toolkit erleichtert die Interaktion, indem einige der Azure AD-Flüsse und -Integrationen hinter einigen einfachen APIs abstrahiert werden. Auf diese Weise können Sie Ihrer Teams-Anwendung ganz einfach Features für einmaliges Anmelden (Single Sign-On, SSO) hinzufügen.

Für Anwendungen, die mit dem Benutzer in einem Chat, einem Team oder einem Kanal interagieren, wird SSO als adaptive Karte manifestiert, mit der der Benutzer interagieren kann, um den Azure AD-Zustimmungsfluss aufzurufen.

## <a name="enable-sso-support"></a>Aktivieren der SSO-Unterstützung

Das Teams-Toolkit hilft Ihnen beim Hinzufügen von SSO zu den folgenden Teams-Funktionen:

* Tab
* Bot
* Benachrichtigungs-Bot: Server erneut aktualisieren
* Befehlsbot

### <a name="add-sso-using-visual-studio-code"></a>Hinzufügen von SSO mit Visual Studio Code

Die folgenden Schritte helfen Ihnen beim Hinzufügen von SSO mithilfe des Teams-Toolkits in Visual Studio Code

1. Öffnen Sie **Visual Studio Code.**
2. Wählen Sie "Teams Toolkit :::image type="content" source="../assets/images/teams-toolkit-v2/add-sso/teams-toolkit-sidebar-icon.png" alt-text="sso Add sidebar"::: " in der linken Navigationsleiste aus.
3. Wählen Sie unter **"ENTWICKLUNG****" die Option "Features hinzufügen"** aus.

    :::image type="content" source="../assets/images/teams-toolkit-v2/add-sso/sso-add features.png" alt-text="sso Features hinzufügen":::

    * Sie können auch die Befehlspalette öffnen und **Teams auswählen: Features hinzufügen**

4. Wählen Sie **"Einmaliges Anmelden" aus**.

    :::image type="content" source="../assets/images/teams-toolkit-v2/add-sso/sso-select features.png" alt-text="sso select":::

### <a name="add-sso-using-teamsfx-cli"></a>Hinzufügen von SSO mithilfe von TeamsFx CLI

Sie können den Befehl in Ihrem **Projektstammverzeichnis** ausführen`teamsfx add sso`.

> [!Note]
> Das Feature aktiviert SSO für alle vorhandenen anwendbaren Funktionen. Führen Sie die gleichen Schritte aus, um SSO zu aktivieren, wenn Sie dem Projekt später Funktionen hinzufügen.

## <a name="customize-your-project-using-teams-toolkit"></a>Anpassen Ihres Projekts mithilfe des Teams-Toolkits

In der folgenden Tabelle sind die Änderungen aufgeführt, die das Teams-Toolkit an Ihrem Projekt vornimmt:

   |**Type**|**Datei**|**Zweck**|
   |--------|--------|-----------|
   |Erstellen|`aad.template.json` Unter `template/appPackage`|Das Azure AD-Anwendungsmanifest stellt Ihre Azure AD-App dar. `template/appPackage` hilft beim Registrieren einer Azure AD-App während der lokalen Debug- oder Bereitstellungsphase.|
   |Ändern|`manifest.template.json` Unter `template/appPackage`|Ein `webApplicationInfo` Objekt wird ihrer Manifestvorlage der Teams-App hinzugefügt. Teams erfordert dieses Feld, um SSO zu aktivieren. Die Änderung wird wirksam, wenn Sie das lokale Debuggen oder bereitstellen auslösen.|
   |Erstellen|`auth/tab`|Referenzcode, Authentifizierungsumleitungsseiten und eine `README.md` Datei werden in diesem Pfad für ein Registerkartenprojekt generiert.|
   |Erstellen|`auth/bot`|Referenzcode, Authentifizierungsumleitungsseiten und eine `README.md` Datei werden in diesem Pfad für ein Botprojekt generiert.|

> [!Note]
> Durch das Hinzufügen von SSO ändert das Teams-Toolkit nichts in der Cloud, bis Sie das lokale Debuggen auslösen. Aktualisieren Sie Ihren Code, um sicherzustellen, dass SSO im Projekt funktioniert.

## <a name="update-your-application-to-use-sso"></a>Aktualisieren Ihrer Anwendung für die Verwendung von SSO

Mit den folgenden Schritten können Sie SSO in Ihrer Anwendung aktivieren.

> [!NOTE]
> Diese Änderungen basieren auf den Vorlagen, die wir gerüsten.

---
<br>
<br><details>
<summary><b>Registerkartenprojekt </b></summary>

1. Kopieren `auth-start.html` und `auth-end.htm`** im `auth/public` Ordner in `tabs/public/`. Das Teams-Toolkit registriert diese beiden Endpunkte im Umleitungsfluss von Azure AD für Azure AD.

2. Ordner unter `auth/tab` kopieren `sso` nach `tabs/src/sso/`.

    * `InitTeamsFx`: Die Datei implementiert eine Funktion, die das TeamsFx SDK initialisiert und die Komponente öffnet `GetUserProfile` , nachdem das SDK initialisiert wurde.

    * `GetUserProfile`: Die Datei implementiert eine Funktion, die die Microsoft Graph-API aufruft, um Benutzerinformationen abzurufen.

3. Ausführen `npm install @microsoft/teamsfx-react` unter `tabs/`.

4. Fügen Sie die folgenden Zeilen zum `tabs/src/components/sample/Welcome.tsx` Importieren hinzu `InitTeamsFx`:

    ```Bash

    import { InitTeamsFx } from "../../sso/InitTeamsFx";

    ```

5. Ersetzen Sie die folgende Zeile: `<AddSSO />` durch`<InitTeamsFx />`, um die Komponente durch `InitTeamsFx` die `AddSso` Komponente zu ersetzen.

</details>
<details>
<summary><b>Bot-Projekt </b></summary>

1. Ordner kopieren `auth/bot/public` nach `bot/src`. Die beiden Ordner enthalten HTML-Seiten, die für die Authentifizierungsumleitung verwendet werden. Sie müssen die Datei ändern `bot/src/index` , um diesen Seiten das Routing hinzuzufügen.

2. Ordner kopieren `auth/bot/sso` nach `bot/src`. Die beiden Ordner enthalten drei Dateien als Referenz für die SSO-Implementierung:

    * `showUserInfo`: Es implementiert eine Funktion zum Abrufen von Benutzerinformationen mit SSO-Token. Sie können dies befolgen, um eine eigene Methode zu erstellen, die ein SSO-Token erfordert.

    * `ssoDialog`: Es wird ein [ComponentDialog-Objekt](/javascript/api/botbuilder-dialogs/componentdialog?view=botbuilder-ts-latest&preserve-view=true) erstellt, das für SSO verwendet wird.

    * `teamsSsoBot`: Es erstellt einen [TeamsActivityHandler](/javascript/api/botbuilder/teamsactivityhandler?view=botbuilder-ts-latest&preserve-view=true) mit `ssoDialog` und fügt `showUserInfo` ihn als Befehl hinzu, der ausgelöst werden kann.

3. Folgen Sie dem Codebeispiel, und registrieren Sie Ihren eigenen Befehl `addCommand` in dieser Datei (optional).

4. Ausführen `npm install isomorphic-fetch` unter `bot/`.

5. Führen Sie die folgende Zeile in "package.json" aus`bot/`, und ersetzen Sie `npm install copyfiles` sie:
  
   ```JSON

   "build": "tsc --build",

    ```

    mit 

   ```JSON

   "build": "tsc --build && copyfiles public/*.html lib/",

   ```

   Die HTML-Seiten, die für die Authentifizierungsumleitung verwendet werden, werden beim Erstellen dieses Botprojekts kopiert.

6. Nachdem Sie die folgenden Dateien hinzugefügt haben, müssen Sie eine neue `teamsSsoBot` Instanz in `bot/src/index` der Datei erstellen. Ersetzen Sie den folgenden Code:

   ```Bash
  
   // Process Teams activity with Bot Framework.
   server.post("/api/messages", async (req, res) => {
   await commandBot.requestHandler(req, res);
   });  

   ```

    mit 

   ```Bash

   const handler = new TeamsSsoBot();
   // Process Teams activity with Bot Framework.
   server.post("/api/messages", async (req, res) => {
       await commandBot.requestHandler(req, res, async (context)=> {
           await handler.run(context);
       });
   });

   ```

7. Fügen Sie die HTML-Routen in der `bot/src/index` Datei hinzu:

   ```Bash

   server.get(
       "/auth-*.html",
       restify.plugins.serveStatic({
           directory: path.join(__dirname, "public"),
       })
   );

   ```

8. Fügen Sie die folgenden Zeilen zum `bot/src/index` Importieren `teamsSsoBot` hinzu und `path`:

   ```Bash

   // For ts:
   import { TeamsSsoBot } from "./sso/teamsSsoBot";
   const path = require("path");

   // For js:
   const { TeamsSsoBot } = require("./sso/teamsSsoBot");
   const path = require("path");

   ```

9. Registrieren Sie Ihren Befehl im Teams-App-Manifest. Öffnen Sie `templates/appPackage/manifest.template.json`den Bot, und fügen Sie die folgenden Zeilen in `command` `commandLists` Ihrem Bot hinzu:

   ```JSON

   {
       "title": "show",
       "description": "Show user profile using Single Sign On feature"
   }

   ```

</details>
<details>
<summary><b>Hinzufügen eines neuen Befehls zum Bot </b></summary>

> [!NOTE]
> Derzeit gelten diese Anweisungen für `command bot`. Wenn Sie mit einem `bot`Beginnen beginnen, sehen Sie sich [das Beispiel bot-sso an](https://github.com/OfficeDev/TeamsFx-Samples/tree/v2/bot-sso).

Die folgenden Schritte helfen Ihnen beim Hinzufügen eines neuen Befehls, nachdem Sie SSO in Ihrem Projekt hinzugefügt haben:

1. Erstellen Sie eine neue Datei (`todo.ts` oder `todo.js`) unter `bot/src/` und fügen Sie Ihre eigene Geschäftslogik hinzu, um die Graph-API aufzurufen:

# <a name="typescript"></a>[TypeScript](#tab/typescript)

   ```typescript
   // for TypeScript:
export async function showUserImage(
    context: TurnContext,
    ssoToken: string,
    param: any[]
): Promise<DialogTurnResult> {
    await context.sendActivity("Retrieving user photo from Microsoft Graph ...");

    // Init TeamsFx instance with SSO token
    const teamsfx = new TeamsFx().setSsoToken(ssoToken);

    // Update scope here. For example: Mail.Read, etc.
    const graphClient = createMicrosoftGraphClient(teamsfx, param[0]);
    
    // You can add following code to get your photo:
    // let photoUrl = "";
    // try {
    //   const photo = await graphClient.api("/me/photo/$value").get();
    //   photoUrl = URL.createObjectURL(photo);
    // } catch {
    //   // Could not fetch photo from user's profile, return empty string as placeholder.
    // }
    // if (photoUrl) {
    //   await context.sendActivity(
    //     `You can find your photo here: ${photoUrl}`
    //   );
    // } else {
    //   await context.sendActivity("Could not retrieve your photo from Microsoft Graph. Please make sure you have uploaded your photo.");
    // }

    return;
}  
   ```

# <a name="javascript"></a>[JavaScript](#tab/javascript)

   ```javaScript
   // for JavaScript:
export async function showUserImage(context, ssoToken, param) {
    await context.sendActivity("Retrieving user photo from Microsoft Graph ...");

    // Init TeamsFx instance with SSO token
    const teamsfx = new TeamsFx().setSsoToken(ssoToken);

    // Update scope here. For example: Mail.Read, etc.
    const graphClient = createMicrosoftGraphClient(teamsfx, param[0]);
    
    // You can add following code to get your photo:
    // let photoUrl = "";
    // try {
    //   const photo = await graphClient.api("/me/photo/$value").get();
    //   photoUrl = URL.createObjectURL(photo);
    // } catch {
    //   // Could not fetch photo from user's profile, return empty string as placeholder.
    // }
    // if (photoUrl) {
    //   await context.sendActivity(
    //     `You can find your photo here: ${photoUrl}`
    //   );
    // } else {
    //   await context.sendActivity("Could not retrieve your photo from Microsoft Graph. Please make sure you have uploaded your photo.");
    // }

    return;
}
   ```

---

2. Registrieren eines neuen Befehls

   * Fügen Sie die folgende Zeile für die neue Befehlsregistrierung mithilfe von `addCommand` `teamsSsoBot`:

     ```bash

     this.dialog.addCommand("ShowUserProfile", "show", showUserInfo);

     ```

   * Fügen Sie nach der obigen Zeile die folgenden Zeilen hinzu, um einen neuen Befehl `photo` zu registrieren und sich mit der oben hinzugefügten Methode `showUserImage` zu verbinden:

     ```bash

     // As shown here, you can add your own parameter into the `showUserImage` method
     // You can also use regular expression for the command here
     const scope = ["User.Read"];
     this.dialog.addCommand("ShowUserPhoto", new RegExp("photo\s*.*"), showUserImage, scope);

     ```

3. Registrieren Sie Ihren Befehl im Teams-App-Manifest. Öffnen Sie `templates/appPackage/manifest.template.json`den Bot, und fügen Sie die folgenden Zeilen in `command` `commandLists` Ihrem Bot hinzu:

   ```JSON

   {
       "title": "photo",
       "description": "Show user photo using Single Sign On feature"
   }

   ```

</details>
<br>

## <a name="debug-your-application"></a>Debuggen Sie Ihre Anwendung

Drücken Sie F5, um die Anwendung zu debuggen. Teams Toolkit verwendet die Azure AD-Manifestdatei, um eine Azure AD-Anwendung für SSO zu registrieren. Informationen zu lokalen Debugfunktionen des Teams-Toolkits finden Sie [unter "Lokales Debuggen Ihrer Teams-App](debug-local.md)".

## <a name="customize-azure-ad-application-registration"></a>Anpassen der Azure AD-Anwendungsregistrierung

Mit dem [Azure AD-App-Manifest](/azure/active-directory/develop/reference-app-manifest) können Sie verschiedene Aspekte der Anwendungsregistrierung anpassen. Sie können das Manifest nach Bedarf aktualisieren. Wenn Sie zusätzliche API-Berechtigungen für den Zugriff auf die gewünschten APIs einschließen müssen, lesen Sie [API-Berechtigungen für den Zugriff auf die gewünschten APIs](https://github.com/OfficeDev/TeamsFx/wiki/#customize-aad-manifest-template).
Informationen zum Anzeigen Ihrer Azure AD-Anwendung im Azure-Portal finden [Sie unter "Azure AD-Anwendung im Azure-Portal anzeigen](https://github.com/OfficeDev/TeamsFx/wiki/Manage-AAD-application-in-Teams-Toolkit#How-to-view-the-AAD-app-on-the-Azure-portal)".

## <a name="sso-authentication-concepts"></a>SSO-Authentifizierungskonzepte

Die folgenden Konzepte helfen Ihnen bei der SSO-Authentifizierung:

### <a name="working-of-sso-in-teams"></a>Arbeiten von SSO in Teams

Bei der SSO-Authentifizierung (Single Sign-On) in Microsoft Azure Active Directory (Azure AD) wird das Authentifizierungstoken automatisch aktualisiert, um zu minimieren, wie oft Benutzer ihre Anmeldeinformationen eingeben müssen. Wenn Benutzer der Verwendung Ihrer App zustimmen, müssen sie ihre Zustimmung auf einem anderen Gerät nicht erneut erteilen, da sie automatisch angemeldet werden.

Teams-Registerkarten und -Bots weisen einen ähnlichen Fluss für die SSO-Unterstützung auf. Weitere Informationen finden Sie unter:

1. [SSO-Authentifizierung (Single Sign-On) auf Registerkarten](../tabs/how-to/authentication/tab-sso-overview.md)
2. [SSO-Authentifizierung (Single Sign-On) in Bots](../bots/how-to/authentication/auth-aad-sso-bots.md)

### <a name="simplified-sso-with-teamsfx"></a>Vereinfachtes SSO mit TeamsFx

TeamsFx trägt dazu bei, die Entwickleraufgaben mithilfe von SSO zu reduzieren und auf Cloudressourcen bis hin zu Einzelzeilenanweisungen mit Nullkonfiguration zuzugreifen.

Mit dem TeamsFx SDK können Sie Benutzerauthentifizierungscode auf vereinfachte Weise mithilfe von Anmeldeinformationen schreiben:

1. Benutzeridentität in Browserumgebung: `TeamsUserCredential` stellt die Identität des aktuellen Teams-Benutzers dar.
2. Benutzeridentität in Node.js Umgebung: `OnBehalfOfUserCredentail` verwendet "On-Behalf-Of"-Fluss und SSO-Token.
3. Anwendungsidentität in Node.js Umgebung: `AppCredential` stellt die Anwendungsidentität dar.

Weitere Informationen zum TeamsFx SDK finden Sie unter:

* [TeamsFx SDK](TeamsFx-SDK.md) - oder [API-Referenz](/javascript/api/@microsoft/teamsfx/?view=msteams-client-js-latest&preserve-view=true)
* [Beispielkatalog für Microsoft Teams Framework (TeamsFx)](https://github.com/OfficeDev/TeamsFx-Samples/tree/v2)

## <a name="see-also"></a>Siehe auch

* [Vorbereiten von Konten zum Erstellen von Teams-Apps](accounts.md)
