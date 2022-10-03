---
title: TeamsFx SDK
author: surbhigupta
description: In diesem Modul erfahren Sie mehr über das TeamsFx SDK, Kernkonzepte und Codestruktur, erweiterte Anpassungen und Szenarien
ms.author: v-amprasad
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 9d870680e146564bb23db0193d2e2b116a249009
ms.sourcegitcommit: 16898eebeddc1bc1ac0d9862b4627c3bb501c109
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2022
ms.locfileid: "68327587"
---
# <a name="teamsfx-sdk"></a>TeamsFx SDK

TeamsFx trägt dazu bei, Ihre Aufgaben zu reduzieren, indem Microsoft Teams Single Sign-On (Teams SSO) verwendet wird und auf Cloudressourcen bis hin zu einzeiligen Anweisungen mit Nullkonfiguration zugegriffen wird. Sie können das TeamsFx SDK in Browser- und Node.js-Umgebung verwenden. Auf die Kernfunktionen von TeamsFx kann in der Client- und Serverumgebung zugegriffen werden. Sie können Benutzerauthentifizierungscode auf eine vereinfachte Weise für Folgendes schreiben:

* Registerkarte "Teams"
* Teams-Bot
* Azure Function

## <a name="prerequisites"></a>Voraussetzungen

Sie müssen die folgenden Tools installieren und Ihre Entwicklungsumgebung einrichten:

| &nbsp; | Installieren | Zum Benutzen... |
   | --- | --- | --- |
   | &nbsp; | [Visual Studio Code](https://code.visualstudio.com/download) | Build-Umgebungen für JavaScript, TypeScript oder SharePoint Framework (SPFx). Verwenden Sie Version 1.55 oder höher. |
   | &nbsp; | [Teams Toolkit](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension)| Eine Microsoft Visual Studio Code-Erweiterung, die ein Projektgerüst für Ihre App erstellt. Verwenden Sie version 4.0.0. |
   | &nbsp; | [Node.js](https://nodejs.org/en/download/) | Back-End-JavaScript-Laufzeitumgebung. Verwenden Sie die neueste Version von v16 LTS.|
   | &nbsp; | [Microsoft Teams](https://www.microsoft.com/microsoft-teams/download-app) | Microsoft Teams für die Zusammenarbeit mit allen, mit denen Sie zusammenarbeiten, über Apps für Chats, Besprechungen und Anrufe – alles an einem Ort.|
   | &nbsp; | [Microsoft&nbsp; Edge](https://www.microsoft.com/edge) (empfohlen) oder [Google Chrome](https://www.google.com/chrome/) | Ein Browser mit Entwicklertools. |

> [!NOTE]
> Wenn Ihr Projekt verwandte `botbuilder` Pakete als [Abhängigkeiten](https://github.com/Microsoft/botbuilder-js#packages) installiert hat, stellen Sie sicher, dass sie dieselbe Version haben.

Sie müssen über Arbeitskenntnisse verfügen über:

* [Quellcode](https://github.com/OfficeDev/TeamsFx/tree/main/packages/sdk)
* [Paket (NPM)](https://www.npmjs.com/package/@microsoft/teamsfx)
* [API-Referenzdokumentation](https://aka.ms/teamsfx-sdk-help)
* [Beispiele](https://github.com/OfficeDev/TeamsFx-Samples)

## <a name="get-started"></a>Erste Schritte

TeamsFx SDK ist im Gerüstprojekt mit TeamsFx Toolkit oder CLI vorkonfiguriert.
Weitere Informationen finden Sie unter [Teams-App-Projekt](https://github.com/OfficeDev/TeamsFx/blob/main/packages/vscode-extension/README.md).

### <a name="install-the-microsoftteamsfx-package"></a>Installieren Sie das `@microsoft/teamsfx` Paket

Installieren Sie das TeamsFx SDK für TypeScript oder JavaScript mit `npm`:

```bash
npm install @microsoft/teamsfx
```

## <a name="teamsfx-core-functionalities"></a>Kernfunktionen von TeamsFx

### <a name="teamsfx-class"></a>TeamsFx-Klasse

TeamsFx-Klasseninstanzen greifen standardmäßig auf alle TeamsFx-Einstellungen aus Umgebungsvariablen zu. Sie können auch benutzerdefinierte Konfigurationswerte festlegen, um die Standardwerte zu überschreiben. Einzelheiten finden Sie in der [Außerkraftsetzungskonfiguration](#override-configuration).
Beim Erstellen einer TeamsFx-Instanz müssen Sie auch den Identitätstyp angeben.
Es gibt zwei Identitätstypen:

* **Benutzeridentität**: Stellt den aktuellen Benutzer von Teams dar.
* **Anwendungsidentität**: Stellt die Anwendung selbst dar.

    > [!NOTE]
    > Bei diesen beiden Identitätstypen sind die TeamsFx-Konstruktoren und -Methoden nicht identisch.

Weitere Informationen zur Benutzeridentität und Anwendungsidentität finden Sie im folgenden Abschnitt:

<details>
<summary><b> Benutzeridentität </b></summary>

| Befehl | Beschreibung |
|----------------|-------------|
| `new TeamsFx(IdentityType.User)`| Die Anwendung wird als aktueller Teams-Benutzer authentifiziert. |
| `TeamsFx:setSsoToken()`| Benutzeridentität in der Node.js-Umgebung (ohne Browser). |
| `TeamsFx:getUserInfo()` | Um Basisinformationen des Benutzers zu erhalten. |
| `TeamsFx:login()` | Wird verwendet, damit Benutzer den Zustimmungsprozess durchführen können, wenn Sie SSO verwenden möchten, um Zugriffstoken für bestimmte OAuth-Bereiche zu erhalten. |

> [!NOTE]
> Sie können im Namen des aktuellen Teams-Benutzers auf Ressourcen zugreifen.
</details>

<details>
<summary><b> Anwendungsidentität </b></summary>

| Befehl | Beschreibung |
|----------------|-------------|
| `new TeamsFx(IdentityType.App)`| Application  is authenticated as an application. The permission usually needs administrator's approval.|
| `TeamsFx:getCredential()`| Es stellt automatisch dem Identitätstyp entsprechende Anmeldeinformationsinstanzen bereit. |

> [!NOTE]
> Sie benötigen die Zustimmung des Administrators für Ressourcen.
</details>

### <a name="credential"></a>Credential

Um TeamsFx zu initialisieren, müssen Sie den erforderlichen Identitätstyp auswählen. Post specifying the identity type SDK uses different type of credential class. Diese stellen die Identität dar und rufen das Zugriffstoken durch den entsprechenden Authentifizierungsfluss ab. Anmeldeinformationsklassen implementieren `TokenCredential` eine Schnittstelle, die allgemein in Azure-Bibliotheks-APIs verwendet wird, die zugriffstoken für bestimmte Bereiche bereitstellen sollen. Andere APIs verlassen sich auf den Aufruf `TeamsFx:getCredential()` von Anmeldeinformationen, um eine Instanz von `TokenCredential` zu erhalten. Weitere Informationen zu klassenbezogenen Klassen für Anmeldeinformationen und den Authentifizierungsfluss finden Sie im [Ordner "Anmeldeinformationen"](https://github.com/OfficeDev/TeamsFx/tree/main/packages/sdk/src/credential).

Es gibt drei Anmeldeinformationsklassen, um die Authentifizierung zu vereinfachen. Hier sind die entsprechenden Szenarien für die Ziele der einzelnen Anmeldeinformationsklassen.

<details>
<summary><b> Benutzeridentität in Browserumgebung </b></summary>

`TeamsUserCredential` stellt die Identität des aktuellen Benutzers von Teams dar. Wenn die Anmeldeinformationen des Benutzers zum ersten Mal authentifiziert werden, führt Teams SSO den Fluss "Im Auftrag von" für den Tokenaustausch durch. SDK verwendet diese Anmeldeinformationen, wenn Sie die Benutzeridentität in der Browserumgebung auswählen.

Die erforderlichen Konfigurationen sind: `initiateLoginEndpoint` und `clientId`.
</details>

<details>
<summary><b> Benutzeridentität in Node.js Umgebung </b></summary>

`OnBehalfOfUserCredential` verwendet den On-Behalf-Of-Fluss und erfordert teams-SSO-Token in Azure-Funktionen oder Bot-Szenarien. TeamsFx SDK verwendet die folgenden Anmeldeinformationen, wenn Sie die Benutzeridentität in Node.js Umgebung auswählen.

Erforderliche Konfiguration:`authorityHost`, `tenantId`, `clientId`, `clientSecret` oder `certificateContent`.
</details>

<details>
<summary><b> App-Identität in Node.js Umgebung </b></summary>

`AppCredential` stellt die App-Identität dar. Sie können die App-Identität verwenden, wenn der Benutzer nicht beteiligt ist, z. B. in einen zeitgesteuerten Automatisierungsauftrag. TeamsFx SDK verwendet die folgenden Anmeldeinformationen, wenn Sie die App-Identität in Node.js Umgebung auswählen.

Erforderliche Konfiguration: `tenantId`, `clientId`, `clientSecret` oder `certificateContent`.
</details>

### <a name="bot-sso"></a>Bot-SSO

Bot-bezogene Klassen werden im [bot-Ordner gespeichert](https://github.com/OfficeDev/TeamsFx/tree/main/packages/sdk/src/bot).

`TeamsBotSsoPrompt` in Bot-Framework integriert. Es vereinfacht den Authentifizierungsprozess, wenn Sie eine Botanwendung entwickeln und den Bot-SSO verwenden möchten.

Erforderliche Konfiguration: `initiateLoginEndpoint`, `tenantId`, `clientId` und `applicationIdUri`.

### <a name="supported-functions"></a>Unterstützte Funktionen

TeamsFx SDK provides several functions to ease the configuration for third-party libraries. They're located under [core folder](https://github.com/OfficeDev/TeamsFx/tree/main/packages/sdk/src/core).

* Microsoft Graph Service:`createMicrosoftGraphClient` und `MsGraphAuthProvider` Hilfe beim Erstellen einer authentifizierten Graph-Instanz.
* SQL:`getTediousConnectionConfig` gibt eine langwierige Verbindungskonfiguration zurück.

    Erforderliche Konfiguration:

  * Wenn Sie die Benutzeridentität verwenden möchten, dann `sqlServerEndpoint`und `sqlUsername` `sqlPassword` sind erforderlich.
  * Wenn Sie msi-Identität verwenden möchten, dann `sqlServerEndpoint`und `sqlIdentityId` sind erforderlich.

### <a name="override-configuration"></a>Konfiguration überschreiben

Sie können beim Erstellen einer neuen `TeamsFx` Instanz eine benutzerdefinierte Konfiguration übergeben, um die Standardkonfiguration zu überschreiben oder erforderliche Felder festzulegen, wenn `environment variables` sie fehlen.

<details>
<summary><b> Für Registerkartenprojekt </b> </summary>

Wenn Sie ein Registerkartenprojekt mit dem Microsoft Visual Studio Code Toolkit erstellt haben, werden die folgenden Konfigurationswerte aus vorkonfigurierten Umgebungsvariablen verwendet:

* authorityHost (REACT_APP_AUTHORITY_HOST)
* tenantId (REACT_APP_TENANT_ID)
* clientId (REACT_APP_CLIENT_ID)
* initiateLoginEndpoint (REACT_APP_START_LOGIN_PAGE_URL)
* applicationIdUri (REACT_APP_START_LOGIN_PAGE_URL)
* apiEndpoint (REACT_APP_FUNC_ENDPOINT) / wird nur verwendet, wenn eine Back-End-Funktion vorhanden ist
* apiName (REACT_APP_FUNC_NAME) / wird nur verwendet, wenn eine Back-End-Funktion vorhanden ist

</details>

<details>
<summary><b> Für Azure-Funktion oder Bot-Projekt </b></summary>

Wenn Sie ein Azure-Funktions- oder Botprojekt mit dem Visual Studio Code Toolkit erstellt haben, werden die folgenden Konfigurationswerte aus vorkonfigurierten Umgebungsvariablen verwendet:

* initiateLoginEndpoint (INITIATE_LOGIN_ENDPOINT)
* authorityHost (M365_AUTHORITY_HOST)
* tenantId (M365_TENANT_ID)
* clientId (M365_CLIENT_ID)
* clientSecret (M365_CLIENT_SECRET)
* applicationIdUri (M365_APPLICATION_ID_URI)
* apiEndpoint (API_ENDPOINT)
* sqlServerEndpoint (SQL_ENDPOINT) / wird nur verwendet, wenn eine SQL-Instanz vorhanden ist
* sqlUsername (SQL_USER_NAME) / wird nur verwendet, wenn eine SQL-Instanz vorhanden ist
* sqlPassword (SQL_PASSWORD) / wird nur verwendet, wenn eine SQL-Instanz vorhanden ist
* sqlDatabaseName (SQL_DATABASE_NAME) / wird nur verwendet, wenn eine SQL-Instanz vorhanden ist
* sqlIdentityId (IDENTITY_ID) / wird nur verwendet, wenn eine SQL-Instanz vorhanden ist.

</details>

### <a name="error-handling"></a>Fehlerbehandlung

Der grundlegende Typ der API-Fehlerantwort ist `ErrorWithCode`, der Fehlercode und Fehlermeldung enthält. Um beispielsweise bestimmte Fehler herauszufiltern, können Sie das folgende Snippet verwenden:

```typescript
try {
  const teamsfx = new TeamsFx();
  await teamsfx.login("User.Read");
} catch (err: unknown) {
  if (err instanceof ErrorWithCode && err.code !== ErrorCode.ConsentFailed) {
    throw err;
  } else {
    // Silently fail because user cancels the consent dialog
    return;
  }
}
```

Wenn die Anmeldeinformationsinstanz in einer anderen Bibliothek wie Microsoft Graph verwendet wird, ist es möglich, dass der Fehler abgefangen und transformiert wird.

## <a name="microsoft-graph-scenarios"></a>Microsoft Graph-Szenarien

Dieser Abschnitt enthält mehrere Codeausschnitte für allgemeine Szenarien im Zusammenhang mit Microsoft Graph. In solchen Szenarien kann der Benutzer APIs mit unterschiedlichen Berechtigungen an verschiedenen Enden (Frontend/Back-End) aufrufen.

* Benutzerdelegatberechtigung im Frontend (Verwenden von TeamsUserCredential) <details>
    <summary><b>Verwenden der Graph-API in der Registerkarten-App</b></summary>

    Dieser Codeausschnitt zeigt Ihnen, wie Sie Benutzerprofile von Microsoft Graph verwenden `TeamsFx` und `createMicrosoftGraphClient` abrufen. Außerdem wird gezeigt, wie Sie ein `GraphError`.

    1. Importieren Sie die erforderlichen Klassen.

    ```typescript
    import {
      createMicrosoftGraphClient,
      TeamsFx,
    } from "@microsoft/teamsfx";
    ```

    2. Hiermit erhalten Sie `TeamsFx.login()` die Zustimmung des Benutzers.

    ```typescript
    // Put these code in a call-to-action callback function to avoid browser blocking automatically showing up pop-ups.
    await teamsfx.login(["User.Read"]); // Login with scope
    ```

    3. Sie können eine TeamsFx-Instanz und einen Graph-Client initialisieren und Informationen von MS Graph von diesem Client abrufen.

    ```typescript
    try {
      const teamsfx = new TeamsFx();
      const graphClient = createMicrosoftGraphClient(teamsfx, ["User.Read"]); // Initializes MS Graph SDK using our MsGraphAuthProvider
      const profile = await graphClient.api("/me").get();
    } catch (err: unknown) {
      // ErrorWithCode is handled by Graph client
      if (err instanceof GraphError && err.code?.includes(ErrorCode.UiRequiredError)) {
        // Need to show login button to ask for user consent.
      }
    }
    ```

    Weitere Informationen zum Beispiel zur Verwendung von Graph-API in der Registerkarten-App finden Sie im Beispiel für die [Registerkarte "hello-world"](https://github.com/OfficeDev/TeamsFx-Samples/tree/dev/hello-world-tab).

    </details>

    <details>
    <summary><b>Integration in das Microsoft Graph-Toolkit</b></summary>

    Die [Mgt-Bibliothek (Microsoft Graph Toolkit)](https://aka.ms/mgt) ist eine Sammlung verschiedener Authentifizierungsanbieter und UI-Komponenten, die von Microsoft Graph unterstützt werden.

    Das `@microsoft/mgt-teamsfx-provider` Paket macht die Klasse verfügbar, die die `TeamsFxProvider` Klasse zum Anmelden von Benutzern und zum Abrufen von Token für die Verwendung mit Graph verwendet `TeamsFx` .

    1. Sie können die folgenden erforderlichen Pakete installieren:

    ```bash
    npm install @microsoft/mgt-element @microsoft/mgt-teamsfx-provider @microsoft/teamsfx
    ```

    2. Initialisieren Sie den Anbieter in Ihrer Komponente.

    ```typescript
     // Import the providers and credential at the top of the page
    import {Providers} from '@microsoft/mgt-element';
    import {TeamsFxProvider} from '@microsoft/mgt-teamsfx-provider';
    import {TeamsUserCredential} from "@microsoft/teamsfx";

    const scope = ["User.Read"];
    const teamsfx = new TeamsFx();
    const provider = new TeamsFxProvider(teamsfx, scope);
    Providers.globalProvider = provider;   
    ```

    3. Sie können die `teamsfx.login(scopes)` Methode verwenden, um das erforderliche Zugriffstoken abzurufen.

    ```typescript
    // Put these code in a call-to-action callback function to avoid browser blocking automatically showing up pop-ups. 
    await teamsfx.login(this.scope);
    Providers.globalProvider.setState(ProviderState.SignedIn);
    ```

    4. Sie können jetzt eine beliebige Komponente auf Ihrer HTML-Seite oder in Ihrer `render()` Methode mit React hinzufügen, um den Kontext für den `TeamsFx` Zugriff auf Microsoft Graph zu verwenden.

    ```html
    <mgt-person query="me" view="threeLines"></mgt-person>
    ```

    ```typescript
    public render(): void {
    return (
        <div>
            <Person personQuery="me" view={PersonViewType.threelines}></Person>
        </div>
    );
    }    
    ```

    Weitere Informationen zum Beispiel zum Initialisieren des TeamsFx-Anbieters finden Sie im Beispiel für den [Kontaktexporteur](https://github.com/OfficeDev/TeamsFx-Samples/tree/dev/graph-toolkit-contact-exporter).

    </details>

* Benutzerdelegatberechtigung im Back-End (Verwenden von OnBehalfOfUserCredential) <details>
    <summary><b>Verwenden von Graph-API in der Bot-Anwendung</b></summary>

    Dieser Codeausschnitt zeigt Ihnen, wie `TeamsBotSsoPrompt` Sie ein Dialogfeld festlegen und sich dann anmelden, um ein Zugriffstoken abzurufen.

    1. Initialisieren und Hinzufügen `TeamsBotSsoPrompt` zum Dialogfeldsatz.

    ```typescript
    const { ConversationState, MemoryStorage } = require("botbuilder");
    const { DialogSet, WaterfallDialog } = require("botbuilder-dialogs");
    const { TeamsBotSsoPrompt } = require("@microsoft/teamsfx");

    const convoState = new ConversationState(new MemoryStorage());
    const dialogState = convoState.createProperty("dialogState");
    const dialogs = new DialogSet(dialogState);

    const teamsfx = new TeamsFx();
    dialogs.add(
      new TeamsBotSsoPrompt(teamsfx, "TeamsBotSsoPrompt", {
        scopes: ["User.Read"],
      })
    );    
    ```

    2. Beginnen Sie das Dialogfeld, und melden Sie sich an.

    ```typescript
    dialogs.add(
      new WaterfallDialog("taskNeedingLogin", [
        async (step) => {
          return await step.beginDialog("TeamsBotSsoPrompt");
        },
        async (step) => {
          const token = step.result;
          if (token) {
            // ... continue with task needing access token ...
          } else {
            await step.context.sendActivity(`Sorry... We couldn't log you in. Try again later.`);
            return await step.endDialog();
          }
        },
      ])
    );    
    ```

    Weitere Informationen zum Beispiel zur Verwendung der Graph-API in der [Bot-Anwendung finden Sie im Beispiel "bot-sso"](https://github.com/OfficeDev/TeamsFx-Samples/tree/dev/bot-sso).

    </details>

    <details>
    <summary><b>Verwenden von Graph-API in der Nachrichtenerweiterung</b></summary>

    Dieser Codeausschnitt zeigt Ihnen, wie Sie Erweiterungen von `TeamsActivityHandler`außer Kraft setzen `handleTeamsMessagingExtensionQuery` und die vom TeamsFx SDK bereitgestellte Verwendung `handleMessageExtensionQueryWithToken` verwenden, um sich anzumelden, um ein Zugriffstoken abzurufen:

    ```typescript
    public async handleTeamsMessagingExtensionQuery(context: TurnContext, query: any): Promise<any> {
      return await handleMessageExtensionQueryWithToken(context, null, 'User.Read', 
        async (token: MessageExtensionTokenResponse) => {
          // ... continue to query with access token ...
        });
    }    
    ```

    Weitere Informationen zum Beispiel zur Verwendung der Graph-API in der Nachrichtenerweiterung finden Sie unter [message-extension-sso-sample](https://aka.ms/teamsfx-me-sso-sample).
    </details>

    <details>
    <summary><b>Verwenden von Graph-API im Befehls-Bot</b></summary>

    Dieser Codeausschnitt zeigt Ihnen, wie Sie den Befehls-Bot zum Aufrufen der Microsoft-API implementieren `TeamsFxBotSsoCommandHandler` .

    ```typescript
    import { Activity, TurnContext } from "botbuilder";
    import {
      CommandMessage,
      TriggerPatterns,
      TeamsFx,
      createMicrosoftGraphClient,
      TeamsFxBotSsoCommandHandler,
      TeamsBotSsoPromptTokenResponse,
    } from "@microsoft/teamsfx";

    export class ProfileSsoCommandHandler implements TeamsFxBotSsoCommandHandler {
      triggerPatterns: TriggerPatterns = "profile";

      async handleCommandReceived(
        context: TurnContext,
        message: CommandMessage,
        tokenResponse: TeamsBotSsoPromptTokenResponse,
      ): Promise<string | Partial<Activity> | void> {
        // Init TeamsFx instance with SSO token
        const teamsfx = new TeamsFx().setSsoToken(tokenResponse.ssoToken);

        // Add scope for your Azure AD app. For example: Mail.Read, etc.
        const graphClient = createMicrosoftGraphClient(teamsfx, ["User.Read"]);
      
        // Call graph api use `graph` instance to get user profile information
        const me = await graphClient.api("/me").get();

        if (me) {
          // Bot will send the user profile info to user
          return `Your command is '${message.text}' and you're logged in as ${me.displayName}`;
        } else {
          return "Could not retrieve profile information from Microsoft Graph.";
        }
      }
    }    
    ```

    Weitere Informationen zur Verwendung dieser Klasse im Befehlsbot finden [Sie unter Hinzufügen von einmaligem Anmelden zur Teams-App](add-single-sign-on.md). Und es gibt auch ein [Command-Bot-with-sso-Beispielprojekt](https://github.com/OfficeDev/TeamsFx-Samples/tree/dev/command-bot-with-sso) , das Sie mit dem SSO-Befehls-Bot testen können.

    </details>

    <details>
    <summary><b>Aufrufen der Azure-Funktion in der Registerkarten-App: Fluss "Im Auftrag von"</b></summary>

    Dieser Codeausschnitt zeigt, wie Sie die Azure-Funktion mithilfe `CreateApiClient` oder `axios` Bibliothek aufrufen und wie Sie Graph-API in der Azure-Funktion aufrufen, um Benutzerprofile abzurufen.

    1. Sie können die vom TeamsFx SDK bereitgestellte Azure-Funktion verwenden `CreateApiClient` :

    ```typescript
    async function callFunction(teamsfx?: TeamsFx) {
      const teamsfx = new TeamsFx();

      // Get the credential.
      const credential = teamsfx.getCredential(); 
      // Create an API client by providing the token and endpoint.
      const apiClient = CreateApiClient(
        teamsfx.getConfig("YOUR_API_ENDPOINT"), // Create an API Client that uses SSO token to authenticate requests
        new BearerTokenAuthProvider(async () =>  (await credential.getToken(""))!.token) // Call API hosted in Azure Functions on behalf of user to inject token to request header
      );

      // Send a GET request to "RELATIVE_API_PATH", "/api/functionName" for example.
      const response = await apiClient.get("RELATIVE_API_PATH");
      return response.data;
    }    
    ```

    Sie können die Bibliothek auch zum Aufrufen der Azure-Funktion verwenden `axios` .

    ```typescript
    async function callFunction(teamsfx?: TeamsFx) {
      const accessToken = await teamsfx.getCredential().getToken(""); // Get SSO token 
      // teamsfx.getConfig("apiEndpoint") will read REACT_APP_FUNC_ENDPOINT environment variable 
      const endpoint = teamsfx.getConfig("apiEndpoint");
      const response = await axios.default.get(endpoint + "/api/" + functionName, {
        headers: {
          authorization: "Bearer " + accessToken.token,
        },
      });
      return response.data;
    }    
    ```

    2. Rufen Sie Graph-API in der Azure-Funktion im Auftrag des Benutzers als Reaktion auf.

    ```typescript
    export default async function run(
      context: Context,
      req: HttpRequest,
      teamsfxContext: TeamsfxContext
    ): Promise<Response> {
      const res: Response = { status: 200, body: {},};
      // ...
      teamsfx = new TeamsFx().setSsoToken(accessToken);
      // Query user's information from the access token.
      try {
        const currentUser: UserInfo = await teamsfx.getUserInfo();
        if (currentUser && currentUser.displayName) {
          res.body.userInfoMessage = `User display name is ${currentUser.displayName}.`;
        } else {
          res.body.userInfoMessage = "No user information was found in access token.";
        }
      } catch (e) {
      }
      // Create a graph client to access user's Microsoft 365 data after user has consented.
      try {
        const graphClient: Client = createMicrosoftGraphClient(teamsfx, [".default"]);
        const profile: any = await graphClient.api("/me").get();
        res.body.graphClientMessage = profile;
      } catch (e) {
      }
      return res;
    }    
    ```

    Weitere Informationen zum Beispiel zur Verwendung der Graph-API in der Bot-Anwendung finden Sie im  [Beispiel "hello-world-tab-with-back"](https://github.com/OfficeDev/TeamsFx-Samples/tree/dev/hello-world-tab-with-backend).

    </details>

* Anwendungsberechtigung im Back-End <details>
    <summary><b>Verwenden Sie die zertifikatbasierte Authentifizierung in Azure Function</b></summary>

    Dieser Codeausschnitt zeigt Ihnen, wie Sie zertifikatbasierte Anwendungsberechtigungen verwenden, um das Token abzurufen, das zum Aufrufen von Graph-API verwendet werden kann.

    1. Sie können die `authConfig` initialisieren, indem Sie eine `PEM-encoded key certificate`.

    ```typescript
    const authConfig = {
      clientId: process.env.M365_CLIENT_ID,
      certificateContent: "The content of a PEM-encoded public/private key certificate",
      authorityHost: process.env.M365_AUTHORITY_HOST,
      tenantId: process.env.M365_TENANT_ID,
    };    
    ```

    2. Sie können das `authConfig` Token verwenden, um das Token abzurufen.

    ```typescript
    const teamsfx = new TeamsFx(IdentityType.App);
    teamsfx.setCustomeConfig(authConfig);
    const token = teamsfx.getCredential().getToken();    
    ```

    </details>

    <details>
    <summary><b>Verwenden der geheimen Clientauthentifizierung in der Azure-Funktion</b></summary>

    Dieser Codeausschnitt zeigt Ihnen, wie Sie die Clientschlüsselanwendungsberechtigung verwenden, um das Token abzurufen, das zum Aufrufen Graph-API verwendet werden kann.

    1. Sie können die `authConfig` initialisieren, indem Sie eine `client secret`.

    ```typescript
    const authConfig = {
      clientId: process.env.M365_CLIENT_ID,
      clientSecret: process.env.M365_CLIENT_SECRET,
      authorityHost: process.env.M365_AUTHORITY_HOST,
      tenantId: process.env.M365_TENANT_ID,
    };    
    ```

    2. Sie können das `authConfig` Token verwenden, um das Token abzurufen.

    ```typescript
    const teamsfx = new TeamsFx(IdentityType.App);
    teamsfx.setCustomeConfig(authConfig);
    const token = teamsfx.getCredential().getToken();    
    ```

    Weitere Informationen zum Beispiel zur Verwendung der Graph-API in der Bot-Anwendung finden Sie im [Beispiel "hello-world-tab-with-back"](https://github.com/OfficeDev/TeamsFx-Samples/tree/dev/hello-world-tab-with-backend).

    </details>

## <a name="other-scenarios"></a>Sonstige Szenarien

Dieser Abschnitt enthält mehrere Codeausschnitte für andere Szenarien im Zusammenhang mit Microsoft Graph. Sie können einen API-Client in der Bot- oder Azure-Funktion erstellen und auf die SQL-Datenbank in Der Azure-Funktion zugreifen.

  <details>
  <summary><b>Erstellen eines API-Clients zum Aufrufen einer vorhandenen API in Bot oder Azure-Funktion</b></summary>

  Dieser Codeausschnitt zeigt, wie Sie eine vorhandene API in Bot nach `ApiKeyProvider`aufrufen.

  ```typescript
  const teamsfx = new TeamsFx();

  // Create an API Key auth provider. In addition to APiKeyProvider, following auth providers are also available:
  // BearerTokenAuthProvider, BasicAuthProvider, CertificateAuthProvider.
  const authProvider = new ApiKeyProvider("YOUR_API_KEY_NAME",
    teamsfx.getConfig("YOUR_API_KEY_VALUE"), // This reads the value of YOUR_API_KEY_VALUE environment variable.
    ApiKeyLocation.Header
  );

  // Create an API client using above auth provider.
  // You can also implement AuthProvider interface and use it here.
  const apiClient = createApiClient(
    teamsfx.getConfig("YOUR_API_ENDPOINT"), // This reads YOUR_API_ENDPOINT environment variable.
    authProvider
  );

  // Send a GET request to "RELATIVE_API_PATH", "/api/apiname" for example.
  const response = await apiClient.get("RELATIVE_API_PATH");  
  ```

  </details>

  <details>
  <summary><b>Greifen Sie in der Azure-Funktion auf die SQL-Datenbank zu</b></summary>

  Verwenden Sie `tedious` die Bibliothek, um auf SQL zuzugreifen und die Authentifizierung zu verwalten `DefaultTediousConnectionConfiguration` . Sie können auch Verbindungskonfigurationen anderer SQL-Bibliotheken basierend auf dem Ergebnis von `sqlConnectionConfig.getConfig()`erstellen.

  1. Legen Sie die Verbindungskonfiguration fest.

  ```typescript
  // Equivalent to:
  // const sqlConnectConfig = new DefaultTediousConnectionConfiguration({
  //    sqlServerEndpoint: process.env.SQL_ENDPOINT,
  //    sqlUsername: process.env.SQL_USER_NAME,
  //    sqlPassword: process.env.SQL_PASSWORD,
  // });
  const teamsfx = new TeamsFx();
  // If there's only one SQL database
  const config = await getTediousConnectionConfig(teamsfx);
  // If there are multiple SQL databases
  const config2 = await getTediousConnectionConfig(teamsfx, "your database name");  
  ```

  2. Stellen Sie eine Verbindung mit Ihrer Datenbank her.

  ```typescript
  const connection = new Connection(config);
  connection.on("connect", (error) => {
    if (error) {
      console.log(error);
    }
  });  
  ```

  > [!NOTE]
  > Weitere Informationen zum Beispiel für den Zugriff auf die [SQL-Datenbank in der Azure-Funktion finden Sie im Beispiel "Jetzt freigeben"](https://github.com/OfficeDev/TeamsFx-Samples/tree/dev/share-now).

</details>

## <a name="advanced-customization"></a>Erweiterte Anpassung

### <a name="configure-log"></a>Protokoll konfigurieren

Sie können die Kundenprotokollebene festlegen und Ausgaben umleiten, wenn Sie diese Bibliothek verwenden.

> [!NOTE]
> Die Protokollierung ist standardmäßig deaktiviert, Sie können sie aktivieren, indem Sie die Protokollebene festlegen.

#### <a name="enable-log-by-setting-log-level"></a>Aktivieren Sie das Protokoll, indem Sie die Protokollebene festlegen

Wenn Sie die Protokollebene festlegen, wird die Protokollierung aktiviert. Protokollinformationen werden standardmäßig in der Konsole gedruckt.

Legen Sie die Protokollebene mit dem folgenden Snippet fest:

```typescript
// Only need the warning and error messages.
setLogLevel(LogLevel.Warn);
```

> [!NOTE]
> Sie können die Protokollausgabe umleiten, indem Sie einen benutzerdefinierten Logger oder eine Protokollfunktion einstellen.

#### <a name="redirect-by-setting-custom-logger"></a>Umleitung durch Einstellen eines benutzerdefinierten Loggers

```typescript
setLogLevel(LogLevel.Info);
// Set another logger if you want to redirect to Application Insights in Azure Function
setLogger(context.log);
```

#### <a name="redirect-by-setting-custom-log-function"></a>Umleitung durch Einstellen der benutzerdefinierten Protokollfunktion

```typescript
setLogLevel(LogLevel.Info);
// Only log error message to Application Insights in bot application.
setLogFunction((level: LogLevel, message: string) => {
  if (level === LogLevel.Error) {
    this.telemetryClient.trackTrace({
      message: message,
      severityLevel: Severity.Error,
    });
  }
});
```

> [!NOTE]
> Protokollfunktionen werden nicht wirksam, wenn Sie eine benutzerdefinierte Protokollierung festlegen.

## <a name="upgrade-latest-sdk-version"></a>Aktualisieren Sie die neueste SDK-Version

Wenn Sie die version des SDK verwenden, die verfügt `loadConfiguration()`, können Sie die folgenden Schritte ausführen, um auf die neueste SDK-Version zu aktualisieren:

1. Benutzerdefinierte `loadConfiguration()` Einstellungen entfernen und übergeben mit `new TeamsFx(IdentityType.User, { ...customConfig })`
2. Ersetzen Sie `new TeamsUserCredential()` durch `new TeamsFx()`.
3. Ersetzen Sie `new M365TenantCredential()` durch `new TeamsFx(IdentityType.App)`.
4. Ersetzen Sie `new OnBehalfOfUserCredential(ssoToken)` durch `new TeamsFx().setSsoToken(ssoToken)`.
5. Übergeben Sie die Instanz von `TeamsFx` an Hilfsfunktionen, um die Anmeldeinformationsinstanz zu ersetzen.

## <a name="next-step"></a>Nächster Schritt

Ausführliche Beispiele zur Verwendung des TeamsFx [SDK-Beispielprojekts](https://github.com/OfficeDev/TeamsFx-Samples) .

## <a name="see-also"></a>Siehe auch

[Microsoft TeamsFx-Beispielkatalog](https://github.com/OfficeDev/TeamsFx-Samples).
