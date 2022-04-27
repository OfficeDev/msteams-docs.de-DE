---
title: TeamsFx SDK
author: MuyangAmigo
description: Informationen zum TeamsFx SDK
ms.author: nintan
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: ade31e39d48b92cca4309b16762dc95afccf1925
ms.sourcegitcommit: 3bfd0d2c4d83f306023adb45c8a3f829f7150b1d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2022
ms.locfileid: "65073097"
---
# <a name="teamsfx-sdk"></a>TeamsFx SDK

TeamsFx trägt dazu bei, die Entwickleraufgaben zu reduzieren, indem es Teams SSO nutzt und auf Cloudressourcen bis hin zu Einzelzeilenanweisungen mit Nullkonfiguration zugreift. TeamsFx SDK ist für die Verwendung in Browser- und Node.js-Umgebung entwickelt. Häufige Szenarien sind:

* Teams-Registerkartenanwendung
* Azure-Funktion
* Teams Bot

Sie können das TeamsFx SDK für Folgendes verwenden:

* Zugreifen auf die Kernfunktionen in der Client- und Serverumgebung 
* Vereinfachtes Schreiben von Benutzerauthentifizierungscode

## <a name="prerequisites"></a>Voraussetzungen

Installieren Sie die folgenden Tools, und richten Sie Ihre Entwicklungsumgebung ein:

* Neueste Version von Node.js
* Wenn ihr Projekt verwandte [Pakete](https://github.com/Microsoft/botbuilder-js#packages) als Abhängigkeiten installiert `botbuilder` hat, stellen Sie sicher, dass sie die gleiche Version aufweisen. Derzeit ist die erforderliche Version 4.15.0 oder höher. Weitere Informationen finden Sie unter [Bot Builder-Pakete sollten die gleiche Version haben](https://github.com/BotBuilderCommunity/botbuilder-community-js/issues/57#issuecomment-508538548).

Sie müssen über Arbeitskenntnisse in folgenden Themen verfügen:

* [Quellcode](https://github.com/OfficeDev/TeamsFx/tree/main/packages/sdk)
* [Paket (NPM)](https://www.npmjs.com/package/@microsoft/teamsfx)
* [API-Referenzdokumentation](https://aka.ms/teamsfx-sdk-help)
* [Beispiele](https://github.com/OfficeDev/TeamsFx-Samples)

## <a name="get-started"></a>Erste Schritte

Das TeamsFx SDK ist im Gerüstprojekt mithilfe des TeamsFx Toolkits oder der CLI vorkonfiguriert.
Weitere Informationen finden Sie [unter Teams App-Projekt](https://github.com/OfficeDev/TeamsFx/blob/main/packages/vscode-extension/README.md).

### <a name="install-the-microsoftteamsfx-package"></a>Installieren des Pakets `@microsoft/teamsfx`

Installieren Sie das TeamsFx SDK für TypeScript oder JavaScript mit `npm`:

```bash
npm install @microsoft/teamsfx
```

### <a name="create-microsoftgraphclient-service"></a>Dienst erstellen `MicrosoftGraphClient`

Um ein Graph-Clientobjekt zu erstellen und auf die Microsoft Graph-API zuzugreifen, benötigen Sie die Anmeldeinformationen, um sich zu authentifizieren. Das SDK stellt APIs bereit, die für Entwickler konfiguriert werden können.

<br>

<details>
<summary><b>Aufrufen Graph-API im Namen Teams Benutzers (Benutzeridentität)</b></summary>

Verwenden Sie den folgenden Codeausschnitt:

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
<summary><b>Aufrufen Graph-API ohne Benutzer (Anwendungsidentität)</b></summary>

Es ist keine Interaktion mit Teams Benutzer erforderlich. Sie können Microsoft Graph als Anwendungsidentität aufrufen.

Verwenden Sie den folgenden Codeausschnitt:

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

Die TeamsFx-Klasseninstanz greift standardmäßig über Umgebungsvariablen auf alle TeamsFx-Einstellungen zu. Sie können auch angepasste Konfigurationswerte festlegen, um die Standardwerte außer Kraft zu setzen. Überprüfen Sie die [Außerkraftsetzungskonfiguration](#override-configuration) auf Details. Beim Erstellen einer TeamsFx-Instanz müssen Sie auch den Identitätstyp angeben. Es gibt zwei Identitätstypen:

* Benutzeridentität
* Anwendungsidentität

#### <a name="user-identity"></a>Benutzeridentität

| Befehl | Beschreibung |
|----------------|-------------|
| `new TeamsFx(IdentityType.User)`| Die Anwendung wird als aktueller Teams Benutzer authentifiziert. |
| `TeamsFx:setSsoToken()`| Benutzeridentität in Node.js Umgebung (ohne Browser). |
| `TeamsFx:getUserInfo()` | So rufen Sie die Basisinformationen des Benutzers ab. |
| `TeamsFx:login()` | Es wird verwendet, um dem Benutzer die Durchführung des Zustimmungsprozesses zu ermöglichen, wenn Sie SSO verwenden möchten, um Zugriffstoken für bestimmte OAuth-Bereiche abzurufen. |

> [!NOTE]
> Sie können im Namen des aktuellen Teams Benutzers auf Ressourcen zugreifen.

#### <a name="application-identity"></a>Anwendungsidentität

| Befehl | Beschreibung |
|----------------|-------------|
| `new TeamsFx(IdentityType.App)`| Die Anwendung wird als Anwendung authentifiziert. Für die Berechtigung ist in der Regel die Genehmigung durch den Administrator erforderlich.|
| `TeamsFx:getCredential()`| Es stellt Anmeldeinformationsinstanzen bereit, die automatisch dem Identitätstyp entsprechen. |

> [!NOTE]
> Sie benötigen die Administratorzustimmung für Ressourcen.

### <a name="credential"></a>Anmeldeinformationen

Sie müssen beim Initialisieren von TeamsFx den Identitätstyp auswählen. Nachdem Sie den Identitätstyp beim Initialisieren von TeamsFx angegeben haben, verwendet SDK verschiedene Arten von Anmeldeinformationsklassen, um die Identität darzustellen und das Zugriffstoken durch den entsprechenden Authentifizierungsfluss abzurufen.

Es gibt drei Anmeldeinformationsklassen, um die Authentifizierung zu vereinfachen. [Anmeldeinformationsordner](https://github.com/OfficeDev/TeamsFx/tree/main/packages/sdk/src/credential). Anmeldeinformationsklassen implementieren `TokenCredential` eine Schnittstelle, die in Azure-Bibliotheks-APIs allgemein verwendet wird und Zugriffstoken für bestimmte Bereiche bereitstellt. Andere APIs verwenden Anmeldeinformationsaufrufe `TeamsFx:getCredential()` , um eine Instanz von `TokenCredential`abzurufen.

Hier sind die entsprechenden Szenarien für die einzelnen Ziele der Anmeldeinformationsklasse.

#### <a name="user-identity-in-browser-environment"></a>Benutzeridentität in Browserumgebung
`TeamsUserCredential`stellt Teams Identität des aktuellen Benutzers dar. Wenn Sie diese Anmeldeinformationen verwenden, wird die Zustimmung des Benutzers zum ersten Mal angefordert. Es nutzt den Teams SSO- und On-Behalf-Of-Fluss, um den Tokenaustausch durchzuführen. SDK verwendet diese Anmeldeinformationen, wenn Entwickler die Benutzeridentität in der Browserumgebung auswählen.

Erforderliche Konfiguration: `initiateLoginEndpoint`, `clientId`.

#### <a name="user-identity-in-nodejs-environment"></a>Benutzeridentität in Node.js Umgebung
`OnBehalfOfUserCredential`verwendet den On-Behalf-Of-Fluss und benötigt Teams SSO-Token. Es wurde für die Verwendung in Azure-Funktionen oder Bot-Szenarien entwickelt. SDK verwendet diese Anmeldeinformationen, wenn Entwickler die Benutzeridentität in Node.js Umgebung auswählen.

Erforderliche Konfiguration: `authorityHost`, `tenantId`, `clientId`oder `clientSecret` `certificateContent`.

#### <a name="application-identity-in-nodejs-environment"></a>Anwendungsidentität in Node.js Umgebung
`AppCredential` stellt die Anwendungsidentität dar. Es wird in der Regel verwendet, wenn der Benutzer nicht wie ein zeittriggerter Automatisierungsauftrag beteiligt ist. SDK verwendet diese Anmeldeinformationen, wenn Entwickler die App-Identität in Node.js Umgebung auswählen.

Erforderliche Konfiguration: `tenantId`, `clientId`oder `clientSecret` `certificateContent`.

### <a name="bot-sso"></a>Bot-SSO

Bot-bezogene Klassen werden im [Botordner](https://github.com/OfficeDev/TeamsFx/tree/main/packages/sdk/src/bot) gespeichert.

`TeamsBotSsoPrompt` hat eine gute Integration in Bot Framework. Es vereinfacht den Authentifizierungsprozess, wenn Sie eine Botanwendung entwickeln und den Bot-SSO nutzen möchten.

Erforderliche Konfiguration: `initiateLoginEndpoint`, `tenantId`, `clientId`und `applicationIdUri`.

### <a name="supported-functions"></a>Unterstützte Funktionen

Das TeamsFx SDK bietet mehrere Funktionen, um die Konfiguration für Drittanbieterbibliotheken zu vereinfachen. Sie befinden sich unter dem [Hauptordner](https://github.com/OfficeDev/TeamsFx/tree/main/packages/sdk/src/core).

*  Microsoft Graph Service:`createMicrosoftGraphClient` und `MsGraphAuthProvider` Hilfe beim Erstellen authentifizierter Graph Instanz.
*  SQL:`getTediousConnectionConfig` Gibt eine mühsame Verbindungskonfiguration zurück.

Erforderliche Konfiguration:
* `sqlServerEndpoint`, `sqlUsername`, `sqlPassword` wenn Sie die Benutzeridentität verwenden möchten
* `sqlServerEndpoint`, `sqlIdentityId` wenn Sie die MSI-Identität verwenden möchten

### <a name="error-handling"></a>Fehlerbehandlung

Api-Fehlerantwort ist `ErrorWithCode`, die Fehlercode und Fehlermeldung enthält. Um beispielsweise einen bestimmten Fehler herauszufiltern, können Sie den folgenden Codeausschnitt verwenden:

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

Der folgende Abschnitt enthält mehrere Codeausschnitte für häufige Szenarien:

<br>

<details>
<summary><b>Verwenden von Graph-API in der Registerkarten-App</b></summary>
 
Verwenden `TeamsFx` und `createMicrosoftGraphClient`.

```ts
const teamsfx = new TeamsFx();
const graphClient = createMicrosoftGraphClient(teamsfx, ["User.Read"]);
const profile = await graphClient.api("/me").get();
```

</details>

<br>

<details>
<summary><b>Aufrufen der Azure-Funktion in der Registerkarten-App</b></summary>

Verwenden Sie `axios` die Bibliothek, um eine HTTP-Anforderung an die Azure-Funktion zu senden.

```ts
const teamsfx = new TeamsFx();
const token = teamsfx.getCredential().getToken(""); // Get SSO token for the use
// Call API hosted in Azure Functions on behalf of user
const apiEndpoint = teamsfx.getConfig("apiEndpoint");
const response = await axios.default.get(apiEndpoint + "api/httptrigger1", {
  headers: {
    authorization: "Bearer " + token,
  },
});
```

</details>

<br>

<details>
<summary><b>Zugreifen auf SQL-Datenbank in der Azure-Funktion</b></summary>


Verwenden Sie `tedious` die Bibliothek, um auf SQL zuzugreifen und die Authentifizierung zu verwalten`DefaultTediousConnectionConfiguration`.
Abgesehen davon `tedious`können Sie auch Verbindungskonfigurationen anderer SQL Bibliotheken basierend auf dem Ergebnis von `sqlConnectionConfig.getConfig()`verfassen.

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
<summary><b>Verwenden der zertifikatbasierten Authentifizierung in der Azure-Funktion</b></summary>

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
<summary><b>Verwenden von Graph-API in der Botanwendung</b></summary>

Zum Dialogfeldsatz hinzufügen `TeamsBotSsoPrompt` .

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

Sie können die Kundenprotokollebene festlegen und Ausgaben umleiten, wenn Sie diese Bibliothek verwenden. Die Protokollierung ist standardmäßig deaktiviert. Sie können sie aktivieren, indem Sie die Protokollebene festlegen.

#### <a name="enable-log-by-setting-log-level"></a>Aktivieren des Protokolls durch Festlegen der Protokollebene

Die Protokollierung ist nur aktiviert, wenn Sie die Protokollebene festlegen. Standardmäßig werden Protokollinformationen in der Konsole gedruckt.

Legen Sie die Protokollebene mithilfe des folgenden Codeausschnitts fest:

```ts
// Only need the warning and error messages.
setLogLevel(LogLevel.Warn);
```

Sie können die Protokollausgabe umleiten, indem Sie die benutzerdefinierte Protokollierungs- oder Protokollfunktion festlegen.

#### <a name="redirect-by-setting-custom-logger"></a>Umleiten durch Festlegen des benutzerdefinierten Loggers

```ts
setLogLevel(LogLevel.Info);
// Set another logger if you want to redirect to Application Insights in Azure Function
setLogger(context.log);
```

#### <a name="redirect-by-setting-custom-log-function"></a>Umleiten durch Festlegen einer benutzerdefinierten Protokollfunktion

> [!NOTE]
> Die Protokollfunktion wird nicht wirksam, wenn Sie eine benutzerdefinierte Protokollierung festlegen.

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

## <a name="override-configuration"></a>Außerkraftsetzen der Konfiguration
Sie können beim Erstellen einer TeamsFx-Instanz eine benutzerdefinierte Konfiguration übergeben, um die Standardkonfiguration zu überschreiben oder erforderliche Felder festzulegen, wenn Umgebungsvariablen fehlen.

- Wenn Sie ein Registerkartenprojekt mit VS Code Toolkit erstellt haben, werden die folgenden Konfigurationswerte aus vorkonfigurierten Umgebungsvariablen verwendet:
  * authorityHost (REACT_APP_AUTHORITY_HOST)
  * tenantId (REACT_APP_TENANT_ID)
  * clientId (REACT_APP_CLIENT_ID)
  * initiateLoginEndpoint (REACT_APP_START_LOGIN_PAGE_URL)
  * applicationIdUri (REACT_APP_START_LOGIN_PAGE_URL)
  * apiEndpoint (REACT_APP_FUNC_ENDPOINT)
  * apiName (REACT_APP_FUNC_NAME)

- Wenn Sie das Azure Function/Bot-Projekt mit VS Code Toolkit erstellt haben, werden die folgenden Konfigurationswerte aus vorkonfigurierten Umgebungsvariablen verwendet:
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

## <a name="upgrade-latest-sdk-version"></a>Aktualisieren der neuesten SDK-Version

Wenn Sie die Version des SDK verwenden, die vorhanden ist `loadConfiguration()`, können Sie die folgenden Schritte ausführen, um auf die neueste SDK-Version zu aktualisieren.
1. Entfernen `loadConfiguration()` und Übergeben angepasster Einstellungen mithilfe von `new TeamsFx(IdentityType.User, { ...customConfig })`
2. Ersetzen durch `new TeamsUserCredential()``new TeamsFx()`
3. Ersetzen durch `new M365TenantCredential()``new TeamsFx(IdentityType.App)`
4. Ersetzen durch `new OnBehalfOfUserCredential(ssoToken)``new TeamsFx().setSsoToken(ssoToken)`
5. Übergeben der Instanz von an Hilfsfunktionen zum Ersetzen der `TeamsFx` Anmeldeinformationsinstanz

Weitere Informationen finden Sie unter [TeamsFx-Klasse](#teamsfx-class).

## <a name="next-step"></a>Nächster Schritt

[Beispiele](https://github.com/OfficeDev/TeamsFx-Samples) für detaillierte Beispiele zur Verwendung des TeamsFx SDK.

## <a name="see-also"></a>Siehe auch

[Microsoft TeamsFx-Beispielkatalog](https://github.com/OfficeDev/TeamsFx-Samples).
