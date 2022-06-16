---
title: TeamsFx SDK
author: MuyangAmigo
description: Informationen zum TeamsFx SDK
ms.author: nintan
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: ed110f95d8f25ba4595d8b96e08c5e49a0c9225e
ms.sourcegitcommit: 5070746e736edb4ae77cd3efcb2ab8bb2e5819a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/16/2022
ms.locfileid: "66123766"
---
# <a name="teamsfx-sdk"></a>TeamsFx SDK

TeamsFx hilft, die Entwickleraufgaben zu reduzieren, indem es Teams SSO nutzt und auf Cloud-Ressourcen bis hin zu einzeiligen Anweisungen ohne Konfiguration zugreift. TeamsFx SDK wurde entwickelt, um in Browser- und Node.js-Umgebungen verwendet zu werden, gängige Szenarien umfassen:

* Anwendung auf der Registerkarte „Teams“.
* Azure Function
* Teams-Bot

Sie können das TeamsFx SDK verwenden, um:

* Greifen Sie auf die Wichtigsten Funktionen in der Client- und Serverumgebung zu.
* Schreiben Sie Benutzerauthentifizierungscode auf vereinfachte Weise.

## <a name="prerequisites"></a>Voraussetzungen

Installieren Sie die folgenden Tools und richten Sie Ihre Entwicklungsumgebung ein:

* Neueste Version von Node.js
* Wenn Ihr Projekt verwandte `botbuilder` Pakete als [Abhängigkeiten](https://github.com/Microsoft/botbuilder-js#packages) installiert hat, stellen Sie sicher, dass sie dieselbe Version haben. Derzeit ist die erforderliche Version 4.15.0 oder höher. Weitere Informationen finden [Sie unter Bot-Builder-Pakete sollten dieselbe Version haben](https://github.com/BotBuilderCommunity/botbuilder-community-js/issues/57#issuecomment-508538548).

Sie müssen über folgende Kenntnisse verfügen:

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

### <a name="create-microsoftgraphclient-service"></a>Dienst `MicrosoftGraphClient` erstellen

Um ein Graph-Client-Objekt zu erstellen und auf die Microsoft Graph-API zuzugreifen, benötigen Sie die Anmeldeinformationen zur Authentifizierung. Das SDK bietet APIs zum Konfigurieren für Entwickler.

<br>

<details>
<summary><b>Aufrufen der Graph-API im Namen des Teams-Benutzers (Benutzeridentität)</b></summary>

Verwenden Sie den folgenden Ausschnitt:

```ts
// Equivalent to:
// const teamsfx = new TeamsFx(IdentityType.User, {
//   initiateLoginEndpoint: process.env.REACT_APP_START_LOGIN_PAGE_URL,
//   clientId: process.env.REACT_APP_CLIENT_ID,
// }
const teamsfx = new TeamsFx();
const graphClient = createMicrosoftGraphClient(teamsfx, ["User.Read"]); // Initializes MS Graph SDK using our MsGraphAuthProvider
const profile = await graphClient.api("/me").get(); // Get the profile of current user
```

</details>

<br>

<details>
<summary><b>Graph-API ohne Benutzer aufrufen (Anwendungsidentität)</b></summary>

Es erfordert keine Interaktion mit dem Team-Benutzer. Sie können Microsoft Graph als Anwendungsidentität aufrufen.

Verwenden Sie den folgenden Ausschnitt:

```ts
// Equivalent to:
// const teamsfx = new TeamsFx(IdentityType.App, {
//   initiateLoginEndpoint: process.env.REACT_APP_START_LOGIN_PAGE_URL,
//   clientId: process.env.REACT_APP_CLIENT_ID,
// });
const teamsfx = new TeamsFx(IdentityType.App);
const graphClient = createMicrosoftGraphClient(teamsfx);
const profile = await graphClient.api("/users/{object_id_of_another_people}").get(); // Get the profile of certain user
```

</details>

<br>

## <a name="core-concepts-and-code-structure"></a>Kernkonzepte und Codestruktur

### <a name="teamsfx-class"></a>TeamsFx-Klasse

TeamsFx-Klasseninstanzen greifen standardmäßig auf alle TeamsFx-Einstellungen aus Umgebungsvariablen zu. Sie können auch benutzerdefinierte Konfigurationswerte festlegen, um die Standardwerte zu überschreiben. Einzelheiten finden Sie in der [Außerkraftsetzungskonfiguration](#override-configuration).
Beim Erstellen einer TeamsFx-Instanz müssen Sie auch den Identitätstyp angeben.
Es gibt zwei Identitätstypen:

* Benutzeridentität
* Anwendungsidentität

#### <a name="user-identity"></a>Benutzeridentität

| Befehl | Beschreibung |
|----------------|-------------|
| `new TeamsFx(IdentityType.User)`| Die Anwendung wird als aktueller Teams-Benutzer authentifiziert. |
| `TeamsFx:setSsoToken()`| Benutzeridentität in der Node.js-Umgebung (ohne Browser). |
| `TeamsFx:getUserInfo()` | Um Basisinformationen des Benutzers zu erhalten. |
| `TeamsFx:login()` | Wird verwendet, damit Benutzer den Zustimmungsprozess durchführen können, wenn Sie SSO verwenden möchten, um Zugriffstoken für bestimmte OAuth-Bereiche zu erhalten. |

> [!NOTE]
> Sie können im Namen des aktuellen Teams-Benutzers auf Ressourcen zugreifen.

#### <a name="application-identity"></a>Anwendungsidentität

| Befehl | Beschreibung |
|----------------|-------------|
| `new TeamsFx(IdentityType.App)`| Die Anwendung wird als Anwendung authentifiziert. Die Berechtigung erfordert normalerweise die Genehmigung des Administrators.|
| `TeamsFx:getCredential()`| Es stellt automatisch dem Identitätstyp entsprechende Anmeldeinformationsinstanzen bereit. |

> [!NOTE]
> Sie benötigen die Zustimmung des Administrators für Ressourcen.

### <a name="credential"></a>Credential

Sie müssen den Identitätstyp auswählen, wenn Sie TeamsFx initialisieren. Nachdem Sie den Identitätstyp bei der Initialisierung von TeamsFx angegeben haben, verwendet das SDK verschiedene Arten von Anmeldeinformationsklassen, um die Identität darzustellen und Zugriffstoken durch den entsprechenden Authentifizierungsablauf zu erhalten.

Es gibt drei Anmeldeinformationsklassen, um die Authentifizierung zu vereinfachen. [credential ordner](https://github.com/OfficeDev/TeamsFx/tree/main/packages/sdk/src/credential). Anmeldeinformationsklassen implementieren `TokenCredential` eine Schnittstelle, die in Azure-Bibliotheks-APIs weit verbreitet ist und darauf ausgelegt ist, Zugriffstoken für bestimmte Bereiche bereitzustellen. Andere APIs verlassen sich auf den Aufruf `TeamsFx:getCredential()` von Anmeldeinformationen, um eine Instanz von `TokenCredential` zu erhalten.

Hier sind die entsprechenden Szenarien für die Ziele der einzelnen Anmeldeinformationsklassen.

#### <a name="user-identity-in-browser-environment"></a>Benutzeridentität in der Browserumgebung

`TeamsUserCredential` stellt die Identität des aktuellen Benutzers von Teams dar. Bei Verwendung dieser Anmeldeinformationen wird beim ersten Mal die Zustimmung des Benutzers angefordert. Es nutzt den SSO- und On-Behalf-Of-Flow von Teams, um Token auszutauschen. Das SDK verwendet diese Anmeldeinformationen, wenn der Entwickler die Benutzeridentität in der Browserumgebung auswählt.

Erforderliche Konfiguration: `initiateLoginEndpoint`, `clientId`.

#### <a name="user-identity-in-nodejs-environment"></a>Benutzeridentität in der Node.js-Umgebung

`OnBehalfOfUserCredential` verwendet den On-Behalf-Of-Flow und benötigt Teams-SSO-Token. Es ist für die Verwendung in Azure Function- oder Bot-Szenarien konzipiert. Das SDK verwendet diese Anmeldeinformationen, wenn der Entwickler die Benutzeridentität in der Node.js-Umgebung auswählt.

Erforderliche Konfiguration:`authorityHost`, `tenantId`, `clientId`, `clientSecret` oder `certificateContent`.

#### <a name="application-identity-in-nodejs-environment"></a>Anwendungsidentität in der Node.js-Umgebung

`AppCredential` stellt die Anwendungsidentität dar. Wird verwendet, wenn der Benutzer nicht beteiligt ist, wie z. B. ein zeitgesteuerter Automatisierungsjob. Das SDK verwendet diese Anmeldeinformationen, wenn der Entwickler die App-Identität in der Node.js-Umgebung auswählt.

Erforderliche Konfiguration: `tenantId`, `clientId`, `clientSecret` oder `certificateContent`.

### <a name="bot-sso"></a>Bot-SSO

Bot-bezogene Klassen werden im [bot-Ordner gespeichert](https://github.com/OfficeDev/TeamsFx/tree/main/packages/sdk/src/bot).

`TeamsBotSsoPrompt` weist eine gute Integration mit dem Bot-Framework auf. Es vereinfacht den Authentifizierungsprozess, wenn Sie Bot-Anwendungen entwickeln und Bot-SSO nutzen möchten.

Erforderliche Konfiguration: `initiateLoginEndpoint`, `tenantId`, `clientId` und `applicationIdUri`.

### <a name="supported-functions"></a>Unterstützte Funktionen

TeamsFx SDK bietet mehrere Funktionen, um die Konfiguration für Bibliotheken von Drittanbietern zu vereinfachen. Sie befinden sich unter dem [Hauptordner](https://github.com/OfficeDev/TeamsFx/tree/main/packages/sdk/src/core).

* Microsoft Graph Service:`createMicrosoftGraphClient` und `MsGraphAuthProvider` Hilfe beim Erstellen einer authentifizierten Graph-Instanz.
* SQL:`getTediousConnectionConfig` gibt eine langwierige Verbindungskonfiguration zurück.

Erforderliche Konfiguration:

* `sqlServerEndpoint`, `sqlUsername`, `sqlPassword` wenn Sie die Benutzeridentität verwenden möchten
* `sqlServerEndpoint`, `sqlIdentityId` wenn Sie die MSI-Identität verwenden möchten

### <a name="error-handling"></a>Fehlerbehandlung

Die API-Fehlerantwort ist `ErrorWithCode`, die den Fehlercode und die Fehlermeldung enthält. Um beispielsweise bestimmte Fehler herauszufiltern, können Sie das folgende Snippet verwenden:

```ts
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

```ts
try {
  const teamsfx = new TeamsFx();
  const graphClient = createMicrosoftGraphClient(teamsfx, ["User.Read"]); // Initializes MS Graph SDK using our MsGraphAuthProvider
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

Der folgende Abschnitt enthält mehrere Codeausschnitte für gängige Szenarien:

<br>

<details>
<summary><b>Verwenden Sie die Graph-API in der Tab-App</b></summary>

Verwenden `TeamsFx` und `createMicrosoftGraphClient`.

```ts
const teamsfx = new TeamsFx();
const graphClient = createMicrosoftGraphClient(teamsfx, ["User.Read"]);
const profile = await graphClient.api("/me").get();
```

</details>

<br>

<details>
<summary><b>Erstellen eines API-Clients zum Aufrufen einer vorhandenen API in Bot oder Azure-Funktion</b></summary>

:::image type="content" source="~/assets/images/teams-toolkit-v2/teams toolkit fundamentals/createapi-client.PNG" alt-text="API-Client erstellen" border="false":::

</details>

<br>

<details>
<summary><b>Rufen Sie die Azure-Funktion in der Registerkarten-App auf</b></summary>

Verwenden Sie `axios` die Bibliothek, um eine HTTP-Anforderung an die Azure-Funktion zu senden.

```ts
const teamsfx = new TeamsFx();
const credential = teamsfx.getCredential(); //Create an API Client that uses SSO token to authenticate requests
const apiClient = CreateApiClient(teamsfx.getConfig("apiEndpoint")),
new BearerTokenAuthProvider(async () =>  (await credential.getToken(""))!.token);// Call API hosted in Azure Functions on behalf of user
const response = await apiClient.get("/api/" + functionName);
```

</details>

<br>

<details>
<summary><b>Greifen Sie in der Azure-Funktion auf die SQL-Datenbank zu</b></summary>

Verwenden Sie die `tedious` Bibliothek, um auf SQL zuzugreifen `DefaultTediousConnectionConfiguration` und die Authentifizierung zu nutzen.
Abgesehen davon können `tedious`Sie auch Verbindungskonfigurationen anderer SQL-Bibliotheken basierend auf dem Ergebnis von erstellen `sqlConnectionConfig.getConfig()`.

```ts
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
const config2 = await getTediousConnectionConfig(teamsfx "your database name");
const connection = new Connection(config);
connection.on("connect", (error) => {
  if (error) {
    console.log(error);
  }
});
```

</details>

<br>

<details>
<summary><b>Verwenden Sie die zertifikatbasierte Authentifizierung in Azure Function</b></summary>

```ts
const authConfig = {
  clientId: process.env.M365_CLIENT_ID,
  certificateContent: "The content of a PEM-encoded public/private key certificate",
  authorityHost: process.env.M365_AUTHORITY_HOST,
  tenantId: process.env.M365_TENANT_ID,
};
const teamsfx = new TeamsFx(IdentityType.App);
teamsfx.setCustomeConfig({
  certificateContent: "The content of a PEM-encoded public/private key certificate"
});
const token = teamsfx.getCredential().getToken();
```

</details>

<br>

<details>
<summary><b>Verwenden Sie die Graph-API in der Bot-Anwendung</b></summary>

Zum `TeamsBotSsoPrompt` Dialogset hinzufügen.

```ts
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

</details>

<br>

## <a name="advanced-customization"></a>Erweiterte Anpassung

### <a name="configure-log"></a>Protokoll konfigurieren

Sie können die Kundenprotokollebene festlegen und Ausgaben umleiten, wenn Sie diese Bibliothek verwenden. Die Protokollierung ist standardmäßig deaktiviert, Sie können sie aktivieren, indem Sie die Protokollebene festlegen.

#### <a name="enable-log-by-setting-log-level"></a>Aktivieren Sie das Protokoll, indem Sie die Protokollebene festlegen

Die Protokollierung wird nur aktiviert, wenn Sie die Protokollebene festlegen. Standardmäßig werden Protokollinformationen auf der Konsole ausgegeben.

Legen Sie die Protokollebene mit dem folgenden Snippet fest:

```ts
// Only need the warning and error messages.
setLogLevel(LogLevel.Warn);
```

Sie können die Protokollausgabe umleiten, indem Sie einen benutzerdefinierten Logger oder eine Protokollfunktion einstellen.

#### <a name="redirect-by-setting-custom-logger"></a>Umleitung durch Einstellen eines benutzerdefinierten Loggers

```ts
setLogLevel(LogLevel.Info);
// Set another logger if you want to redirect to Application Insights in Azure Function
setLogger(context.log);
```

#### <a name="redirect-by-setting-custom-log-function"></a>Umleitung durch Einstellen der benutzerdefinierten Protokollfunktion

> [!NOTE]
> Die Log-Funktion wird nicht wirksam, wenn Sie einen benutzerdefinierten Logger einstellen.

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

## <a name="override-configuration"></a>Konfiguration überschreiben

Sie können beim Erstellen einer TeamsFx-Instanz eine benutzerdefinierte Konfiguration übergeben, um die Standardkonfiguration zu überschreiben oder erforderliche Felder festzulegen, wenn Umgebungsvariablen fehlen.

* Wenn Sie ein Registerkartenprojekt mit VS Code Toolkit erstellt haben, werden die folgenden Konfigurationswerte aus vorkonfigurierten Umgebungsvariablen verwendet:
  * authorityHost (REACT_APP_AUTHORITY_HOST)
  * tenantId (REACT_APP_TENANT_ID)
  * clientId (REACT_APP_CLIENT_ID)
  * initiateLoginEndpoint (REACT_APP_START_LOGIN_PAGE_URL)
  * applicationIdUri (REACT_APP_START_LOGIN_PAGE_URL)
  * apiEndpoint (REACT_APP_FUNC_ENDPOINT)
  * apiName (REACT_APP_FUNC_NAME)

* Wenn Sie ein Azure-Funktions-/Bot-Projekt mit VS Code Toolkit erstellt haben, werden die folgenden Konfigurationswerte aus vorkonfigurierten Umgebungsvariablen verwendet:
  * initiateLoginEndpoint (INITIATE_LOGIN_ENDPOINT)
  * authorityHost (M365_AUTHORITY_HOST)
  * tenantId (M365_TENANT_ID)
  * clientId (M365_CLIENT_ID)
  * clientSecret (M365_CLIENT_SECRET)
  * applicationIdUri (M365_APPLICATION_ID_URI)
  * apiEndpoint (API_ENDPOINT)
  * sqlServerEndpoint (SQL_ENDPOINT)
  * sqlUsername (SQL_USER_NAME)
  * sqlPassword (SQL_PASSWORD)
  * sqlDatabaseName (SQL_DATABASE_NAME)
  * sqlIdentityId (IDENTITY_ID)

## <a name="upgrade-latest-sdk-version"></a>Aktualisieren Sie die neueste SDK-Version

Wenn Sie die SDK-Version mit `loadConfiguration()` verwenden, können Sie diese Schritte ausführen, um auf die neueste SDK-Version zu aktualisieren.

1. Benutzerdefinierte `loadConfiguration()` Einstellungen entfernen und übergeben mit `new TeamsFx(IdentityType.User, { ...customConfig })`
2. Ersetzen `new TeamsUserCredential()` mit `new TeamsFx()`
3. Ersetzen `new M365TenantCredential()` mit `new TeamsFx(IdentityType.App)`
4. Ersetzen `new OnBehalfOfUserCredential(ssoToken)` mit `new TeamsFx().setSsoToken(ssoToken)`
5. Übergeben Sie die Instanz von `TeamsFx` an Hilfsfunktionen, um die Anmeldeinformationsinstanz zu ersetzen

Weitere Informationen finden Sie unter [TeamsFx-Klasse](#teamsfx-class).

## <a name="next-step"></a>Nächster Schritt

[Beispielprojekt](https://github.com/OfficeDev/TeamsFx-Samples) für detaillierte Beispiele zur Verwendung des TeamsFx SDK.

## <a name="see-also"></a>Siehe auch

[Microsoft TeamsFx-Beispielkatalog](https://github.com/OfficeDev/TeamsFx-Samples).
