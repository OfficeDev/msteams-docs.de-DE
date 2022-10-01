---
title: Hinzufügen des einmaligen Anmeldens zu Ihren Teams-Apps
author: zyxiaoyuer
description: In diesem Modul erfahren Sie, wie Sie einmaliges Anmelden (Single Sign-On, SSO) des Teams-Toolkits hinzufügen, SSO-Unterstützung aktivieren, Ihre Anwendung so aktualisieren, dass sie SSO verwendet
ms.author: surbhigupta
ms.localizationpriority: medium
ms.topic: overview
ms.date: 05/20/2022
ms.openlocfilehash: 9c221b0903d4541c4b0601e14ea347680140dfb9
ms.sourcegitcommit: 3aaccc48906fc6f6fbf79916af5664bf55537250
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2022
ms.locfileid: "68295963"
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
2. Wählen Sie "Teams Toolkit :::image type="content" source="~/assets/images/teams-toolkit-v2/teams-toolkit-sidebar-icon.png" alt-text="sso Add sidebar"::: " in der linken Navigationsleiste aus.
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

   |**Typ**|**Datei**|**Zweck**|
   |--------|--------|-----------|
   |Erstellen|`aad.template.json` Unter `template/appPackage`|Das Azure AD-Anwendungsmanifest stellt Ihre Azure AD-App dar. `template/appPackage` hilft beim Registrieren einer Azure AD-App während der lokalen Debug- oder Bereitstellungsphase.|
   |Ändern|`manifest.template.json` Unter `template/appPackage`|Ein `webApplicationInfo` Objekt wird ihrer Manifestvorlage der Teams-App hinzugefügt. Teams erfordert dieses Feld, um SSO zu aktivieren. Die Änderung wird wirksam, wenn Sie das lokale Debuggen oder bereitstellen auslösen.|
   |Erstellen|`auth/tab`|Referenzcode, Authentifizierungsumleitungsseiten und `README.md` Dateien werden in diesem Pfad für ein Registerkartenprojekt generiert.|
   |Erstellen|`auth/bot`|Referenzcode, Authentifizierungsumleitungsseiten und `README.md` Dateien werden in diesem Pfad für ein Botprojekt generiert.|

> [!Note]
> Durch das Hinzufügen von SSO ändert das Teams-Toolkit nichts in der Cloud, bis Sie das lokale Debuggen auslösen. Aktualisieren Sie Ihren Code, um sicherzustellen, dass SSO im Projekt funktioniert.

## <a name="update-your-application-to-use-sso"></a>Aktualisieren Ihrer Anwendung für die Verwendung von SSO

Die folgenden Schritte helfen Ihnen, SSO in Ihrer Anwendung zu aktivieren:

> [!NOTE]
> Diese Änderungen basieren auf den Vorlagen, die wir gerüsten.

---
<br>
<br><details>
<summary><b>Registerkartenprojekt </b></summary>

1. Kopieren `auth-start.html` und `auth-end.htm`** im `auth/public` Ordner in `tabs/public/`. Das Teams-Toolkit registriert diese beiden Endpunkte im Umleitungsfluss von Azure AD für Azure AD.

2. Ordner unter `auth/tab` kopieren `sso` nach `tabs/src/sso/`.

    * `InitTeamsFx`: Die Datei implementiert eine Funktion, die das TeamsFx SDK initialisiert und die Komponente öffnet `GetUserProfile` , nachdem das SDK initialisiert wurde.

    * `GetUserProfile`: Die Datei implementiert eine Funktion, die Microsoft Graph-API aufruft, um Benutzerinformationen abzurufen.

3. Ausführen `npm install @microsoft/teamsfx-react` unter `tabs/`.

4. Fügen Sie die folgenden Zeilen zum `tabs/src/components/sample/Welcome.tsx` Importieren hinzu `InitTeamsFx`:

    ```Bash

    import { InitTeamsFx } from "../../sso/InitTeamsFx";

    ```

5. Ersetzen Sie die folgende Zeile:

   `<AddSSO />`um `<InitTeamsFx />` die Komponente durch `InitTeamsFx` die `AddSso` Komponente zu ersetzen.

</details>
<details>
<summary><b>Bot-Projekt </b></summary>

#### <a name="set-up-the-azure-ad-redirects"></a>Einrichten der Azure AD-Umleitungen

1. Verschieben des Ordners `auth/bot/public` in `bot/src`. Dieser Ordner enthält HTML-Seiten, die von der Botanwendung gehostet werden. Wenn der Fluss für einmaliges Anmelden mit Azure AD initiiert wird, wird der Benutzer zu den HTML-Seiten umgeleitet.
1. Ändern Sie Ihre `bot/src/index` , um die entsprechenden `restify` Routen zu HTML-Seiten hinzuzufügen.

    ```ts
    const path = require("path");

    server.get(
        "/auth-*.html",
        restify.plugins.serveStatic({
            directory: path.join(__dirname, "public"),
        })
    );
    ```

#### <a name="update-your-app"></a>Aktualisieren Ihrer App

Der SSO-Befehlshandler `ProfileSsoCommandHandler` verwendet ein Azure AD-Token, um Microsoft Graph aufzurufen. Dieses Token wird mithilfe des angemeldeten Teams-Benutzertokens abgerufen. Der Fluss wird in einem Dialogfeld zusammengeführt, in dem bei Bedarf ein Zustimmungsdialogfeld angezeigt wird.

1. Datei `profileSsoCommandHandler` unter Ordner verschieben `auth/bot/sso` nach `bot/src`. `ProfileSsoCommandHandler` Klasse ist ein SSO-Befehlshandler, um Benutzerinformationen mit SSO-Token abzurufen, dieser Methode zu folgen und einen eigenen SSO-Befehlshandler zu erstellen.
1. Öffnen Sie `package.json` die Datei, und stellen Sie sicher, dass teamsfx SDK-Version >= 1.2.0
1. Führen Sie den `npm install isomorphic-fetch --save` Befehl im Ordner aus `bot` .
1. Führen Sie für ts-Skript den `npm install copyfiles --save-dev` Befehl im `bot` Ordner aus, und ersetzen Sie die folgenden Zeilen in `package.json`:

    ```json
    "build": "tsc --build && shx cp -r ./src/adaptiveCards ./lib/src",
    ```

     mit 

    ```json
    "build": "tsc --build && shx cp -r ./src/adaptiveCards ./lib/src && copyfiles src/public/*.html lib/",
    ```

    Dadurch werden die HTML-Seiten kopiert, die beim Erstellen des Botprojekts für die Authentifizierungsumleitung verwendet werden.

1. Damit der SSO-Zustimmungsfluss funktioniert, ersetzen Sie den folgenden Code in `bot/src/index` der Datei:

    ```ts
    server.post("/api/messages", async (req, res) => {
        await commandBot.requestHandler(req, res);
    });
    ```

     mit 

    ```ts
    server.post("/api/messages", async (req, res) => {
        await commandBot.requestHandler(req, res).catch((err) => {
            // Error message including "412" means it is waiting for user's consent, which is a normal process of SSO, sholdn't throw this error.
            if (!err.message.includes("412")) {
                throw err;
            }
        });
    });
    ```

1. Ersetzen Sie die Optionen zum `ConversationBot` `bot/src/internal/initialize` Hinzufügen der SSO-Konfiguration und des SSO-Befehlshandlers:

    ```ts
    export const commandBot = new ConversationBot({
        ...
        command: {
            enabled: true,
            commands: [new HelloWorldCommandHandler()],
        },
    });
    ```

     mit 

    ```ts
    import { ProfileSsoCommandHandler } from "../profileSsoCommandHandler";

    export const commandBot = new ConversationBot({
        ...
        // To learn more about ssoConfig, please refer teamsfx sdk document: https://docs.microsoft.com/microsoftteams/platform/toolkit/teamsfx-sdk
        ssoConfig: {
            aad :{
                scopes:["User.Read"],
            },
        },
        command: {
            enabled: true,
            commands: [new HelloWorldCommandHandler() ],
            ssoCommands: [new ProfileSsoCommandHandler()],
        },
    });
    ```

1. Registrieren Sie Ihren Befehl im Teams-App-Manifest. Öffnen Sie `templates/appPackage/manifest.template.json`den Bot, und fügen Sie die folgenden Zeilen in `commands` `commandLists` Ihrem Bot hinzu:

    ```json
    {
        "title": "profile",
        "description": "Show user profile using Single Sign On feature"
    }
    ```

#### <a name="add-a-new-sso-command-to-the-bot-optional"></a>Hinzufügen eines neuen SSO-Befehls zum Bot (optional)

Nachdem Sie SSO erfolgreich in Ihrem Projekt hinzugefügt haben, können Sie einen neuen SSO-Befehl hinzufügen.

1. Erstellen Sie eine neue Datei, z`photoSsoCommandHandler.ts`. B. oder `photoSsoCommandHandler.js` fügen `bot/src/` Sie einen eigenen SSO-Befehlshandler hinzu, um Graph-API aufzurufen:

    ```TypeScript
    // for TypeScript:
    import { Activity, TurnContext, ActivityTypes } from "botbuilder";
    import "isomorphic-fetch";
    import {
        CommandMessage,
        TriggerPatterns,
        TeamsFx,
        createMicrosoftGraphClient,
        TeamsFxBotSsoCommandHandler,
        TeamsBotSsoPromptTokenResponse,
    } from "@microsoft/teamsfx";

    export class PhotoSsoCommandHandler implements TeamsFxBotSsoCommandHandler {
        triggerPatterns: TriggerPatterns = "photo";

        async handleCommandReceived(
            context: TurnContext,
            message: CommandMessage,
            tokenResponse: TeamsBotSsoPromptTokenResponse,
        ): Promise<string | Partial<Activity> | void> {
            await context.sendActivity("Retrieving user information from Microsoft Graph ...");

            const teamsfx = new TeamsFx().setSsoToken(tokenResponse.ssoToken);

            const graphClient = createMicrosoftGraphClient(teamsfx, ["User.Read"]);

            let photoUrl = "";
            try {
                const photo = await graphClient.api("/me/photo/$value").get();
                const arrayBuffer = await photo.arrayBuffer();
                const buffer=Buffer.from(arrayBuffer, 'binary');
                photoUrl = "data:image/png;base64," + buffer.toString("base64");
            } catch {
                // Could not fetch photo from user's profile, return empty string as placeholder.
            }
            if (photoUrl) {
                const photoMessage: Partial<Activity> = {
                    type: ActivityTypes.Message, 
                    text: 'This is your photo:', 
                    attachments: [
                        {
                            name: 'photo.png',
                            contentType: 'image/png',
                            contentUrl: photoUrl
                        }
                    ]
                };
                return photoMessage;
            } else {
                return "Could not retrieve your photo from Microsoft Graph. Please make sure you have uploaded your photo.";
            }
        }
    }
    ```

    ```javascript
    // for JavaScript:
    const { ActivityTypes } = require("botbuilder");
    require("isomorphic-fetch");
    const { createMicrosoftGraphClient, TeamsFx } = require("@microsoft/teamsfx");

    class PhotoSsoCommandHandler {
        triggerPatterns = "photo";

        async handleCommandReceived(context, message, tokenResponse) {
            await context.sendActivity("Retrieving user information from Microsoft Graph ...");

            const teamsfx = new TeamsFx().setSsoToken(tokenResponse.ssoToken);

            const graphClient = createMicrosoftGraphClient(teamsfx, ["User.Read"]);
        
            let photoUrl = "";
            try {
                const photo = await graphClient.api("/me/photo/$value").get();
                const arrayBuffer = await photo.arrayBuffer();
                const buffer=Buffer.from(arrayBuffer, 'binary');
                photoUrl = "data:image/png;base64," + buffer.toString("base64");
            } catch {
            // Could not fetch photo from user's profile, return empty string as placeholder.
            }
            if (photoUrl) {
                const photoMessage = {
                    type: ActivityTypes.Message, 
                    text: 'This is your photo:', 
                    attachments: [
                        {
                            name: 'photo.png',
                            contentType: 'image/png',
                            contentUrl: photoUrl
                        }
                    ]
                };
                return photoMessage;
            } else {
                return "Could not retrieve your photo from Microsoft Graph. Please make sure you have uploaded your photo.";
            }
        }
    }

    module.exports = {
        PhotoSsoCommandHandler,
    };

    ```

1. Hinzufügen `PhotoSsoCommandHandler` einer Instanz zum `ssoCommands` Array in `bot/src/internal/initialize.ts`:

    ```ts
    // for TypeScript:
    import { PhotoSsoCommandHandler } from "../photoSsoCommandHandler";

    export const commandBot = new ConversationBot({
        ...
        command: {
            ...
            ssoCommands: [new ProfileSsoCommandHandler(), new PhotoSsoCommandHandler()],
        },
    });
    ```

    ```javascript
    // for JavaScript:
    ...
    const { PhotoSsoCommandHandler } = require("../photoSsoCommandHandler");

    const commandBot = new ConversationBot({
        ...
        command: {
            ...
            ssoCommands: [new ProfileSsoCommandHandler(), new PhotoSsoCommandHandler()]
        },
    });
    ...

    ```

1. Registrieren Sie Ihren Befehl im Teams-App-Manifest. Öffnen Sie `templates/appPackage/manifest.template.json`den Bot, und fügen Sie die folgenden Zeilen in `commands` `commandLists` Ihrem Bot hinzu:

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

Mit dem [Azure AD-App-Manifest](/azure/active-directory/develop/reference-app-manifest) können Sie verschiedene Aspekte der Anwendungsregistrierung anpassen. Sie können das Manifest nach Bedarf aktualisieren. Wenn Sie weitere API-Berechtigungen für den Zugriff auf die gewünschten APIs einschließen müssen, lesen Sie [API-Berechtigungen für den Zugriff auf die gewünschten APIs](https://github.com/OfficeDev/TeamsFx/wiki/#customize-aad-manifest-template).
Informationen zum Anzeigen Ihrer Azure AD-Anwendung in Azure-Portal finden [Sie unter Anzeigen der Azure AD-Anwendung in Azure-Portal](https://github.com/OfficeDev/TeamsFx/wiki/Manage-AAD-application-in-Teams-Toolkit#How-to-view-the-AAD-app-on-the-Azure-portal).

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
2. Benutzeridentität in Node.js Umgebung: `OnBehalfOfUserCredential` verwendet "On-Behalf-Of"-Fluss und SSO-Token.
3. Anwendungsidentität in Node.js Umgebung: `AppCredential` stellt die Anwendungsidentität dar.

Weitere Informationen zum TeamsFx SDK finden Sie unter:

* [TeamsFx SDK](TeamsFx-SDK.md) - oder [API-Referenz](/javascript/api/@microsoft/teamsfx/?view=msteams-client-js-latest&preserve-view=true)
* [Beispielkatalog für Microsoft Teams Framework (TeamsFx)](https://github.com/OfficeDev/TeamsFx-Samples/tree/v2)

## <a name="see-also"></a>Siehe auch

* [Voraussetzungen für das Erstellen Ihrer Teams-App](tools-prerequisites.md)
