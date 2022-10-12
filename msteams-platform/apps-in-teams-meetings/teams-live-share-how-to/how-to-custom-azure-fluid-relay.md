---
title: Verwenden des benutzerdefinierten Azure Fluid Relay-Diensts
author: surbhigupta
description: In diesem Modul erfahren Sie, wie Sie einen benutzerdefinierten Azure Fluid Relay-Dienst mit Live Share verwenden.
ms.topic: overview
ms.localizationpriority: high
ms.author: v-ypalikila
ms.date: 07/21/2022
ms.openlocfilehash: b8bec005450515fbef7dfb60e58fac1325235b62
ms.sourcegitcommit: 0fa0bc081da05b2a241fd8054488d9fd0104e17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2022
ms.locfileid: "68552518"
---
---

# <a name="custom-azure-fluid-relay-service"></a>Benutzerdefinierter Azure Fluid Relay-Dienst

Obwohl Sie wahrscheinlich lieber unseren kostenlosen gehosteten Dienst verwenden, gibt es Situationen, in denen es von Vorteil ist, Ihren eigenen Azure Fluid Relay-Dienst für Ihre Live Share-App zu verwenden.

## <a name="pre-requisites"></a>Voraussetzungen

1. Erstellen Sie eine Besprechungsseite und eine App-Besprechungserweiterung, wie im [Lernprogramm zum Würfelroller](../teams-live-share-tutorial.md) gezeigt.
2. Aktualisieren Sie Ihr App-Manifest so, dass alle [erforderlichen Berechtigungen](../teams-live-share-capabilities.md#register-rsc-permissions) enthalten sind.
3. Stellen Sie einen Azure Fluid Relay-Dienst bereit, wie in diesem [Lernprogramm](/azure/azure-fluid-relay/how-tos/provision-fluid-azure-portal) beschrieben.

## <a name="connect-to-azure-fluid-relay-service"></a>Herstellen einer Verbindung mit dem Azure Fluid Relay-Dienst

Beim Aufrufen der Initialisierung `LiveShareClient`können Sie Eigenes `AzureConnectionConfig`definieren. Live Share ordnet Containern zu, die Sie mit Besprechungen erstellen, aber Sie müssen die Schnittstelle zum Signieren von `ITokenProvider` Token für Ihre Container implementieren. In diesem Beispiel wird die Azure-Funktion `AzureFunctionTokenProvider`erläutert, die eine Azure-Cloudfunktion verwendet, um ein Zugriffstoken von einem Server anzufordern.

# <a name="javascript"></a>[JavaScript](#tab/javascript)

```javascript
import { LiveShareClient, LivePresence } from "@microsoft/live-share";
import { SharedMap } from "fluid-framework";
import { AzureFunctionTokenProvider } from "@fluidframework/azure-client";

// Define a custom connection for your app
const options = {
  connection: {
    tenantId: "MY_TENANT_ID",
    tokenProvider: new AzureFunctionTokenProvider(
      "MY_SERVICE_ENDPOINT_URL" + "/api/GetAzureToken",
      { userId: "userId", userName: "Test User" }
    ),
    endpoint: "MY_SERVICE_ENDPOINT_URL",
    type: "remote",
  },
};
// Join the Fluid container
const liveShare = new LiveShareClient(options);
const schema = {
  initialObjects: {
    presence: LivePresence,
    ticTacToePositions: SharedMap,
  },
};
const { container } = await liveShare.joinContainer(schema);

// ... ready to start app sync logic
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

```TypeScript
import {
  LiveShareClient,
  ILiveShareClientOptions,
  LivePresence,
} from "@microsoft/live-share";
import { SharedMap } from "fluid-framework";
import { AzureFunctionTokenProvider } from "@fluidframework/azure-client";

// Define a custom connection for your app
const options: ILiveShareClientOptions = {
  connection: {
    tenantId: "MY_TENANT_ID",
    tokenProvider: new AzureFunctionTokenProvider(
      "MY_FUNCTION_ENDPOINT_URL" + "/api/GetAzureToken",
      { userId: "userId", userName: "Test User" }
    ),
    endpoint: "MY_SERVICE_ENDPOINT_URL",
    type: "remote",
  },
};
// Join the Fluid container
const liveShare = new LiveShareClient(options);
const schema = {
  initialObjects: {
    presence: LivePresence,
    ticTacToePositions: SharedMap,
  },
};
const { container } = await liveShare.joinContainer(schema);

// ... ready to start app sync logic
```

---

## <a name="why-use-a-custom-azure-fluid-relay-service"></a>Warum einen benutzerdefinierten Azure Fluid Relay-Dienst verwenden?

Erwägen Sie die Verwendung einer benutzerdefinierten AFR-Dienstverbindung, wenn Sie:

* Speicherung von Daten in Fluid-Containern über die Lebensdauer einer Besprechung hinaus erforderlich.
* Übertragen vertraulicher Daten über den Dienst, der eine benutzerdefinierte Sicherheitsrichtlinie erfordert.
* Entwickeln Sie Features über Fluid Framework für Ihre Anwendung außerhalb von Teams.

## <a name="why-use-live-share-with-your-custom-service"></a>Warum verwenden Sie Live Share mit Ihrem benutzerdefinierten Dienst?

Azure Fluid Relay ist für die Arbeit mit jeder webbasierten Anwendung konzipiert, d. h. es funktioniert mit oder ohne Microsoft Teams. Das wirft eine wichtige Frage auf: Wenn ich meinen eigenen Azure Fluid Relay-Dienst baue, benötige ich dann noch Live Share?

Live Share verfügt über Features, die für häufige Besprechungsszenarien von Vorteil sind, die andere Features in Ihrer App erweitern, einschließlich:

* [Containerzuordnung](#container-mapping)
* [Liveobjekte und Rollenüberprüfung](#live-objects-and-role-verification)
* [Mediensynchronisierung](#media-synchronization)

### <a name="container-mapping"></a>Containerzuordnung

Das `LiveShareClient` In `@microsoft/live-share` ist für die Zuordnung eines eindeutigen Besprechungsbezeichners zu Ihren Fluid-Containern verantwortlich, wodurch sichergestellt wird, dass alle Besprechungsteilnehmer demselben Container beitreten. Im Rahmen dieses Prozesses versucht der Client, eine Verbindung mit einer `containerId` Besprechung herzustellen, die der bereits vorhandenen Besprechung zugeordnet ist. Wenn kein Container vorhanden ist, wird er `AzureClient` verwendet, um einen Container zu `AzureConnectionConfig` erstellen und den Container dann an andere Besprechungsteilnehmer weiterzuleitet `containerId` .

Wenn Ihre App bereits über einen Mechanismus zum Erstellen von Fluid-Containern und deren Freigabe für andere Mitglieder verfügt, z. B. durch Einfügen der in die `containerId` Besprechungsphase freigegebenen URL, ist dies für Ihre App möglicherweise nicht erforderlich.

### <a name="live-objects-and-role-verification"></a>Liveobjekte und Rollenüberprüfung

Live Share-Live-Datenstrukturen wie `LivePresence`, `LiveState`und `LiveEvent` sind auf die Zusammenarbeit in Besprechungen zugeschnitten und werden daher in Fluid-Containern, die außerhalb von Microsoft Teams verwendet werden, nicht unterstützt. Features wie die Rollenüberprüfung helfen Ihrer App, die Erwartungen unserer Benutzer zu erfüllen.

> [!NOTE]
> Als zusätzlichen Vorteil bieten Liveobjekte auch schnellere Nachrichtenlatenzen im Vergleich zu herkömmlichen Fluid-Datenstrukturen.

Weitere Informationen finden Sie auf der Seite ["Kernfunktionen"](../teams-live-share-capabilities.md) .

### <a name="media-synchronization"></a>Mediensynchronisierung

Pakete von `@microsoft/live-share-media` werden in Fluid-Containern, die außerhalb von Microsoft Teams verwendet werden, nicht unterstützt.

Weitere Informationen finden Sie auf der Seite " [Medienfunktionen"](../teams-live-share-media-capabilities.md) .

## <a name="see-also"></a>Siehe auch

* [GitHub-Repository](https://github.com/microsoft/live-share-sdk)
* [Live Share SDK-Referenzdokumente](/javascript/api/@microsoft/live-share/)
* [Referenzdokumentation zum Live Share Media SDK](/javascript/api/@microsoft/live-share-media/)
* [Live Share-Funktionen](../teams-live-share-capabilities.md)
* [Live Share-Medienfunktionen](../teams-live-share-media-capabilities.md)
* [Live Share – FAQ](../teams-live-share-faq.md)
* [Teams-Apps in Besprechungen](../teams-apps-in-meetings.md)
