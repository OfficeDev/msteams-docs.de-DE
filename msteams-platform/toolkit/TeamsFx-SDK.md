---
title: TeamsFx SDK
author: MuyangAmigo
description: Informationen zum TeamsFx SDK
ms.author: nintan
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 63c5fad9c795c513b476f305c09d94ffad7c5d61
ms.sourcegitcommit: f1e6f90fb6f7f5825e55a6d18ccf004d0091fb6d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2021
ms.locfileid: "61228075"
---
# <a name="teamsfx-sdk-for-typescript-or-javascript"></a>TeamsFx SDK für TypeScript oder JavaScript

TeamsFx zielt darauf ab, Die Aufgaben der Implementierung von Identität und Zugriff auf Cloudressourcen bis hin zu einzeiligen Anweisungen mit der "Nullkonfiguration" zu reduzieren.

Verwenden Sie die Bibliothek für Folgendes:

- Greifen Sie auf ähnliche Weise auf Kernfunktionen in der Client- und Serverumgebung zu.
- Schreiben von Benutzerauthentifizierungscode auf vereinfachte Weise.

   * [Quellcode](https://github.com/OfficeDev/TeamsFx/tree/main/packages/sdk) 
   * [Paket (NPM)](https://www.npmjs.com/package/@microsoft/teamsfx) 
   * [API-Referenzdokumentation](https://aka.ms/teamsfx-sdk-help) 
   * [Beispiele](https://github.com/OfficeDev/TeamsFx-Samples)

## <a name="get-started"></a>Erste Schritte

TeamsFx SDK ist im Gerüstprojekt mithilfe des TeamsFx-Toolkits oder der CLI vorkonfiguriert.
Weitere Informationen zu Teams App-Projekt finden Sie unter [README](https://github.com/OfficeDev/TeamsFx/blob/main/packages/vscode-extension/README.md).

### <a name="prerequisites"></a>Voraussetzungen

- Node.js `10.x.x` Oder höher.
- Wenn Ihr Projekt `botbuilder` verwandte [Pakete](https://github.com/Microsoft/botbuilder-js#packages) als Abhängigkeiten installiert hat, stellen Sie sicher, dass sie die gleiche Version und die gleiche Version `>= 4.9.3` aufweisen. ([Problem – alle BOTBUILDER-Pakete sollten dieselbe Version sein)](https://github.com/BotBuilderCommunity/botbuilder-community-js/issues/57#issuecomment-508538548)

> [!TIP]
> Ein Projekt, das vom TeamsFx-Toolkit VS Code Erweiterung oder CLI-Tool erstellt wurde.

### <a name="install-the-microsoftteamsfx-package"></a>Installieren des `@microsoft/teamsfx` Pakets

Installieren Sie das TeamsFx SDK für TypeScript oder JavaScript `npm` mit:

```bash
npm install @microsoft/teamsfx
```

### <a name="create-and-authenticate-a-microsoftgraphclient"></a>Erstellen und Authentifizieren eines `MicrosoftGraphClient`

Um ein Graph-Clientobjekt für den Zugriff auf die Microsoft Graph-API zu erstellen, benötigen Sie die Anmeldeinformationen für die Authentifizierung. Das SDK bietet mehrere Anmeldeinformationsklassen zur Auswahl, die verschiedene Anforderungen erfüllen. Sie müssen die Konfiguration laden, bevor Sie Anmeldeinformationen verwenden.

- In der Browserumgebung müssen Sie die Konfigurationsparameter explizit übergeben. Das Gerüst React Projekts hat zu verwendende Umgebungsvariablen bereitgestellt.

```ts
loadConfiguration({
  authentication: {
    initiateLoginEndpoint: process.env.REACT_APP_START_LOGIN_PAGE_URL,
    simpleAuthEndpoint: process.env.REACT_APP_TEAMSFX_ENDPOINT,
    clientId: process.env.REACT_APP_CLIENT_ID,
  },
});
```

- In nodeJS-Umgebungen wie Azure Function können Sie einfach `loadConfiguration` aufrufen. Es wird standardmäßig aus Umgebungsvariablen geladen.

```ts
loadConfiguration();
```

#### <a name="using-teams-app-user-credential"></a>Verwenden Teams App-Benutzeranmeldeinformationen

Verwenden Sie den folgenden Codeausschnitt:

> [Hinweis] Sie können diese Anmeldeinformationsklasse nur in Browseranwendungen wie Teams Tab-App verwenden.

```ts
loadConfiguration({
  authentication: {
    initiateLoginEndpoint: process.env.REACT_APP_START_LOGIN_PAGE_URL,
    simpleAuthEndpoint: process.env.REACT_APP_TEAMSFX_ENDPOINT,
    clientId: process.env.REACT_APP_CLIENT_ID,
  },
});
const credential = new TeamsUserCredential();
const graphClient = createMicrosoftGraphClient(credential, ["User.Read"]); // Initializes MS Graph SDK using our MsGraphAuthProvider
const profile = await graphClient.api("/me").get();
```

#### <a name="using-microsoft-365-tenant-credential"></a>Verwenden Microsoft 365 Mandantenanmeldeinformationen

Es ist keine Interaktion mit Teams App-Benutzer erforderlich. Sie können Microsoft Graph als Anwendung aufrufen.
Verwenden Sie den folgenden Codeausschnitt:

```ts
loadConfiguration();
const credential = new M365TenantCredential();
const graphClient = createMicrosoftGraphClient(credential);
const profile = await graphClient.api("/users/{object_id_of_another_people}").get();
```

## <a name="core-concepts-and-code-structure"></a>Kernkonzepte und Codestruktur

### <a name="credentials"></a>Anmeldeinformationen

Es gibt drei Anmeldeinformationsklassen, die sich unter dem [Anmeldeinformationsordner](https://github.com/OfficeDev/TeamsFx/tree/main/packages/sdk/src/credential) befinden, um die Authentifizierung zu vereinfachen. 

Anmeldeinformationsklassen implementieren `TokenCredential` eine Schnittstelle, die in Azure-Bibliotheks-APIs allgemein verwendet wird. Sie sind so konzipiert, dass sie Zugriffstoken für bestimmte Bereiche bereitstellen.
Die Anmeldeinformationsklassen stellen unter bestimmten Szenarien unterschiedliche Identitäten dar.

`TeamsUserCredential`Teams Identität des aktuellen Benutzers darstellen. Wenn Sie diese Anmeldeinformationen verwenden, wird die Zustimmung des Benutzers zum ersten Mal angefordert.
`M365TenantCredential`Microsoft 365 Mandantenidentität darstellen. Es wird in der Regel verwendet, wenn der Benutzer nicht beteiligt ist, z. B. bei einem zeitgesteuerten Automatisierungsauftrag.
`OnBehalfOfUserCredential` verwendet den Im-Auftrag-von-Fluss. Es benötigt ein Zugriffstoken, und Sie können ein neues Token für einen anderen Bereich abrufen. Es wurde für die Verwendung in Azure Function- oder Bot-Szenarien entwickelt.

### <a name="bots"></a>Bots

Bot-bezogene Klassen werden im [Bot-Ordner](https://github.com/OfficeDev/TeamsFx/tree/main/packages/sdk/src/bot) gespeichert.

`TeamsBotSsoPrompt` bietet eine gute Integration in das Bot-Framework. Es vereinfacht den Authentifizierungsprozess beim Entwickeln einer Bot-Anwendung.

### <a name="helper-functions"></a>Hilfsfunktionen

Das TeamsFx SDK bietet Hilfsfunktionen, um die Konfiguration für Drittanbieterbibliotheken zu vereinfachen. Sie befinden sich unter dem [Hauptordner.](https://github.com/OfficeDev/TeamsFx/tree/main/packages/sdk/src/core)

### <a name="error-handling"></a>Fehlerbehandlung

Die API wird `ErrorWithCode` ausgelöst, wenn ein Fehler auftritt. Jede `ErrorWithCode` enthält Fehlercode und Fehlermeldung.

Um beispielsweise einen bestimmten Fehler herauszufiltern, können Sie die folgende Überprüfung verwenden:

```ts
try {
  const credential = new TeamsUserCredential();
  await credential.login("User.Read");
} catch (err: unknown) {
  if (err instanceof ErrorWithCode && err.code !== ErrorCode.ConsentFailed) {
    throw err;
  } else {
    // Silently fail because user cancels the consent dialog
    return;
  }
}
```

Und wenn die Anmeldeinformationsinstanz in einer anderen Bibliothek wie Microsoft Graph verwendet wird, ist es möglich, dass der Fehler abgefangen und transformiert wird.

```ts
try {
  const credential = new TeamsUserCredential();
  const graphClient = createMicrosoftGraphClient(credential, ["User.Read"]); // Initializes MS Graph SDK using our MsGraphAuthProvider
  const profile = await graphClient.api("/me").get();
} catch (err: unknown) {
  // ErrorWithCode is handled by Graph client
  if (err instanceof GraphError && err.code?.includes(ErrorCode.UiRequiredError)) {
    this.setState({
      showLoginBtn: true,
    });
  }
}
```

## <a name="scenarios"></a>Szenarien

Die folgenden Abschnitte enthalten mehrere Codeausschnitte, die einige der gängigsten Szenarien abdecken:

- [Verwenden Graph-API in der Registerkarten-App](#use-graph-api-in-tab-app)
- [Aufrufen der Azure-Funktion in der Registerkarten-App](#call-azure-function-in-tab-app)
- [Zugreifen auf SQL-Datenbank in Azure Function](#access-sql-database-in-azure-function)
- [Verwenden der zertifikatbasierten Authentifizierung in Azure Function](#use-certificate-based-authentication-in-azure-function)
- [Verwenden der Graph-API in der Bot-Anwendung](#use-graph-api-in-bot-application)

### <a name="use-graph-api-in-tab-app"></a>Verwenden Graph-API in der Registerkarten-App

Use `TeamsUserCredential` and `createMicrosoftGraphClient` .

```ts
loadConfiguration({
  authentication: {
    initiateLoginEndpoint: process.env.REACT_APP_START_LOGIN_PAGE_URL,
    simpleAuthEndpoint: process.env.REACT_APP_TEAMSFX_ENDPOINT,
    clientId: process.env.REACT_APP_CLIENT_ID,
  },
});
const credential: any = new TeamsUserCredential();
const graphClient = createMicrosoftGraphClient(credential, ["User.Read"]);
const profile = await graphClient.api("/me").get();
```

### <a name="call-azure-function-in-tab-app"></a>Aufrufen der Azure-Funktion in der Registerkarten-App

Verwenden Sie `axios` die Bibliothek, um eine HTTP-Anforderung an Azure Function zu senden.

```ts
loadConfiguration({
  authentication: {
    initiateLoginEndpoint: process.env.REACT_APP_START_LOGIN_PAGE_URL,
    simpleAuthEndpoint: process.env.REACT_APP_TEAMSFX_ENDPOINT,
    clientId: process.env.REACT_APP_CLIENT_ID,
  },
});
const credential: any = new TeamsUserCredential();
const token = credential.getToken(""); // Get SSO token for the user
// Call API hosted in Azure Functions on behalf of user
const apiConfig = getResourceConfiguration(ResourceType.API);
const response = await axios.default.get(apiConfig.endpoint + "api/httptrigger1", {
  headers: {
    authorization: "Bearer " + token,
  },
});
```

### <a name="access-sql-database-in-azure-function"></a>Zugreifen auf SQL Datenbank in Azure Function

Verwenden Sie `tedious` die Bibliothek, um auf SQL zuzugreifen und `DefaultTediousConnectionConfiguration` die Authentifizierung zu verwalten.
Abgesehen davon `tedious` können Sie auch Verbindungskonfigurationen anderer SQL Bibliotheken basierend auf dem Ergebnis von `sqlConnectionConfig.getConfig()` erstellen.

```ts
loadConfiguration();
const sqlConnectConfig = new DefaultTediousConnectionConfiguration();
const config = await sqlConnectConfig.getConfig();
const connection = new Connection(config);
connection.on("connect", (error) => {
  if (error) {
    console.log(error);
  }
});
```

### <a name="use-certificate-based-authentication-in-azure-function"></a>Verwenden der zertifikatbasierten Authentifizierung in Azure Function

```ts
loadConfiguration({
  authentication: {
    clientId: process.env.M365_CLIENT_ID,
    certificateContent: "The content of a PEM-encoded public/private key certificate",
    authorityHost: process.env.M365_AUTHORITY_HOST,
    tenantId: process.env.M365_TENANT_ID,
  },
});
```

### <a name="use-graph-api-in-bot-application"></a>Verwenden Graph-API in der Bot-Anwendung

Zum `TeamsBotSsoPrompt` Dialogfeldsatz hinzufügen.

```ts
const { ConversationState, MemoryStorage } = require("botbuilder");
const { DialogSet, WaterfallDialog } = require("botbuilder-dialogs");
const { TeamsBotSsoPrompt } = require("@microsoft/teamsfx");

const convoState = new ConversationState(new MemoryStorage());
const dialogState = convoState.createProperty("dialogState");
const dialogs = new DialogSet(dialogState);

loadConfiguration();
dialogs.add(
  new TeamsBotSsoPrompt("TeamsBotSsoPrompt", {
    scopes: ["User.Read"],
  })
);

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

## <a name="troubleshooting"></a>Problembehandlung

### <a name="configure-log"></a>Konfigurieren des Protokolls

Sie können die Protokollebene des Kunden festlegen und Ausgaben umleiten, wenn Sie diese Bibliothek verwenden.
Die Protokollierung ist standardmäßig deaktiviert, Sie können sie aktivieren, indem Sie die Protokollebene festlegen.

#### <a name="enable-log-by-setting-log-level"></a>Aktivieren des Protokolls durch Festlegen der Protokollebene

Wenn die Protokollebene festgelegt ist, ist die Protokollierung aktiviert. Protokollinformationen werden standardmäßig in der Konsole gedruckt.

Legen Sie die Protokollebene mithilfe des folgenden Codeausschnitts fest:

```ts
// Only need the warning and error messages.
setLogLevel(LogLevel.Warn);
```

Sie können die Protokollausgabe umleiten, indem Sie die benutzerdefinierte Protokollierungs- oder Protokollfunktion festlegen.

##### <a name="redirect-by-setting-custom-logger"></a>Umleiten durch Festlegen der benutzerdefinierten Protokollierung

```ts
setLogLevel(LogLevel.Info);
// Set another logger if you want to redirect to Application Insights in Azure Function
setLogger(context.log);
```

##### <a name="redirect-by-setting-custom-log-function"></a>Umleiten durch Festlegen der benutzerdefinierten Protokollfunktion

Beachten Sie, dass die Protokollfunktion nicht wirksam wird, wenn Sie eine benutzerdefinierte Protokollierung festlegen.

```ts
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

## <a name="see-also"></a>Siehe auch

[Microsoft TeamsFx-Beispielkatalog](https://github.com/OfficeDev/TeamsFx-Samples)