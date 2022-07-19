---
title: Live Share Code-Lernprogramm
author: surbhigupta
description: In diesem Modul erfahren Sie, wie Sie mit Live Share SDK beginnen und wie Sie mit Live Share SDK ein Beispiel für Dice Roller erstellen.
ms.topic: conceptual
ms.localizationpriority: high
ms.author: stevenic
ms.date: 04/07/2022
ms.openlocfilehash: 0210962126604733c4d66ba0db4276ff36cfd6b7
ms.sourcegitcommit: 79d525c0be309200e930cdd942bc2c753d0b718c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2022
ms.locfileid: "66841799"
---
# <a name="dice-roller-code-tutorial"></a>Dice Roller Code-Lernprogramm

In der Dice Roller-Beispiel-App wird Benutzern ein Würfel mit einer Schaltfläche zum Rollen angezeigt. Wenn der Würfel rollt, verwendet das Live Share SDK das Fluid Framework, um die Daten clientsübergreifend zu synchronisieren, sodass jeder das gleiche Ergebnis sieht. Führen Sie zum Synchronisieren von Daten die folgenden Schritte in der Datei [app.js](https://github.com/microsoft/live-share-sdk/blob/main/samples/01.dice-roller/src/app.js) aus:

1. [Einrichten der Anwendung](#set-up-the-application)
2. [Verknüpfen eines Fluid-Containers](#join-a-fluid-container)
3. [Schreiben der Phasenansicht](#write-the-stage-view)
4. [Verbinden der Phasenansicht zu Fluid-Daten](#connect-stage-view-to-fluid-data)
5. [Schreiben der Seitenbereichsansicht](#write-the-side-panel-view)
6. [Schreiben der Einstellungsansicht](#write-the-settings-view)

:::image type="content" source="../assets/images/teams-live-share/dice-roller.png" alt-text="DiceRoller-Beispiel":::

## <a name="set-up-the-application"></a>Einrichten der Anwendung

Beginnen Sie mit dem Importieren der erforderlichen Module. Das Beispiel verwendet den [SharedMap-DDS](https://fluidframework.com/docs/data-structures/map/) aus dem Fluid Framework und den [TeamsFluidClient](/javascript/api/@microsoft/live-share/teamsfluidclient) aus dem Live Share SDK. Das Beispiel unterstützt die Erweiterbarkeit von Teams-Besprechungen, daher müssen wir das [Teams-Client-SDK](https://github.com/OfficeDev/microsoft-teams-library-js) einschließen. Schließlich ist das Beispiel so konzipiert, dass es sowohl lokal als auch in einer Teams-Besprechung ausgeführt wird. Daher müssen wir einige zusätzliche Fluid Framework-Komponenten einschließen, [die zum lokalen Testen des Beispiels](https://fluidframework.com/docs/testing/testing/#azure-fluid-relay-as-an-abstraction-for-tinylicious) erforderlich sind.
  
Anwendungen erstellen Fluid-Container mithilfe eines Schemas, das eine Reihe von *anfänglichen Objekten* definiert, die für den Container verfügbar sind. Im Beispiel wird eine SharedMap verwendet, um den letzten Würfelwert zu speichern, der gerollt wurde. Weitere Informationen finden Sie unter [Datenmodellierung](https://fluidframework.com/docs/build/data-modeling/).

Teams-Besprechungs-Apps erfordern mehrere Ansichten (Inhalt, Konfiguration und Phase). Wir erstellen eine `start()`-Funktion, um die zu rendernden Ansichten zu identifizieren und alle erforderlichen Initialisierungen auszuführen. Wir möchten, dass unsere App sowohl die lokale Ausführung in einem Webbrowser als auch innerhalb einer Teams-Besprechung unterstützt, sodass die `start()`-Funktion nach einem `inTeams=true`-Abfrageparameter sucht, um zu bestimmen, ob er in Teams ausgeführt wird. Bei der Ausführung in Teams muss Ihre Anwendung `app.initialize()` aufrufen, bevor sie andere Teams-js-Methoden aufruft.

Zusätzlich zum `inTeams=true`-Abfrageparameter können wir einen `view=content|config|stage`-Abfrageparameter verwenden, um die Ansicht zu bestimmen, die gerendert werden muss.

```js
import { SharedMap } from "fluid-framework";
import { TeamsFluidClient } from "@microsoft/live-share";
import { app, pages } from "@microsoft/teams-js";
import { LOCAL_MODE_TENANT_ID } from "@fluidframework/azure-client";
import { InsecureTokenProvider } from "@fluidframework/test-client-utils";

const searchParams = new URL(window.location).searchParams;
const root = document.getElementById("content");

// Define container schema

const diceValueKey = "dice-value-key";

const containerSchema = {
  initialObjects: { diceMap: SharedMap }
};

function onContainerFirstCreated(container) {
  // Set initial state of the rolled dice to 1.
  container.initialObjects.diceMap.set(diceValueKey, 1);
}


// STARTUP LOGIC

async function start() {

  // Check for page to display
  let view = searchParams.get('view') || 'stage';

  // Check if we are running on stage.
  if (!!searchParams.get('inTeams')) {

    // Initialize teams app
    await app.initialize();

    // Get our frameContext from context of our app in Teams
    const context = await app.getContext();
    if (context.page.frameContext == 'meetingStage') {
      view = 'stage';
    }
  }

  // Load the requested view
  switch (view) {
    case 'content':
      renderSidePanel(root);
      break;
    case 'config':
      renderSettings(root);
      break;
    case 'stage':
    default:
      const { container } = await joinContainer();
      renderStage(container.initialObjects.diceMap, root);
      break;
  }
}

start().catch((error) => console.error(error));
```

## <a name="join-a-fluid-container"></a>Verknüpfen eines Fluid-Containers

Nicht alle Ihre App-Ansichten müssen zusammenarbeiten. Die `stage`-Ansicht benötigt *immer* Funktionen für die Zusammenarbeit, die `content`-Ansicht benötigt *möglicherweise* Funktionen für die Zusammenarbeit, und die `config`-Ansicht sollte *niemals* Funktionen für die Zusammenarbeit benötigen. Für die Ansichten, die Funktionen für die Zusammenarbeit benötigen, müssen Sie einem Fluid-Container beitreten, der der aktuellen Besprechung zugeordnet ist.

Der Beitritt zum Container für das Meeting ist so einfach wie das Erstellen eines neuen [TeamsFluidClient](/javascript/api/@microsoft/live-share/teamsfluidclient) und das anschließende Aufrufen seiner Methode [joinContainer()](/javascript/api/@microsoft/live-share/teamsfluidclient#@microsoft-live-share-teamsfluidclient-joincontainer).  Wenn Sie lokal ausgeführt werden, müssen Sie eine benutzerdefinierte Verbindungskonfiguration mit einem speziellen `LOCAL_MODE_TENANT_ID` übergeben. Andernfalls ist der Beitritt zu einem lokalen Container mit dem Beitritt zu einem Container in Teams identisch.

```js
async function joinContainer() {
  // Are we running in teams?
  let client;
  if (!!searchParams.get('inTeams')) {
      // Create client
      client = new TeamsFluidClient();
  } else {
      // Create client and configure for testing
      client = new TeamsFluidClient({
        connection: {
          tenantId: LOCAL_MODE_TENANT_ID,
          tokenProvider: new InsecureTokenProvider("", { id: "123", name: "Test User" }),
          orderer: "http://localhost:7070",
          storage: "http://localhost:7070",
        }
      });
  }

  // Join container
  return await client.joinContainer(containerSchema, onContainerFirstCreated);
}
```

> [!NOTE]
> Beim lokalen Testen aktualisiert TeamsFluidClient die Browser-URL so, dass sie die ID des erstellten Testcontainers enthält. Wenn Sie diesen Link auf andere Browserregisterkarten kopieren, wird TeamsFluidClient dem erstellten Testcontainer hinzugefügt. Wenn die Änderung der Anwendungs-URL den Betrieb der Anwendung beeinträchtigt, kann die zum Speichern der Testcontainer-ID verwendete Strategie mithilfe der Optionen [setLocalTestContainerId](/javascript/api/@microsoft/live-share/iteamsfluidclientoptions#@microsoft-live-share-iteamsfluidclientoptions-setlocaltestcontainerid) und [getLocalTestContainerId](/javascript/api/@microsoft/live-share/iteamsfluidclientoptions#@microsoft-live-share-iteamsfluidclientoptions-getlocaltestcontainerid) angepasst werden, die an TeamsFluidClient übergeben werden.

## <a name="write-the-stage-view"></a>Schreiben der Phasenansicht

Viele Teams Meeting Extensibility-Anwendungen sind für die Verwendung von React für ihr Ansichtsframework konzipiert, dies ist jedoch nicht erforderlich. In diesem Beispiel werden beispielsweise HTML/DOM-Standardmethoden verwendet, um eine Ansicht zu rendern.

### <a name="start-with-a-static-view"></a>Beginnen mit einer statischen Ansicht

Es ist einfach, die Ansicht mit lokalen Daten ohne Fluid-Funktionalität zu erstellen und dann Fluid hinzuzufügen, indem Sie einige wichtige Teile der App ändern.

Die `renderStage`-Funktion fügt `stageTemplate` an das übergebene HTML-Element an und erstellt jedes Mal, wenn die Schaltfläche **Rollen** ausgewählt wird, eine funktionierende Würfelrolle mit einem zufälligen Würfelwert. `diceMap` wird in den nächsten Schritten verwendet.

```js
const stageTemplate = document.createElement("template");

stageTemplate["innerHTML"] = `
  <div class="wrapper">
    <div class="dice"></div>
    <button class="roll"> Roll </button>
  </div>
`
function renderStage(diceMap, elem) {
    elem.appendChild(stageTemplate.content.cloneNode(true));
    const rollButton = elem.querySelector(".roll");
    const dice = elem.querySelector(".dice");

    rollButton.onclick = () => updateDice(Math.floor(Math.random() * 6)+1);

    const updateDice = (value) => {
        // Unicode 0x2680-0x2685 are the sides of a die (⚀⚁⚂⚃⚄⚅).
        dice.textContent = String.fromCodePoint(0x267f + value);
    };
    updateDice(1);
}
```

## <a name="connect-stage-view-to-fluid-data"></a>Verbinden der Phasenansicht zu Fluid-Daten

### <a name="modify-fluid-data"></a>Ändern von Fluid-Daten

Um Fluid in der Anwendung zu verwenden, müssen Sie zunächst ändern, was geschieht, wenn der Benutzer `rollButton` auswählt. Anstatt den lokalen Zustand direkt zu aktualisieren, aktualisiert die Schaltfläche die Zahl, die im `value`-Schlüssel der übergebenen `diceMap` gespeichert ist. Da `diceMap` ein Fluid `SharedMap` ist, werden Änderungen an alle Clients verteilt. Alle Änderungen am `diceMap` führen dazu, dass ein `valueChanged`-Ereignis ausgegeben wird, und ein Ereignishandler kann eine Aktualisierung der Ansicht auslösen.

Dieses Muster ist in Fluid üblich, da es der Ansicht ermöglicht, sich sowohl bei lokalen als auch bei Remoteänderungen auf die gleiche Weise zu verhalten.

```js
    rollButton.onclick = () => diceMap.set("dice-value-key", Math.floor(Math.random() * 6)+1);
```

### <a name="rely-on-fluid-data"></a>Verwenden von Fluid-Daten

Die nächste Änderung, die vorgenommen werden muss, besteht darin, die `updateDice`-Funktion so zu ändern, dass sie keinen beliebigen Wert mehr akzeptiert. Dies bedeutet, dass die App den lokalen Würfelwert nicht mehr direkt ändern kann. Stattdessen wird der Wert jedes Mal aus dem `SharedMap` abgerufen, wenn `updateDice` aufgerufen wird.

```js
    const updateDice = () => {
        const diceValue = diceMap.get("dice-value-key");
        dice.textContent = String.fromCodePoint(0x267f + diceValue);
    };
    updateDice();
```

### <a name="handle-remote-changes"></a>Behandeln von Remoteänderungen

Die von `diceMap` zurückgegebenen Werte sind nur eine Momentaufnahme in der Zeit. Um die Daten bei Änderungen auf dem neuesten Stand zu halten, muss ein Ereignishandler auf dem `diceMap` festgelegt werden, um jedes Mal `updateDice` aufzurufen, wenn das `valueChanged`-Ereignis gesendet wird. Eine Liste der ausgelösten Ereignisse und der an diese Ereignisse übergebenen Werte finden Sie unter [SharedMap](https://fluidframework.com/docs/data-structures/map/).

```js
    diceMap.on("valueChanged", updateDice);
```

## <a name="write-the-side-panel-view"></a>Schreiben der Seitenbereichsansicht

Die Seitenbereichsansicht, die über die Registerkarte "`contentUrl`" mit dem `sidePanel`-Framekontext geladen wird, wird dem Benutzer in einem Seitenbereich angezeigt, wenn er Ihre App innerhalb einer Besprechung öffnet. Das Ziel dieser Ansicht besteht darin, einem Benutzer die Auswahl von Inhalten für die App zu ermöglichen, bevor die App für die Besprechungsphase freigegeben wird. Für die Live Share SDK-Apps kann die Seitenbereichsansicht auch als Begleitoberfläche für die App verwendet werden. Der Aufruf von [joinContainer()](/javascript/api/@microsoft/live-share/teamsfluidclient#@microsoft-live-share-teamsfluidclient-joincontainer) aus der Seitenbereichsansicht stellt eine Verbindung mit demselben Fluid-Container her, mit dem die Phasenansicht verbunden ist. Dieser Container kann dann für die Kommunikation mit der Phasenansicht verwendet werden. Stellen Sie sicher, dass Sie mit der Stufenansicht *und* der Seitenbereichsansicht aller Benutzer kommunizieren.

In der Seitenbereichsansicht des Beispiels wird der Benutzer aufgefordert, die Schaltfläche "Freigeben in Phase" auszuwählen.

```js
const sidePanelTemplate = document.createElement("template");

sidePanelTemplate["innerHTML"] = `
  <style>
    .wrapper { text-align: center }
    .title { font-size: large; font-weight: bolder; }
    .text { font-size: medium; }
  </style>
  <div class="wrapper">
    <p class="title">Lets get started</p>
    <p class="text">Press the share to stage button to share Dice Roller to the meeting stage.</p>
  </div>
`;

function renderSidePanel(elem) {
    elem.appendChild(sidePanelTemplate.content.cloneNode(true));
}
```

## <a name="write-the-settings-view"></a>Schreiben der Einstellungsansicht

Die Einstellungsansicht, die über `configurationUrl` in Ihrem App-Manifest geladen wird, wird einem Benutzer angezeigt, wenn er Ihre App zum ersten Mal einer Teams-Besprechung hinzufügt. In dieser Ansicht kann der Entwickler `contentUrl` für die Registerkarte konfigurieren, die basierend auf Benutzereingaben an die Besprechung angeheftet ist. Diese Seite ist derzeit auch dann erforderlich, wenn zum Festlegen des `contentUrl` keine Benutzereingabe erforderlich ist.

> [!Important]
> Der [joinContainer()](/javascript/api/@microsoft/live-share/teamsfluidclient#@microsoft-live-share-teamsfluidclient-joincontainer) des Live Share SDK wird im Kontext der Registerkarte "`settings`" nicht unterstützt.

In der Einstellungsansicht des Beispiels wird der Benutzer aufgefordert, die Schaltfläche "Speichern" auszuwählen.

```js
const settingsTemplate = document.createElement("template");

settingsTemplate["innerHTML"] = `
  <style>
    .wrapper { text-align: center }
    .title { font-size: large; font-weight: bolder; }
    .text { font-size: medium; }
  </style>
  <div class="wrapper">
    <p class="title">Welcome to Dice Roller!</p>
    <p class="text">Press the save button to continue.</p>
  </div>
`;

function renderSettings(elem) {
    elem.appendChild(settingsTemplate.content.cloneNode(true));

    // Save the configurable tab
    pages.config.registerOnSaveHandler(saveEvent => {
      pages.config.setConfig({
        websiteUrl: window.location.origin,
        contentUrl: window.location.origin + '?inTeams=1&view=content',
        entityId: 'DiceRollerFluidLiveShare',
        suggestedDisplayName: 'DiceRollerFluidLiveShare'
      });
      saveEvent.notifySuccess();
    });

    // Enable the Save button in config dialog
    pages.config.setValidityState(true);
}
```

## <a name="test-locally"></a>Lokal testen

Sie können Ihre App lokal mithilfe von `npm run start` testen. Weitere Informationen finden Sie im [Schnellstarthandbuch](./teams-live-share-quick-start.md).

## <a name="test-in-teams"></a>In Teams testen

Nachdem Sie Ihre App lokal mit `npm run start` ausgeführt haben, können Sie Ihre App in Teams testen. Wenn Sie Ihre App ohne Bereitstellung testen möchten, laden Sie den [`ngrok`](https://ngrok.com/) Tunnelingdienst herunter, und verwenden Sie diesen.

### <a name="create-a-ngrok-tunnel-to-allow-teams-to-reach-your-app"></a>Erstellen eines ngrok-Tunnels, damit Teams Ihre App erreichen kann

1. [ngrok herunterladen](https://ngrok.com/download).

1. Verwenden Sie ngrok, um einen Tunnel mit Port 8080 zu erstellen. Führen Sie den folgenden Befehl aus:

    ```
     `ngrok http 8080 --host-header=localhost`
    ```

    Ein neues ngrok-Terminal wird mit einer neuen URL geöffnet, z. B. `https:...ngrok.io`. Die neue URL ist der Tunnel, der auf Ihre App verweist, die in Ihrer `manifest.json`-App aktualisiert werden muss.

### <a name="create-the-app-package-to-sideload-into-teams"></a>Erstellen des App-Pakets zum Querladen in Teams

1. Wechseln Sie zum Dice Roller Beispielordner `\live-share-sdk\samples\01.dice-roller` auf Ihrem Computer. Sie können auch [`.\manifest\manifest.json`](https://github.com/microsoft/live-share-sdk/tree/main/samples/01.dice-roller/manifest) aus dem Dice Roller-Beispiel auf GitHub überprüfen.

1. Öffnen Sie "manifest.json", und aktualisieren Sie die Konfigurations-URL.

   Ersetzen Sie `https://<<BASE_URI_DOMAIN>>` durch Ihren HTTP-Endpunkt aus ngrok.

1. Sie können die folgenden Felder aktualisieren:
   * Legen Sie `developer.name` auf Ihren Namen fest.
   * Aktualisieren Sie `developer.websiteUrl` mit Ihrer Website.
   * Aktualisieren Sie `developer.privacyUrl` mit Ihrer Datenschutzrichtlinie.
   * Aktualisieren Sie `developer.termsOfUseUrl` mit Ihren Nutzungsbedingungen.

1. Zippen Sie den Inhalt des Manifestordners, um `manifest.zip` zu erstellen. Stellen Sie sicher, dass `manifest.zip` nur die `manifest.json`-Quelldatei, das `color`-Symbol und das `outline`-Symbol enthält.

   1. Wählen Sie unter Windows alle Dateien im `.\manifest`-Verzeichnis aus, und komprimieren Sie sie.
  
   > [!NOTE]
   >
   > * Zippen Sie den enthaltenden Ordner nicht.
   > * Geben Sie Ihrer ZIP-Datei einen aussagekräftigen Namen. Beispiel: `DiceRollerLiveShare`.
  
   Weitere Informationen zum Manifest finden Sie in der [Dokumentation zum Teams-Manifest](../resources/schema/manifest-schema.md).

### <a name="sideload-your-app-into-a-meeting"></a>Querladen der App in eine Besprechung

1. Öffnen Sie Teams.

1. Planen Sie eine Besprechung aus dem Kalender in Teams. Stellen Sie sicher, dass Sie mindestens einen Teilnehmer zur Besprechung einladen.

1. Nehmen Sie an der Besprechung teil.

1. Wählen Sie oben im Besprechungsfenster **+ Apps** > **Apps verwalten** aus.

1. Wählen Sie im Bereich **Apps verwalten** die Option **Benutzerdefinierte App hochladen** aus.

   1. Wenn die Option **Benutzerdefinierte App hochladen** nicht angezeigt wird, befolgen Sie die [Anweisungen](/microsoftteams/teams-custom-app-policies-and-settings), um benutzerdefinierte Apps in Ihrem Mandanten zu aktivieren.

1. Wählen Sie die `manifest.zip`-Datei aus, und laden Sie sie von Ihrem Computer hoch.

1. Wählen Sie **Hinzufügen** aus, um Ihre Beispiel-App zur Besprechung hinzuzufügen.

1. Wählen Sie **+Apps** aus, geben Sie Dice Roller in das Suchfeld **App suchen** ein.

1. Wählen Sie die App aus, um sie in der Besprechung zu aktivieren.

1. Wählen Sie **Speichern**.

   Die Dice Roller-App wird dem Teams-Besprechungsbereich hinzugefügt.

1. Wählen Sie im Seitenbereich das Symbol "In Phase freigeben" aus. Teams startet eine Livesynchronisierung mit den Benutzern im Freigabefenster in der Besprechung.

   :::image type="content" source="../assets/images/teams-live-share/teams-live-share-to-stage.png" alt-text="Symbol &quot;In Phase freigeben&quot;":::

   Jetzt sollte die Würfelrolle im Freigabefenster angezeigt werden.

   :::image type="content" source="../assets/images/teams-live-share/teams-live-share-meeting-stage.png" alt-text="Abbildung des Freigabefensters":::

Benutzer, die zur Besprechung eingeladen sind, können Ihre App auf der Phase sehen, wenn sie an der Besprechung teilnehmen.

## <a name="deployment"></a>Bereitstellung

Nachdem Sie Ihren Code bereitgestellt haben, können Sie [Teams Toolkit](../toolkit/provision.md#provision-using-teams-toolkit) oder das [Teams-Entwicklerportal](https://dev.teams.microsoft.com/apps) verwenden, um die ZIP-Datei Ihrer App bereitzustellen und hochzuladen.

> [!NOTE]
> Sie müssen Ihre bereitgestellte appId dem `manifest.json` hinzufügen, bevor Sie die App hochladen oder verteilen.

## <a name="code-samples"></a>Codebeispiele

| Beispielname | Beschreibung                                                      | JavaScript                                                                           |
| :---------- | ---------------------------------------------------------------- | ------------------------------------------------------------------------------------ |
| Dice Roller | Ermöglichen Sie allen verbundenen Clients, einen Würfel zu rollen und das Ergebnis anzuzeigen. | [View](https://github.com/microsoft/live-share-sdk/tree/main/samples/01.dice-roller) |

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Kernfunktionen](teams-live-share-capabilities.md)

## <a name="see-also"></a>Siehe auch

* [GitHub-Repository](https://github.com/microsoft/live-share-sdk)
* [Live Share SDK-Referenzdokumente](/javascript/api/@microsoft/live-share/)
* [Live Share Media SDK-Referenzdokumente](/javascript/api/@microsoft/live-share-media/)
* [Live Share – FAQ](teams-live-share-faq.md)
* [Teams-Apps in Besprechungen](teams-apps-in-meetings.md)
