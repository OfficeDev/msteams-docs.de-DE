---
title: Verwenden von Fluid mit Teams
author: timtwang
ms.author: mobajemu
description: Lernprogramm zum Integrieren von Fluid-unterstützten Echtzeit-Zusammenarbeitsfeatures in eine Microsoft Teams-Registerkartenanwendung
ms.localizationpriority: medium
ms.topic: conceptual
ms.openlocfilehash: 620e2150ca6300fb8d37bc7c68b965aacb19700b
ms.sourcegitcommit: 40d4bde10b6820c62e49e2400b10ab3569c8c815
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/20/2022
ms.locfileid: "68615442"
---
# <a name="use-fluid-with-teams"></a>Verwenden von Fluid mit Teams

Am Ende dieses Lernprogramms können Sie jede fluidgestützte Anwendung in Teams integrieren und in Echtzeit mit anderen zusammenarbeiten.

In diesem Abschnitt lernen Sie die folgenden Konzepte kennen:

1. Integrieren Sie einen Fluid-Client in die Teams-Registerkartenanwendung.
1. Führen Sie Ihre Teams-Anwendung aus, und verbinden Sie sie mit einem Fluid-Dienst (Azure Fluid Relay).
1. Erstellen und abrufen Sie Fluidcontainer, und übergeben Sie sie an eine React Komponente.

Weitere Informationen zum Erstellen komplexer Anwendungen finden Sie unter [Teams Fluid Hallo Welt](https://github.com/microsoft/FluidExamples/tree/main/teams-fluid-hello-world) Beispiel in unserem FluidExamples-Repository.

## <a name="prerequisites"></a>Voraussetzungen

Dieses Lernprogramm erfordert Kenntnisse in den folgenden Konzepten und Ressourcen:

- [Fluid Framework (Übersicht)](https://fluidframework.com/docs/)
- [Fluid Framework – Schnellstart](https://fluidframework.com/docs/start/quick-start/)
- Grundlagen [React und](https://reactjs.org/) [React Hooks](https://reactjs.org/docs/hooks-intro.html)
- So erstellen Sie eine [Microsoft Teams-Registerkarte](/microsoftteams/platform/tabs/what-are-tabs)

> [!div class="nextstepaction"]
> [Erforderliche Komponenten installieren](tab-requirements.md)

## <a name="create-the-project"></a>Erstellen des Projekts

1. Öffnen Sie eine Eingabeaufforderung, und navigieren Sie zu dem übergeordneten Ordner, in dem Sie das Projekt erstellen möchten, `/My Microsoft Teams Projects`z. B. .
1. Erstellen Sie eine Teams-Registerkartenanwendung, indem Sie den folgenden Befehl ausführen und [eine Kanalregisterkarte erstellen](create-channel-group-tab.md#create-a-custom-channel-or-group-tab-with-nodejs):

    ```cmd
    yo teams
    ```

1. Navigieren Sie nach dem Erstellen mit dem folgenden Befehl `cd <your project name>`zum Projekt.
1. Das Projekt verwendet die folgenden Bibliotheken:

    |Bibliothek |Beschreibung |
    |---|---|
    | `fluid-framework`    |Enthält den IFluidContainer und andere [verteilte Datenstrukturen](https://fluidframework.com/docs/build/dds/) , die Daten über Clients hinweg synchronisieren.|
    | `@fluidframework/azure-client`   |Definiert das Startschema für den [Fluid-Container](https://fluidframework.com/docs/build/containers/).|
    | `@fluidframework/test-client-utils` |Definiert die `InsecureTokenProvider` zum Erstellen der Verbindung mit einem Fluid-Dienst erforderlichen.|

    Führen Sie den folgenden Befehl aus, um die Bibliotheken zu installieren:

    ```cmd
    npm install @fluidframework/azure-client fluid-framework @fluidframework/test-client-utils
    ```

## <a name="code-the-project"></a>Programmieren des Projekts

1. Öffnen Sie die Datei `/src/client/<your tab name>` in Ihrem Code-Editor.
1. Erstellen Sie eine neue Datei, `Util.ts` und fügen Sie die folgenden Importanweisungen hinzu:

    ```ts
    //`Util.ts

    import { IFluidContainer } from "fluid-framework";
    import { AzureClient, AzureClientProps } from "@fluidframework/azure-client";
    import { InsecureTokenProvider } from "@fluidframework/test-client-utils";
    ```

### <a name="defining-fluid-functions-and-parameters"></a>Definieren von Fluid-Funktionen und -Parametern

Diese App ist für die Verwendung im Kontext von Microsoft Teams vorgesehen, wobei alle Fluid-bezogenen Importe, Initialisierungen und Funktionen zusammen verwendet werden. Dies bietet eine verbesserte Erfahrung und erleichtert die Verwendung in der Zukunft. Sie können den Importanweisungen den folgenden Code hinzufügen:

```ts
// TODO 1: Define the parameter key(s).
// TODO 2: Define container schema.
// TODO 3: Define connectionConfig (AzureClientProps).
// TODO 4: Create Azure client.
// TODO 5: Define create container function.
// TODO 6: Define get container function.
```

> [!NOTE]
> Die Kommentare definieren alle Funktionen und Konstanten, die für die Interaktion mit dem Fluid-Dienst und -Container erforderlich sind.

1. Ersetzen Sie `TODO 1:` durch den folgenden Code:

    ```ts
    export const containerIdQueryParamKey = "containerId";
    ```

    Die Konstante wird exportiert, während sie an die in den `contentUrl` Microsoft Teams-Einstellungen angefügt wird, und später zum Analysieren der Container-ID auf der Inhaltsseite. Es ist ein gängiges Muster, wichtige Abfrageparameterschlüssel als Konstanten zu speichern, anstatt jedes Mal die unformatierte Zeichenfolge einzugeben.

    Bevor der Client Container erstellen kann, benötigt er eine `containerSchema` , die die in dieser Anwendung verwendeten freigegebenen Objekte definiert. In diesem Beispiel wird eine SharedMap als `initialObjects`verwendet, aber jedes freigegebene Objekt kann verwendet werden.

    > [!NOTE]
    > Dies `map` ist die ID des `SharedMap` Objekts und muss wie alle anderen DDSes innerhalb des Containers eindeutig sein.

1. Ersetzen Sie `TODO: 2` durch den folgenden Code:

    ```ts
    const containerSchema = {
        initialObjects: { map: SharedMap }
    };
    ```

1. Ersetzen Sie `TODO: 3` durch den folgenden Code:

    ```ts
    const connectionConfig : AzureClientProps =
    {
        connection: {
            type: "local",
            tokenProvider: new InsecureTokenProvider("foobar", { id: "user" }),
            endpoint: "http://localhost:7070"
        }
    };
    ```

    Bevor der Client verwendet werden kann, benötigt er eine `AzureClientProps` , die den Vom Client verwendeten Verbindungstyp definiert. Die `connectionConfig` Eigenschaft ist erforderlich, um eine Verbindung mit dem Dienst herzustellen. Der lokale Modus von Azure Client wird verwendet. Um die Zusammenarbeit über alle Clients hinweg zu ermöglichen, ersetzen Sie sie durch Fluid Relay Service-Anmeldeinformationen. Weitere Informationen finden Sie unter [Einrichten des Azure Fluid Relay-Diensts](/azure/azure-fluid-relay/how-tos/provision-fluid-azure-portal).

1. Ersetzen Sie `TODO: 4` durch den folgenden Code:

    ```ts
    const client = new AzureClient(connectionConfig);
    ```

1. Ersetzen Sie `TODO: 5` durch den folgenden Code:

    ```ts
    export async function createContainer() : Promise<string> {
        const { container } = await client.createContainer(containerSchema);
        const containerId = await container.attach();
        return containerId;
    };
    ```

    Wenn Sie den Container auf der Konfigurationsseite erstellen und an die `contentUrl` Einstellung in Teams anfügen, müssen Sie die Container-ID zurückgeben, nachdem Sie den Container angefügt haben.

1. Ersetzen Sie `TODO: 6` durch den folgenden Code:

    ```ts
    export async function getContainer(id : string) : Promise<IFluidContainer> {
        const { container } = await client.getContainer(id, containerSchema);
        return container;
    };
    ```

    Wenn Sie den Fluid-Container abrufen, müssen Sie den Container zurückgeben, da Ihre Anwendung mit dem Container und den darin enthaltenen DDSes auf der Inhaltsseite interagieren muss.

### <a name="create-fluid-container-in-the-configuration-page"></a>Erstellen eines Fluidcontainers auf der Konfigurationsseite

1. Öffnen Sie die Datei `src/client/<your tab name>/<your tab name>Config.tsx` in Ihrem Code-Editor.

    Der Standardmäßigfluss der Teams-Registerkartenanwendung geht von der Konfiguration zur Inhaltsseite. Um die Zusammenarbeit zu ermöglichen, ist das Beibehalten des Containers beim Laden auf der Inhaltsseite von entscheidender Bedeutung. Die beste Lösung zum Beibehalten des Containers besteht darin, die Container-ID als Abfrageparameter an die `contentUrl` und `websiteUrl`die URLs der Inhaltsseite anzufügen. Die Schaltfläche "Speichern" auf der Teams-Konfigurationsseite ist das Gateway zwischen der Konfigurationsseite und der Inhaltsseite. Hier können Sie den Container erstellen und die Container-ID in den Einstellungen anfügen.

1. Fügen Sie die folgende Importanweisung hinzu:

    ```ts
    import { createContainer, containerIdQueryParamKey } from "./Util";
    ```

1. Ersetzen Sie die `onSaveHandler`-Methode durch den folgenden Code. Die einzigen hier hinzugefügten Zeilen sind das Aufrufen der zuvor `Utils.ts` definierten Create-Containermethode und das anschließende Anfügen der zurückgegebenen Container-ID an den `contentUrl` und `websiteUrl` als Abfrageparameter.

    ```ts {linenos=inline,hl_lines=[134,136,137]}
    const onSaveHandler = async (saveEvent: microsoftTeams.settings.SaveEvent) => {
        const host = "https://" + window.location.host;
        const containerId = await createContainer();
        microsoftTeams.settings.setSettings({
            contentUrl: host + "/<your tab name>/?" + containerIdQueryParamKey + "=" + containerId + "&name={loginHint}&tenant={tid}&group={groupId}&theme={theme}",
            websiteUrl: host + "/<your tab name>/?" + containerIdQueryParamKey + "=" + containerId + "&name={loginHint}&tenant={tid}&group={groupId}&theme={theme}",
            suggestedDisplayName: "<your tab name>",
            removeUrl: host + "/<your tab name>/remove.html?theme={theme}",
            entityId: entityId.current
        });
        saveEvent.notifySuccess();
    };
    ```

    Stellen Sie sicher, dass Sie den Namen der Registerkarte aus Ihrem Projekt ersetzen `<your tab name>` .

    > [!WARNING]
    > Da die URL der Inhaltsseite zum Speichern der Container-ID verwendet wird, wird dieser Datensatz entfernt, wenn die Registerkarte "Teams" gelöscht wird.
    > Darüber hinaus kann jede Inhaltsseite nur eine Container-ID unterstützen.

### <a name="refactor-content-page-to-reflect-fluid-application"></a>Inhaltsseite umgestalten, um die Fluid-Anwendung widerzuspiegeln

1. Öffnen Sie die Datei `src/client/<your tab name>/<your tab name>.tsx` in Ihrem Code-Editor. Eine typische fluidbetriebene Anwendung besteht aus einer Ansicht und einer Fluid-Datenstruktur. Konzentrieren Sie sich auf das Abrufen/Laden des Fluid-Containers und lassen Sie alle fluidbezogenen Interaktionen in einer React Komponente.

1. Fügen Sie die folgenden Importanweisungen auf der Inhaltsseite hinzu:

    ```ts
    import { IFluidContainer } from "fluid-framework";
    import { getContainer, containerIdQueryParamKey } from "./Util";
    ```

1. Entfernen Sie den gesamten Code unter den Importanweisungen auf der Inhaltsseite, und ersetzen Sie ihn durch Folgendes:

    ```ts
    export const <your tab name> = () => {
      // TODO 1: Initialize Microsoft Teams.
      // TODO 2: Initialize inTeams boolean.
      // TODO 3: Define container as a React state.
      // TODO 4: Define a method that gets the Fluid container
      // TODO 5: Get Fluid container on content page startup.
      // TODO 6: Pass the container to the React component as argument.
    }
    ```

    Stellen Sie sicher, dass Sie durch den Registerkartennamen ersetzen `<your tab name>` , den Sie für Ihr Projekt definieren.

1. Ersetzen Sie `TODO 1` durch den folgenden Code:

    ```ts
    microsoftTeams.initialize();
    ```

    Um die Inhaltsseite in Teams anzuzeigen, müssen Sie das [JavaScript-Client-SDK von Microsoft Teams](/javascript/api/overview/msteams-client) einschließen und einen Aufruf zur Initialisierung einschließen, nachdem Die Seite geladen wurde.

1. Ersetzen Sie `TODO 2` durch den folgenden Code:

    ```ts
    const [{ inTeams }] = useTeams();
    ```

    Da die Teams-Anwendung nur eine IFrame-Einfügung einer Webseite ist, müssen Sie die `inTeams` boolesche Konstante initialisieren, um zu wissen, ob sich die Anwendung in Teams befindet oder nicht, und ob die Teams-Ressourcen, z. B. die `contentUrl`, verfügbar sind.

1. Ersetzen Sie `TODO 3` durch den folgenden Code:

    ```ts
    const [fluidContainer, setFluidContainer] = useState<IFluidContainer | undefined>(undefined);
    ```

    Verwenden Sie einen React Zustand für den Container, da er die Möglichkeit bietet, den Container und die darin enthaltenen Datenobjekte dynamisch zu aktualisieren.

1. Ersetzen Sie `TODO 4` durch den folgenden Code:

    ```ts
    const getFluidContainer = async (url : URLSearchParams) => {
        const containerId = url.get(containerIdQueryParamKey);
        if (!containerId) {
            throw Error("containerId not found in the URL");
        }
        const container = await getContainer(containerId);
        setFluidContainer(container);
    };
    ```

    Analysieren Sie die URL, um die Abfrageparameterzeichenfolge abzurufen, die durch definiert ist `containerIdQueryParamKey`, und rufen Sie die Container-ID ab. Mit der Container-ID können Sie den Container laden. Sobald Sie den Container haben, legen Sie den `fluidContainer` React Zustand fest, siehe vorherigen Schritt.

1. Ersetzen Sie `TODO 5` durch den folgenden Code:

    ```ts
    useEffect(() => {
        if (inTeams === true) {
            microsoftTeams.settings.getSettings(async (instanceSettings) => {
                const url = new URL(instanceSettings.contentUrl);
                getFluidContainer(url.searchParams);
            });
            microsoftTeams.appInitialization.notifySuccess();
        }
    }, [inTeams]);
    ```

    Nachdem Sie definiert haben, wie der Fluid-Container abgerufen werden soll, müssen Sie React anweisen, beim Laden aufzurufen`getFluidContainer`, und dann das Ergebnis in einem Zustand speichern, je nachdem, ob sich die Anwendung in Teams befindet.
    der [useState-Hook](https://reactjs.org/docs/hooks-state.html) von React stellt den erforderlichen Speicher bereit, und [useEffect](https://reactjs.org/docs/hooks-effect.html) ermöglicht es Ihnen, das Rendern aufzurufen `getFluidContainer` und den zurückgegebenen Wert an `setFluidContainer`zu übergeben.

    Durch Hinzufügen `inTeams` des Abhängigkeitsarrays am Ende der `useEffect`App wird sichergestellt, dass diese Funktion nur beim Laden der Inhaltsseite aufgerufen wird.

1. Ersetzen Sie `TODO 6` durch den folgenden Code:

    ```ts
    if (inTeams === false) {
      return (
          <div>This application only works in the context of Microsoft Teams</div>
      );
    }

    if (fluidContainer !== undefined) {
      return (
          <FluidComponent fluidContainer={fluidContainer} />
      );
    }

    return (
      <div>Loading FluidComponent...</div>
    );
    ```

    > [!NOTE]
    > Es ist wichtig sicherzustellen, dass die Inhaltsseite in Teams geladen wird und dass der Fluid-Container definiert ist, bevor sie an die React Komponente übergeben wird (definiert als `FluidComponent`, siehe unten).

### <a name="create-react-component-for-fluid-view-and-data"></a>Erstellen React Komponente für dynamische Ansicht und Daten

Sie haben den grundlegenden Erstellungsfluss von Teams und Fluid integriert. Sie können jetzt eine eigene React Komponente erstellen, die die Interaktionen zwischen der Anwendungsansicht und Fluid-Daten verarbeitet. Von nun an verhält sich die Logik und der Fluss wie bei anderen fluidbetriebenen Anwendungen. Nachdem Sie die grundlegende Struktur eingerichtet haben, können Sie eines der [Fluid-Beispiele](https://github.com/microsoft/FluidExamples) als Teams-Anwendung erstellen, indem Sie die Interaktion der `ContainerSchema` Anwendungsansicht mit den DDSes/Datenobjekten auf der Inhaltsseite ändern.

## <a name="start-the-fluid-server-and-run-the-application"></a>Starten Sie den Fluid-Server, und führen Sie die Anwendung aus.

Wenn Sie Ihre Teams-Anwendung lokal mit dem lokalen Azure Client-Modus ausführen, stellen Sie sicher, dass Sie den folgenden Befehl in der Eingabeaufforderung ausführen, um den Fluid-Dienst zu starten:

```cmd
npx @fluidframework/azure-local-service@latest
```

Um die Teams-Anwendung auszuführen und zu starten, öffnen Sie ein anderes Terminal, und folgen Sie den [Anweisungen zum Ausführen des Anwendungsservers](create-channel-group-tab.md#upload-your-application-to-teams).

> [!WARNING]
> HostNames mit `ngrok`den kostenlosen Tunneln werden nicht beibehalten. Bei jeder Ausführung wird eine andere URL generiert. Wenn ein neuer `ngrok` Tunnel erstellt wird, kann nicht mehr auf den älteren Container zugegriffen werden. Produktionsszenarien finden [Sie unter Verwenden von AzureClient mit Azure Fluid Relay](#use-azureclient-with-azure-fluid-relay).

> [!NOTE]
> Installieren Sie eine zusätzliche Abhängigkeit, um diese Demo mit Webpack 5 kompatibel zu machen. Wenn Sie einen Kompilierungsfehler im Zusammenhang mit einem "Pufferpaket" erhalten, führen Sie den Vorgang aus `npm install -D buffer` , und versuchen Sie es erneut. Dies wird in einer zukünftigen Version von Fluid Framework behoben.

## <a name="next-steps"></a>Nächste Schritte

### <a name="use-azureclient-with-azure-fluid-relay"></a>Verwenden von AzureClient mit Azure Fluid Relay

Da es sich hierbei um eine Teams-Registerkartenanwendung handelt, stehen Zusammenarbeit und Interaktion im Mittelpunkt. Ersetzen Sie den zuvor bereitgestellten lokalen Modus `AzureClientProps` durch nicht lokale Anmeldeinformationen aus Ihrer Azure-Dienstinstanz, damit andere Personen an der Anwendung teilnehmen und mit Ihnen interagieren können. Erfahren Sie [, wie Sie Ihren Azure Fluid Relay-Dienst bereitstellen](/azure/azure-fluid-relay/how-tos/provision-fluid-azure-portal).

> [!IMPORTANT]
> Es ist wichtig, die Anmeldeinformationen auszublenden, in `AzureClientProps` die Sie übergeben, damit sie versehentlich zur Quellcodeverwaltung verpflichtet werden. Das Teams-Projekt enthält eine `.env` Datei, in der Sie Ihre Anmeldeinformationen als Umgebungsvariablen speichern können und die Datei selbst bereits in der `.gitignore`Datei enthalten ist. Informationen zum Verwenden der Umgebungsvariablen in Teams finden [Sie unter Festlegen und Abrufen von Umgebungsvariablen](#set-and-get-environment-variable).

> [!WARNING]
> `InsecureTokenProvider` ist eine bequeme Möglichkeit, die Anwendung lokal zu testen. Es liegt in Ihrer Verantwortung, jede Benutzerauthentifizierung zu behandeln und ein [sicheres Token](/azure/azure-fluid-relay/how-tos/connect-fluid-azure-service) für jede Produktionsumgebung zu verwenden.

### <a name="set-and-get-environment-variable"></a>Festlegen und Abrufen einer Umgebungsvariablen

Um eine Umgebungsvariable festzulegen und in Teams abzurufen, können Sie die integrierte `.env` Datei nutzen. Der folgende Code wird verwendet, um die Umgebungsvariable festzulegen in `.env`:

```
# .env

TENANT_KEY=foobar
```

Um den Inhalt der `.env` Datei an unsere clientseitige App zu übergeben, müssen Sie sie `webpack.config.js` so konfigurieren, dass `webpack` sie zur Laufzeit darauf zugreifen können. Verwenden Sie den folgenden Code, um die Umgebungsvariable hinzuzufügen:`.env`

```js
// webpack,config.js

webpack.EnvironmentPlugin({
    PUBLIC_HOSTNAME: undefined,
    TAB_APP_ID: null,
    TAB_APP_URI: null,
    REACT_APP_TENANT_KEY: JSON.stringify(process.env.TENANT_KEY) // Add environment variable here
}),
```

Sie können auf die Umgebungsvariable in `Util.ts`

```ts
// Util.ts

tokenProvider: new InsecureTokenProvider(JSON.parse(process.env.REACT_APP_TENANT_KEY!), { id: "user" }),
```

> [!TIP]
> Wenn Sie Änderungen am Code vornehmen, wird das Projekt automatisch neu erstellt, und der Anwendungsserver wird neu geladen. Wenn Sie jedoch Änderungen am Containerschema vornehmen, werden diese nur wirksam, wenn Sie den Anwendungsserver schließen und neu starten. Wechseln Sie dazu zur Eingabeaufforderung, und drücken Sie zweimal STRG-C. Führen Sie dann oder `gulp serve` `gulp ngrok-serve` erneut aus.

## <a name="see-also"></a>Siehe auch

- [Azure Fluid Relay-Dokumentation](/azure/azure-fluid-relay)

- [Dokumentation zu Fluid Framework](https://fluidframework.com/docs/)
- [Flüssige Beispiele GitHub Repository](https://github.com/microsoft/FluidExamples)
